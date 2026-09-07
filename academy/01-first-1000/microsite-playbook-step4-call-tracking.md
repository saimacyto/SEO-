# Microsite Playbook — Step 4: Call Tracking with WhatConverts

This is what turns a phone call into a lead report you can send a client.

WhatConverts answers the question every buyer asks: did that call actually come from your
site? It emails you a report for every call with the number, the duration, a recording, a
transcript, and a button to mark whether the lead was any good. That report is what makes this
look like a real lead generation business rather than a hobby.

## What it costs

This is the first thing in the Playbook with a monthly bill:

- **Master account:** $30/month. Under it you create unlimited profiles, one per microsite —
  so $30 covers your whole portfolio, not per-site.
- **Each local tracking number:** ~$3/month on top.
- **Call recording, transcription, and analysis** are billed per use and show up on your
  invoice — not much per call, but it adds up as lead flow grows.

## Steps

1. Create an account at [whatconverts.com](http://whatconverts.com). Free trial available; it
   does ask for a card up front.
2. Work through onboarding: pick your industry. When asked for a preferred area code, you can
   skip that for now. Choose "install myself," then "manual."
3. Copy your tracking code — the snippet that goes on every site you build.
4. Create a profile for this microsite. Everything lives under the one master account, with a
   separate profile per site. Name it after the business (e.g. "Emergency Locksmith Florida").
5. Add your tracking number: Calls → Phone Numbers → Add a Phone Number. Choose your country,
   choose Local, enter the area code for your target city, Find Numbers, and pick one. Only one
   is needed.
6. Set where it forwards: point it at your own number or a burner to begin with. Once the AI
   receptionist is set up (Step 7 of this module, using Vapi), change this to forward to your
   Vapi number instead.
7. Turn on call recording and transcription in the configuration screen. Call analysis is
   optional. These are the paid extras above, and they're what makes the lead reports worth
   sending.
8. Finish. The number is live.

## Now put the tracking code on your site

Your site was built before you had this code, so it needs to go back through the Builder:

1. Open the Builder and load the project file saved in Step 3 (see
   [Step 3](./microsite-playbook-step3-build.md)).
2. Paste the WhatConverts tracking code into the tracking field.
3. Generate the site again and download it.
4. Re-upload it the same way as before.

This is exactly why Step 3 says to save your project file — reload and re-export, don't start
over.

## Where your reports go

In WhatConverts, set the email address that should receive call reports. Send them to yourself
while testing. Once a business is paying for the leads, send reports straight to them — that's
a large part of what they're paying for.

## When something is off, it's usually one of these

1. **No numbers show up in your area code.** WhatConverts limits which countries you can pull
   numbers from based on your account details. If you only see numbers for the wrong country,
   check your account country before assuming the area code is unavailable.
2. **Calls come through but nothing is recorded.** Recording and transcription were left off in
   the configuration screen.
3. **The call happens but nothing appears in WhatConverts.** The tracking code isn't on the
   live site. Confirm the site was regenerated and re-uploaded after pasting the code in — not
   just saved as a project file.

---

See also: [Step 3](./microsite-playbook-step3-build.md) (the Builder, and why project files
matter), and note that Builder-generated sites already tag phone number links with
`class="wc-phone"` — WhatConverts-ready markup baked in ahead of time, before you've even set
up an account.
