# Community Wisdom — Compress Images to WebP for PageSpeed

Source: community discussion, Rank Expand Academy (Lukas Eisenmann, with a tool recommendation
from Brandon M / Jesse Cunningham).

## The problem

A member ran a site through [PageSpeed Insights](https://pagespeed.web.dev) and found the
homepage was ~12 MB. General guidance: keep a page under 3 MB, preferably under 2 MB. Most of
the weight was JPGs and PNGs.

## The fix

Convert images to WebP. One member used [Squoosh.app](https://squoosh.app) one image at a
time; homepage dropped from 12 MB to 1.86 MB. Mobile PageSpeed score went from the low 60s to
the mid 80s.

**Better tool for bulk conversion:** XnConvert (free, Mac/PC) — does the same WebP conversion
but in bulk with a naming convention, stays fully local (nothing uploaded to a third-party
site, no risk of something being added to the image without your knowledge), and is fast (one
member converted 14 images / 33.88 MiB down to 4.11 MiB — an 87% reduction — in 3 seconds).

## Applying this to a Builder-generated microsite

Checked our own first site (`septicdrippingsprings.com`) against this: total images were
already only ~1.6 MB across 5 photos (nowhere near the 12 MB example), but converted all of
them to WebP anyway since it's free performance with no real downside:

- All 5 images (hero + 4 content photos) converted from JPG to WebP at quality 82.
- Result: ~1.6 MB → ~1.3 MB (19% smaller) — a smaller win than the 12 MB example because the
  Builder's default images were already reasonably compressed, but still worth doing.
- Updated every `<img src="assets/images/*.jpg">` reference across all 32 HTML pages to point
  to the new `.webp` files, then removed the old JPGs.
- No fallback `<picture>`/JPG needed — WebP has near-universal browser support as of 2026.

**Takeaway:** always check actual image weight before assuming it's fine — a 12 MB homepage is
an obvious problem, but even a "fine-looking" ~1.6 MB page can still shave off another ~20% for
free. Do this pass right after downloading the finished site from the Builder, before the first
upload to hosting, so it's not a re-upload/re-deploy done later.
