# Site Build Log: septicdrippingsprings.com (Hill Country Septic Co)

Tracks the build and review history for the first microsite, following
[Step 3 of the Microsite Playbook](../../academy/01-first-1000/microsite-playbook-step3-build.md).
Niche/domain decision is logged separately in
[`niche-decisions/2026-09-07-septic-dripping-springs.md`](../niche-decisions/2026-09-07-septic-dripping-springs.md).

## Build 1 (2026-09-07) — One-Click Builder output

Generated via `build.rankexpand.com` (code `PLAYBOOK2026`). 32 HTML pages delivered:
homepage, 6 service pages (Septic System Installation as primary, plus Aerobic Installation,
Repair, Pumping, Real Estate Inspection, Drain Field Repair & Replacement), 10 town/neighborhood
pages (Driftwood, Henly, Fitzhugh, Hays City, Cloptins Crossing, Pioneer Town, Belterra,
Caliterra, Headwaters, Ledgestone, Sawyer Ranch), plus About, Contact, FAQ, Meet the Team,
Careers, Estimate, Thank You, Service Areas, and standard legal pages (Privacy Policy, Terms,
Referral Marketing Disclosure, Disclaimer, Accessibility, Complaints Policy). Business name:
Hill Country Septic Co. Brand color `#0F6E8C`.

### Review findings (the "review and tighten" pass)

**Fixed in this pass** (edited output HTML directly, per the Builder's own instructions — not
the JSON):
- **Fabricated staff bios.** The generator invented three fictional team members (names +
  invented personal details — a paper road atlas, a vegetable garden, a ranch upbringing)
  presented as real staff across `index.html`, `about.html`, and `meet-the-team.html`, and the
  fictional owner name was also used as the complaint-escalation contact in
  `complaints-policy.html`. Confirmed with the user: fully fictional, no real people behind
  them. Rewrote all four files to describe the operation honestly (small local crew, work
  sometimes completed via vetted independent contractors per the site's own Referral Marketing
  Disclosure page) without inventing named individuals. Verified zero remaining references via
  grep across all 32 files.

**Flagged, not yet fixed (waiting on the user's own setup):**
- **Phone number** `(678) 789-6953` is a placeholder (Atlanta, GA area code — wrong region).
  User is replacing it via a WhatConverts local tracking number (Texas area code) per
  [Step 4](../../academy/01-first-1000/microsite-playbook-step4-call-tracking.md), forwarded
  to a Vapi AI receptionist.
- **Email** `frostyahmed@gmail.com` is a placeholder; user is changing this too.
- **Contact/Estimate forms** both submit to `action="#"` — non-functional. Not yet resolved;
  may end up routed through whatever system handles the Vapi/WhatConverts lead flow instead of
  a traditional form backend. Needs a decision once the call-tracking/voice-agent setup is
  live.

**Checked, no issues found:**
- Legal pages (Privacy Policy, Disclaimer, Complaints Policy, Referral Marketing Disclosure) —
  no fabricated license numbers or certifications. The Referral Marketing Disclosure page in
  particular is genuinely well-done: it honestly discloses the referral/lead-sale business
  model with FTC-style transparency, matching the real business model described in the course.
- Hero and content images — high quality, appropriately branded, no obvious AI-artifact issues.
- Town pages — differentiated content per town (not literal duplicates), correct internal
  linking to neighboring service-area pages.

## Build 1, Review Pass 2 (2026-09-07) — sitewide content/markup/performance pass

A second read-through (all 32 pages plus CSS), explicitly excluding phone/email since the user
is handling those via WhatConverts/Vapi. Fixed:

- **Sitewide typo:** "Septic Inspection (real Estate Transactions)" had broken capitalization
  in the nav, headings, and form dropdown on every page (33 files). Fixed to "Real Estate."
- **Malformed HTML sitewide:** every inline CTA button embedded in body copy was wrapped in an
  invalid nested `<p>` tag (`<p>...<p><a>button</a></p></p>`) across 17 pages. Fixed with a
  script-based pass (byte-identical pattern across files, confirmed via grep before and after).
- **Structured data bug:** two FAQ page schema.org answers had the literal CTA text
  "Get a Free Estimate" bleeding into the machine-readable answer — could surface awkwardly in
  a Google rich snippet. Cleaned.
- **Meaningless pricing tables:** all 6 service pages had tables where every cell said
  "Site-specific estimate" / "Depends on..." — no actual numbers, reads as evasive rather than
  careful. Replaced with real ballpark ranges (e.g. aerobic install $15k&ndash;$30k per our own
  Dripping Springs research; tank pumping $300&ndash;$600; drain field replacement
  $5k&ndash;$15k+), all still qualified as "general planning figures, not a quote" consistent
  with the existing Disclaimer page.
- **Two lazy meta descriptions** (`services.html`, `service-areas.html`) that were just a copy
  of the page `<title>` — rewrote both with real, unique descriptions.
- **Brand color never actually applied:** found the literal unfilled template placeholder
  `{{BRAND_COLOR}}` still in the CSS comment — the whole site was running on the Builder's
  default cyan (`#06d4ef`), not a real brand color. Applied `#0F6E8C` (deep teal-blue) across
  the CSS variables and every page's `theme-color` meta tag.
- **Image weight (per [community WebP tip](../../academy/bonus-community-wisdom/image-compression-webp.md)):**
  converted all 5 site images from JPG to WebP (quality 82) — total image weight ~1.6MB → ~1.3MB
  (19% smaller). Updated all `<img src>` references across all 32 pages and removed the old
  JPGs. Site was already well under the 2-3MB PageSpeed guideline before this, but WebP is free
  performance with no downside.

Verified zero remaining instances of every issue above via grep before repackaging and
resending the zip to the user.

## Next steps

1. Complete WhatConverts + Vapi setup (Step 4), get a real Texas-area tracking number.
2. Decide how form submissions route (traditional form backend vs. folded into the
   Vapi/WhatConverts lead flow).
3. Reload the Builder project file, paste in the WhatConverts tracking snippet, regenerate,
   re-download, re-upload (do not skip the regenerate/re-upload step).
4. Re-send lead reports to self while testing; switch to the paying client's email once a real
   local septic company is paying for the leads.
5. Once live, run the site through [PageSpeed Insights](https://pagespeed.web.dev) to confirm
   real-world mobile/desktop scores.
