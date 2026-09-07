# Microsite Playbook — Step 6: Get Indexed (Omega Indexer)

Google does not know your site exists yet. This tells it.

We use Omega Indexer to push our pages to index.

## Step 1. Get your list of URLs

Your site came from the Builder, so you already have them. Open your `sitemap.xml` in a
browser and copy the list.

Working on a site you did not build? Run a free Screaming Frog crawl and export the live URLs
instead.

## Step 2. Create the campaign in Omega

This part is not obvious, so here is the exact path:

Enter Dashboard → Campaigns → + Create Campaign → Copy & Paste Links. You'll see "Links" and a
field below it. Paste your whole list in there and Omega parses it automatically. No file
upload needed.

## Step 3. Set your dripfeed

Omega submits pages over time rather than all at once, which improves the odds of getting
indexed. How long depends on how big the site is:

- Your first microsite: 1 to 3 days.
- A large build, 80 to 100 pages: 7 to 10 days.

---

**Known gap found while applying this to our own first site:** the One-Click Builder
(`build.rankexpand.com`) does NOT actually generate a `sitemap.xml` in its output — checked the
delivered zip directly and confirmed it's not there. Step 1 as written assumes one exists.
Until/unless the Builder adds this, the workaround is either (a) manually compile the URL list
from the site's own page files, or (b) run a free Screaming Frog crawl on the live site (the
"didn't build it yourself" fallback the lesson already describes) to get the URL export instead.

See also: [Step 3](./microsite-playbook-step3-build.md) (the Builder), [Step 5](./microsite-playbook-step5-hosting.md)
(getting the site live — indexing only matters once it's actually online).
