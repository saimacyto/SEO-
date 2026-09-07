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

## Next steps

1. Complete WhatConverts + Vapi setup (Step 4), get a real Texas-area tracking number.
2. Decide how form submissions route (traditional form backend vs. folded into the
   Vapi/WhatConverts lead flow).
3. Reload the Builder project file, paste in the WhatConverts tracking snippet, regenerate,
   re-download, re-upload (do not skip the regenerate/re-upload step).
4. Re-send lead reports to self while testing; switch to the paying client's email once a real
   local septic company is paying for the leads.
