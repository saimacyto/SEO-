# General SEO Fundamentals Guide (8 Modules)

A standalone, generic SEO training reference — not specific to the Rank Expand Academy
microsite playbook, but useful general-purpose background. Read one module at a time; do the
Action Steps immediately; keep a simple log of what changed and what happened (rankings,
clicks, leads).

## Quick glossary (plain English)

- **Keyword** — the words people type into Google.
- **Search intent** — what the searcher is trying to accomplish.
- **Organic traffic** — visits from unpaid search results.
- **Backlink** — a link from another site to yours.
- **Index** — Google's database of pages it can show.

## Module 1: SEO Fundamentals

**What is SEO?** The practice of making a website more visible when people search on Google,
Bing, etc. Think of a website like a store: content is inventory, site structure is the aisles
and signage, reputation is what other people say about you.

**Why it matters:** organic traffic (visitors not paid for via ads) mostly goes to page-1
results; page 5 is basically invisible.

**How search engines work:**
1. **Crawling** — bots follow links to discover pages.
2. **Indexing** — Google stores what it finds in a giant database.
3. **Ranking** — Google orders results based on which page best answers the search.

**Search intent types:**
- Informational — learning ("how to train a puppy")
- Navigational — finding a specific site ("Facebook login")
- Commercial — researching ("best laptops 2024")
- Transactional — ready to act ("buy iPhone 15 Pro")

If page format doesn't match intent, it usually won't rank.

**The three pillars of SEO:**
1. On-Page SEO — content, titles, headings, images, internal links
2. Off-Page SEO — backlinks and reputation outside the site
3. Technical SEO — speed, mobile usability, crawlability, structured data

**E-E-A-T (quality signals)** Google looks for: Experience (first-hand knowledge), Expertise
(skill and accuracy), Authoritativeness (recognized source), Trustworthiness (honest, safe,
reliable). Stricter standards apply to "Your Money or Your Life" topics (health, finance,
safety).

**Action Steps:** Search your brand/topic and note where you appear (baseline). Check indexing
via `site:yourwebsite.com`.

**Self-Check:** "How to fix a leaky faucet" — what intent, what content format best serves it?

## Module 2: On-Page SEO Essentials

**The on-page checklist:** title tag, meta description, headings (H1/H2/H3), URL, images (file
name/compression/alt text), internal links, keyword placement (natural, not forced).

**Title tags:** under ~60 characters, main keyword early, specific and clickable, unique per
page. Example: "Beginner's Guide to Indoor Herb Gardening | GreenThumb Blog"

**Meta descriptions:** don't directly boost rankings but can boost click-through rate. Under
~155 characters, keyword used naturally, says what the page delivers, light CTA.

**Headings:** H1 = the page's main title (use one), H2 = major sections, H3 = subsections —
think of it like a table of contents.

**URL structure:** clear and descriptive. Good: `yoursite.com/indoor-herb-gardening-guide`.
Bad: `yoursite.com/page?id=12847&cat=3`. Short, hyphens, no random numbers.

**Image optimization:** alt text describes what's in the image (and aids accessibility, e.g.
"Woman watering basil plant on kitchen windowsill"); descriptive file names
(`kitchen-herb-garden.jpg` beats `IMG_4521.jpg`); compress for load speed.

**Internal linking:** distributes authority, guides visitors to related pages, shows Google how
topics connect. Use descriptive anchor text; link to important pages from pages that already
get traffic.

**Keyword placement (without stuffing):** title tag, H1, first ~100 words, at least one H2,
URL, meta description (if natural), relevant image alt text. Write for people first, then check
for natural keyword coverage.

**Action Steps:** Audit top 5 pages for unique title tag/meta description/one H1 each. Add alt
text to key images. Add 2-3 internal links to the most important pages.

**Self-Check:** Homepage title is "Welcome to Our Website - Home - Official Site" — what's
wrong, how would you rewrite it?

## Module 3: Technical SEO Foundations

**What it is:** ensures search engines can crawl, index, and render a site — great content
can't rank if Google can't reliably access it.

**Site speed / Core Web Vitals:**
- LCP (Largest Contentful Paint): target under 2.5s
- INP (Interaction to Next Paint): target under 200ms
- CLS (Cumulative Layout Shift): target under 0.1

Common improvements: compress images, cache assets, use a CDN, reduce unnecessary scripts.
Test with [PageSpeed Insights](https://pagespeed.web.dev/).

**Mobile-friendliness:** Google uses mobile-first indexing — fit small screens, readable text,
tappable buttons, no horizontal scrolling.

**HTTPS security:** encrypts traffic and improves trust; most hosts offer free SSL.

**XML sitemaps:** list key pages so Google can discover them; submit in Google Search Console.

**Robots.txt:** tells crawlers what to avoid; located at `yoursite.com/robots.txt`.

**Common crawlability/indexing blockers:** pages blocked by robots.txt, accidental `noindex`,
broken internal links, orphan pages (no internal links pointing to them), duplicate content
confusing Google.

**Structured data (schema markup):** helps search engines understand content, can unlock rich
results (FAQs, ratings, recipes).

**Canonical tags:** tell Google the "main" version of a page when similar pages exist.

**Action Steps:** Run PageSpeed Insights and record Core Web Vitals. Check mobile usability.
Confirm HTTPS. Submit sitemap in Google Search Console.

**Self-Check:** Great content + many backlinks, but doesn't appear in Google at all — what
technical issues could cause this?

## Module 4: Domain Rating and Backlinks

**Domain Rating (DR):** an Ahrefs metric (0-100) approximating backlink-profile strength — a
reputation score based on who links to you. Check via Ahrefs' free website authority checker;
alternatives: Moz (DA), Semrush (Authority Score).

**Backlinks:** a link from another site to yours; a quality one acts like a vote of confidence.
Why they help: authority transfer, better rankings (often), referral traffic, faster discovery
and indexing.

**Types:** Dofollow (passes authority, default), Nofollow (not a direct endorsement), plus
Google-recognized `sponsored` and `ugc` attributes.

**Quality beats quantity** — Google looks at relevance, authority of the linking site, link
placement (body content beats footer), and anchor text (should describe the page).

**Beginner link-building strategies:** linkable assets (guides/tools/original data), guest
posting (relevant sites), broken link building, digital PR, resource page outreach,
relationship building.

⚠️ **Avoid spammy links** — buying links, link farms, PBNs, automated blasts can trigger
penalties and tank visibility.

**Action Steps:** Check your DR vs. 3 competitors. Pick one linkable asset to build/improve.
List 3 relevant outreach targets. Set a monthly goal of 2-3 quality links.

**Self-Check:** 1,000 backlinks for $50, or a guest post on a respected industry blog — which
and why?

## Module 5: Topical Authority and Keyword Research

**Topical authority:** becoming a trusted source on a subject by covering it deeply and
consistently. Google increasingly rewards depth, not just keyword matches.

**Keyword research** tells you what people actually search for. Key metrics: search volume,
keyword difficulty (KD), CPC (commercial value).

**Long-tail vs. short-tail:** short-tail is broad/high competition ("coffee"); long-tail is
specific/lower competition ("best cold brew maker under $50"). Beginners usually win faster
with long-tail queries.

**Finding keywords — free:** Google autocomplete + "People also ask," Google Keyword Planner,
AnswerThePublic, Ubersuggest (limited). **Paid:** Ahrefs, Semrush, Moz.

**Topic clusters:** pillar page (broad, comprehensive overview) + cluster articles (deep dives
on subtopics) + internal links connecting everything. Example (coffee brand): pillar = "The
Complete Guide to Coffee Brewing"; clusters = pour-over, espresso, cold brew, grind size, water
temperature, common mistakes.

**Content gaps:** find what competitors rank for that you don't; create content that's more
helpful and complete.

**Action Steps:** Pick one main topic. Brainstorm 15-20 subtopics from autocomplete. Group into
3-4 clusters. Plan 1 pillar page + 5 supporting articles.

**Self-Check:** Personal finance blog — target "investing" (huge volume/competition) or "how to
start investing with $500" (lower volume/competition)? Explain why.

## Module 6: Local SEO (for businesses that serve an area)

**What it is:** helps you show up for searches like "dentist near me" or "pizza in Chicago."

**Google Business Profile:** helps appear in Maps and local packs. Setup: claim/create at
business.google.com → verify → fill out every field (hours, services, photos, categories) →
keep info current.

**NAP consistency:** Name, Address, Phone — should be identical everywhere online.

**Local citations:** mentions of NAP (with or without a link) on directories/local sites.

**Reviews and reputation:** influence rankings and conversion — ask happy customers, make it
easy, respond professionally, never buy fake reviews.

**Local content ideas:** location service pages, local guides, community events, local case
studies.

**Action Steps:** Complete Google Business Profile. Fix NAP inconsistencies. Build 5-10 quality
citations. Start a simple review request process.

**Self-Check:** Business name varies across Yelp, Google, and the site — what problem does that
create, how do you fix it?

## Module 7: Measuring SEO Success

**Why measurement matters:** without it, SEO is guessing.

**Essential free tools:** Google Search Console (queries, impressions, clicks, indexing, Core
Web Vitals), Google Analytics 4 (traffic, engagement, conversions).

**Metrics to track:**
- Search visibility: impressions, clicks, CTR, average position
- Traffic and engagement: organic sessions, top landing pages, engagement time
- Conversions: leads/signups/purchases, conversion rate, revenue value

**Realistic expectations — SEO compounds:**
- Months 1-3: foundations + content, little movement
- Months 3-6: early wins on long-tail
- Months 6-12: meaningful growth

**Action Steps:** Set up Search Console. Install GA4. Track monthly: organic traffic, top
queries, top pages, conversions. Review monthly and adjust.

**Self-Check:** Traffic up 20% over 3 months but conversions flat — what might that indicate,
what would you investigate?

## Module 8: Building an SEO Strategy for Growth

**Order of operations:**
1. Fix technical foundations.
2. Improve existing pages.
3. Build topic clusters for authority.
4. Earn quality backlinks.
5. Do local SEO (if relevant).
6. Measure, learn, repeat.

**The growth flywheel:** great content earns links → links build authority → authority helps
content rank faster → rankings drive visibility → visibility attracts more links.

**Common mistakes to avoid:** ignoring intent; chasing huge keywords too early; neglecting
technical SEO; expecting instant results; buying links; forgetting the reader; not measuring;
being inconsistent.

**SEO and AI/LLMs:** as AI answers become more common, sites with strong topical authority and
helpful content are more likely to be referenced.

**Key takeaways:** consistency wins; do the basics extremely well; build authority over time.

---

## Relationship to the Rank Expand Academy playbook

This is a general-purpose reference, not part of the sequential [Microsite Playbook](../01-first-1000/microsite-playbook.md)
(domain → build → call tracking → hosting → indexing). It fills in the "why" behind moves the
playbook already tells you to make mechanically:

- Module 2 (on-page) explains why the Builder generates unique titles/meta descriptions/H1s per
  page — that's the on-page checklist in action.
- Module 3 (technical SEO) is the theory behind the PageSpeed/Core Web Vitals work already done
  on `septicdrippingsprings.com` (see [site build log](../../my-progress/site-builds/septicdrippingsprings-com.md)).
- Module 6 (local SEO) applies directly to every microsite — NAP consistency and Google
  Business Profile setup are worth doing for each site in the portfolio, and aren't yet covered
  by the playbook's numbered steps.
- Module 5 (topic clusters) is the conceptual version of what the Builder's town/neighborhood
  pages + service pages already implement structurally for a microsite.
