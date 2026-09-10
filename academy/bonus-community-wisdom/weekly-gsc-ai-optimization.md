# Community Wisdom — Weekly SEO Optimization with GSC + AI

Source: community discussion, Rank Expand Academy (Jan Kenis, with an automation upgrade from
Jesse Cunningham). This is operator-level / Owner-OS-tier content — a workflow for actively
managing sites once they're live, not part of the core numbered playbook.

## The base workflow (Jan Kenis)

Every week, systematically optimize the most important websites by adjusting existing pages or
adding new ones:

1. Export the last 7 days of Google Search Console data.
2. Export the last 7 days *compared to* the previous 7 days — this immediately shows:
   - Which pages are performing better or worse.
   - Which new keywords are appearing.
3. Feed this data to AI (Claude Code or Codex) and ask it to analyze opportunities according to
   your SEO rules. Specifically ask:
   - Are there clear opportunities for new pages?
   - Do existing pages need to be updated or expanded?

**The core SEO rule:** always check the search intent behind the keywords and look at which
pages currently rank in the top 10 on Google for those terms. If a relevant page already
exists, optimize that page further for the keyword instead of creating unnecessary new ones.

Set this up so the analysis and page creation/updates run inside Claude Code / Codex following
your rules consistently — every new or optimized page follows the same standard.

**Practical notes:**
- The website must be added to Google Search Console.
- **Do not connect all your websites to the same GSC account** (per Jesse Cunningham, this is
  a real risk — reason not spelled out in the thread, but the community treats it as
  established caution; worth asking directly before pooling sites under one GSC account).
- GSC can be connected directly to Claude Code/Codex to automate large parts of this workflow.

Run weekly on main sites — consistently surfaces useful opportunities.

## Decision thresholds (from the Q&A)

**When does a query deserve a new page vs. an update vs. no action?**
> Top 10 results in Google for that query, in combination with impressions/clicks for that week.

**Does AI publish automatically, or does a human review first?**
> Automatic publishing is fine — but keep it to a couple of new/optimized pages at a time. If
> there are a lot of candidate new pages, split them up over time rather than publishing them
> all at once.

## The automation upgrade (Jesse Cunningham) — pull GSC into your own database

The problem with reading GSC data by hand every week: manual export/compare doesn't scale
across a portfolio. This is the full stack for pulling GSC data automatically every day into
your own database, so a dashboard/app reads from that instead of hitting Google's API live.

**Core idea:** a small Python script authenticates to the Search Console API once via OAuth,
pulls data daily into Postgres, and any app/dashboard only ever reads that database. GSC is the
source of truth; the database is the product.

### Step 1 — One-time Google Cloud setup (~15 min)

1. Go to console.cloud.google.com → create a project.
2. APIs & Services → Library → enable "Google Search Console API."
3. APIs & Services → OAuth consent screen → configure it, add yourself as a user, and
   **publish the app to "In production."** Leaving it in "Testing" mode makes the login token
   expire every 7 days and breaks automation weekly — publishing (even for a personal-use app)
   makes the token effectively permanent.
4. APIs & Services → Credentials → Create Credentials → OAuth client ID → Desktop app. Download
   the JSON — this is `client_secret.json`.

Key concept: this is "OAuth as yourself" — the script logs in as your own Google account, so it
can read any Search Console property that account already has access to. No service accounts,
no per-site setup — one login covers every site in the GSC account.

### Step 2 — First-time authentication (once, ever)

```python
from google_auth_oauthlib.flow import InstalledAppFlow
from google.auth.transport.requests import Request
from google.oauth2.credentials import Credentials
from googleapiclient.discovery import build
import os

SCOPES = ["https://www.googleapis.com/auth/webmasters.readonly"]  # read-only

def get_service():
    creds = None
    if os.path.exists("token.json"):
        creds = Credentials.from_authorized_user_file("token.json", SCOPES)
    if not creds or not creds.valid:
        if creds and creds.expired and creds.refresh_token:
            creds.refresh(Request())  # silent refresh — the normal path
        else:
            flow = InstalledAppFlow.from_client_secrets_file("client_secret.json", SCOPES)
            creds = flow.run_local_server(port=0)  # browser opens ONCE, first run only
        with open("token.json", "w") as f:
            f.write(creds.to_json())
    return build("searchconsole", "v1", credentials=creds)
```

Dependencies: `pip install google-api-python-client google-auth-oauthlib`. Scope is
`readonly` — the credential can't modify anything in Search Console, only read it.

### Step 3 — Pulling data (with correct pagination)

```python
def query_rows(service, site_url, start_date, end_date, dimensions, row_limit=25000):
    start_row = 0
    while True:
        body = {"startDate": start_date, "endDate": end_date,
                 "dimensions": dimensions, "rowLimit": row_limit, "startRow": start_row}
        rows = service.searchanalytics().query(siteUrl=site_url, body=body).execute().get("rows", [])
        if not rows:
            break
        yield from rows
        start_row += len(rows)
```

`site_url` must be the exact property string from GSC — either `https://www.example.com/`
(URL-prefix) or `sc-domain:example.com` (domain property). List what a token can see with
`service.sites().list().execute()`.

### Step 4 — Store it in your own database, serve the app from that

The pull script upserts rows into Postgres tables (one for exact daily totals, one for
query-level rows, one for page-level rows), keyed so re-running never duplicates
(`ON CONFLICT ... DO UPDATE`). The app never calls Google directly — it reads the database,
which is fast, quota-proof, and lets GSC data be joined against other business data.

### Step 5 — Automate it

A GitHub Actions cron runs the pull script every morning: the auth files and database URL live
in the repo's encrypted Secrets, the workflow writes them to disk at runtime, runs the pull,
done. Runs whether a computer is on or not, and costs nothing at this scale.

### Hard-won gotchas

1. **Data lags ~2-3 days.** Always end date ranges at `today - 3`.
2. **The query dimension is silently capped** (~5,000 rows/day/property) and hides a huge
   anonymized long-tail — summing query rows undercounts real totals by ~50%+. For headline
   numbers, always pull `dimensions=["date"]` (exact totals); use query rows only for
   drill-downs.
3. **Publish the OAuth app to production** or the token dies every 7 days.
4. **Pull a rolling window daily** (~5 days) rather than re-pulling history — data older than a
   few days is final, and rewriting it is wasted database churn.
5. **Treat `client_secret.json` and `token.json` like passwords** — they grant read access to
   every property in the account. Never commit them to a repo; store them as encrypted secrets
   in the scheduler.

That's the entire stack: one OAuth login → a ~60-line Python client → daily cron → your own
Postgres → your app reads Postgres. No paid tools, no third-party connectors required for the
data pipeline itself.

## The full tech stack (for a dashboard/app built on top of this)

**Frontend/app — Next.js on Vercel (~$20/mo Pro)**
- Next.js (App Router, server components) + React, Tailwind CSS + shadcn/ui.
- Vercel: every git push auto-builds and deploys. Pro tier needed only for long function
  runtimes (300s) for AI routes — a simpler app is fine on the free Hobby tier.
- Server-side caching via Vercel's Data Cache: heavy dashboard queries run once per 24h,
  busted the moment fresh data lands from the pipeline.

**Database + auth — Supabase (Pro, $25/mo)**
- Hosted Postgres — all GSC data lives here. The app talks to it with plain `node-postgres`
  (`pg`) over the connection pooler, not Supabase's client libraries or REST API — Data API and
  RLS not enabled.
- Supabase Auth for login/sessions only (`@supabase/ssr`), email+password with signups disabled
  (admin creates accounts — no signup emails, no magic links, no email infrastructure needed).
- Free tier works to start; Pro is for bigger database + backups.

**Data pipeline — Python + GitHub Actions ($0)**
- Plain Python (`google-api-python-client`, `psycopg2`) pulls from the GSC API and upserts into
  Postgres (the Step 1-5 process above).
- GitHub Actions cron runs every morning; credentials live in GitHub's encrypted Secrets. Free
  at this scale, runs with the local computer off.
- The last cron step hits a secret-protected endpoint on the app to bust the cache so the
  dashboard reflects new data instantly.

**AI layer — Anthropic API (usage-based, cents per use)**
- Claude API server-side only (keys never touch the browser): a bigger model (Sonnet) for
  heavy one-shot analysis, a smaller/faster one (Haiku) for chat, with prompt caching so repeat
  calls cost almost nothing.

**Third-party data — DataForSEO (usage-based)**
- SERP API (~$0.002/query) for "who ranks for this keyword," page-scrape API for competitor
  content, and an LLM-responses API to test what ChatGPT/Gemini actually answer
  (~$0.015-0.07/question) — only needed for competitor/AI-visibility features.

**Repo — GitHub (private, free)**
- Single repo: Next.js app at the root, the Python pipeline in an `engine/` folder, the cron
  workflow in `.github/workflows/`.

## When this applies to a first microsite vs. later

This entire automated-pipeline section is portfolio-scale tooling — relevant once managing
several sites and wanting a unified dashboard, not needed for a single first microsite. For one
site, the manual weekly GSC export + feeding it to Claude Code/Codex (the base workflow above)
is the right-sized version of this — see
[Step 5](../01-first-1000/microsite-playbook-step5-hosting.md) for getting a first site live,
and revisit this file once there's a real reason to automate across a portfolio.
