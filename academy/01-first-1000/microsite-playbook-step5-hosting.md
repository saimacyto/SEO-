# Microsite Playbook — Step 5: Put the Site Live

Your site is a folder of files. This lesson puts that folder on the internet at your domain.

Before picking a route: your site is static — just files, no database, nothing running in the
background. That's what makes the free route possible, and it's why the hosting packages you
may have been pricing don't apply to what you're building.

## Route A. Cloudflare Pages (Free) — start here

1. Log in to Cloudflare, go to Workers and Pages, then Create application.
2. Drag the zip the Builder gave you straight onto the page. No GitHub account, no coding tool,
   no FTP.
3. Add your domain to the project as a custom domain. HTTPS turns itself on.

That's the whole thing. Every future site is a new project in the same account at no extra
cost.

**Cost: $0.** Your only bill is the $10.44 domain from
[Step 2](./microsite-playbook-step2-domain.md).

## Route B. Shared hosting, if you're already paying for it

Use this if you have Hostinger or similar, or want WordPress and email at the same domain
later.

1. Unzip your site folder. You should see `index.html`, an `assets` folder, and your other
   `.html` files at the same level.
2. Open your host's File Manager (sometimes called "Files") from your hosting dashboard.
3. Open your public folder — usually `public_html`, `www`, or `htdocs`. Anything in here shows
   up on your domain.
4. Upload the **contents** of your unzipped folder, not the folder itself. `index.html` needs
   to sit at the top of `public_html`, not one level deep.
5. Keep the structure intact — the `assets` folder comes along with everything inside it.

**Using FTP instead?** Same idea, different tool: grab FileZilla, connect with the credentials
from your dashboard, navigate to `public_html`, drag your files in.

## Check it worked

Visit your domain. You should see your home page. Click around: a service page, an area page,
your estimate page. Everything should load styled, with links working.

If something is off, it's almost always one of these three:

1. **Page loads but no styling.** The `assets` folder didn't come along, or landed in the wrong
   place.
2. **"Page not found."** Files are one level too deep, or `index.html` isn't at the top.
3. **Domain doesn't load at all.** DNS hasn't caught up. Wait a few hours and check again.

Your site is live on the internet. The next lesson tells Google it exists.

## Tweak your microsite with Claude

There's a video on tweaking the microsite in the "What's Next?" folder (Skool classroom).

---

See also: [Step 3](./microsite-playbook-step3-build.md) (the Builder that produces this zip),
[Step 4](./microsite-playbook-step4-call-tracking.md) (call tracking — remember to re-download
and re-upload after adding the WhatConverts snippet, following this same upload process).
