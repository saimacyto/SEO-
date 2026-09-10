# Recognizing YouTube Studio Screenshots

Identify what each screenshot is before pulling numbers. Each YouTube Studio view shows different metrics in different places. Match the screenshot to one of these, then extract the listed fields.

---

## Retention curve ("Key moments for audience retention")
**Recognize it by:** a line chart that starts high-left and falls to the right, a "This video" (blue) vs "Typical retention" (gray) legend, a video preview pane, and big numbers for Average view duration and Average percentage viewed. Often has an "Intro" tag and an AI callout like "X% of viewers are still watching at 0:30."

**Pull:**
- Average view duration (AVD) - e.g. 4:45
- Average percentage viewed (APV) - e.g. 22.6%
- Video length - read it off the player timestamp (e.g. 00:00 / 21:03)
- 30s retention callout if present
- The curve shape: how steep the initial drop, where blue sits vs the gray typical band, any mid-video cliffs or swells, how the tail ends

This is the richest screenshot for diagnosis. Always do the retention autopsy when you have it.

---

## Views by content
**Recognize it by:** "Views by Content" header, a date-range control ("Last 28 days"), a line chart of views over time, and a table row per video with columns for Views, Watch time (hours), Subscribers, Estimated revenue, Impressions, and Impressions click-through rate.

**Pull:**
- Video title (in the table row and the controls)
- Views, Watch time (hours), Subscribers gained, Estimated revenue, Impressions, CTR
- Date range / window
- Trajectory of the views line: rising, peaked-then-declining, flat, or sleeper. Note the peak value and date if a tooltip shows it.

This is the richest screenshot for the scorecard. Compute RPM from revenue and views, and sub conversion from subs and views.

---

## Traffic sources
**Recognize it by:** "Traffic source types" or a breakdown listing Browse features, Suggested videos, YouTube search, External, Shorts feed, Channel pages, Direct/unknown, etc., each with a % and often a watch-time bar.

**Pull:** the % share of each source. Then read it:
- **Browse-heavy:** YouTube is recommending it on the home feed. Evergreen-friendly, scales.
- **Suggested-heavy:** riding next to other videos. Make content adjacent to whatever's feeding it.
- **Search-heavy:** evergreen, keyword-driven. The title's keywords matter most; this builds slowly and lasts.
- **External-heavy:** traffic from off-platform (a post, a newsletter, a Short). Won't sustain unless browse/suggested take over.
- **Shorts feed:** a Short is driving it. Different game - hook in the first second.

---

## Demographics
**Recognize it by:** age/gender bar charts (e.g. "25-34, male 30%") and a geography list (US, India, UK, etc. with %).

**Pull:** age/gender split and top geographies. Use this to explain RPM (US/UK-heavy = higher RPM; India/SEA-heavy = lower) and to sanity-check who the content is actually reaching vs who it's for.

---

## Channel overview / dashboard
**Recognize it by:** big top-line cards for Views, Watch time (hours), and Subscribers over a window, often with a "Top videos" list and a "Realtime" panel.

**Pull:** the window totals and the top videos. This is a channel-level read, not a single-video audit. Note which videos are carrying the channel and whether subs are growing.

---

## Top videos / content table
**Recognize it by:** a sortable table of multiple videos with per-video Views, watch time, etc.

**Pull:** the per-video rows. Useful for spotting which format or topic outperforms. Compare the winners' shared traits (length, topic, packaging style) and name the pattern.

---

## Real-time
**Recognize it by:** "Realtime" header, a 48-hour or 60-minute view count, and a list of recent videos with live counts.

**Pull:** the 48h count and which video is driving it. Limited for a full audit - flag that you need the retention or views-by-content screen for the real diagnosis.

---

## If the screenshot doesn't match any of these
Read whatever labeled numbers you can see, state plainly what view it appears to be, extract what's there, and tell the user which screen would complete the picture. Never invent the missing data.
