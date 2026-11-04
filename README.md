# Astera Studio — Responsive Mockup

A clickable, touch-friendly mockup of **Astera Studio**, a chat-first analytics tool where business users ask questions in plain language, get a chart with a short summary, and pin it to a dashboard. Each chart is fed by a data pipeline, which users can check on and lightly edit from iPhone, iPad or desktop.

Built for the Software Developer Intern take-home assessment by **Batool Kazmi** (FAST-NUCES Karachi).

## How to run

1. Unzip the folder.
2. Double-click `index.html`. No build step, no server, no backend.

Keep all files in the same folder. `index.html` loads `style.css` and `chart.umd.min.js` locally, so the charts work offline. Only the Plus Jakarta Sans font comes from Google Fonts, and it falls back to the system font if you're offline.

## What's inside

```
index.html          markup, sample data and all JavaScript
style.css           design tokens, layout and responsive rules
chart.umd.min.js    Chart.js 4.x, bundled locally
README.md           this file
note.txt            one-page design note
```

## The screens

**Chat**
- Greeting card with an original cat mascot and suggested questions (plus a "Try:" shortcut row).
- Asking a question shows a typing animation, then an answer card with a chart and a short summary.
- Answer actions: **Pin to dashboard**, **View pipeline** (jumps to the pipeline behind the chart) and **Change chart** (bar/line toggle).

**Dashboard**
- Four KPI cards, three charts, a data-freshness label and a pipeline status pill.
- If the pipeline has failed, a banner with a **Re-run** button appears. Re-running goes Failed → Running → Succeeded, then shows a **Scheduled** pill with the next run time.
- Filters for date range and region (a popover on desktop, a bottom sheet on phone).
- Charts pinned from Chat appear under "Pinned from Chat".

**Pipelines**
- Pipeline selector, status header, last run time and a Re-run button.
- Desktop and iPad: a node canvas with curved connectors, row counts and a side panel to inspect and edit the selected step.
- iPhone: a vertical stepper. Tapping a step opens a bottom sheet to rename it, change the filter condition or join key, enable or disable it, or re-run from that step. Swipe down or tap outside to close.
- Both layouts use the same data and the same edit functions.

## How each screen size adapts

| Size | Navigation | Dashboard | Pipeline detail |
|---|---|---|---|
| iPhone (under 768px) | Bottom tab bar with safe-area padding | KPIs and charts stack into one column | Vertical stepper and bottom sheet |
| iPad (768–1199px) | Slim icon sidebar | Two-column grid | Node canvas and side panel |
| Desktop (1200px and up) | Icon sidebar and top bar with search and date | KPIs in four columns, charts in three | Node canvas and side panel |

## Touch and accessibility

- Interactive controls are at least 44px tall.
- Nothing depends on hover. Tooltips are hidden on touch devices.
- Status is shown with an icon, label and color, never color alone.
- Respects iPhone safe areas (`viewport-fit=cover` and `env(safe-area-inset-bottom)`).

## Sample data

All data is made up. The theme is the author's own world: YouTube cover performance (click-through rate) and Fiverr orders by region.

There are two pipelines:
- **YouTube Cover Performance Sync** (Succeeded)
- **Fiverr Regional Order Sync** (Failed at the "Join with Database" step because of a renamed join key; re-running fixes it)

Each follows Read Excel → Filter Rows → Join with Database → Transform.

## Things to try

1. In Chat, tap a suggested question, pin the chart, then open Dashboard to see it pinned.
2. On the Dashboard, tap **Re-run** and watch the status, KPIs and freshness update. Then open Pipelines to see the same status there.
3. In Pipelines on a phone-width window, tap a step to edit it in the bottom sheet.
4. Resize the browser to 375, 768 and 1440px to see each layout.

## Notes and limitations

- It's a mockup. Edits and re-runs update in-page sample data only and reset on reload.
- Tested in Chrome device mode at 375, 768 and 1440px.

## Tech

HTML, CSS and vanilla JavaScript, with Chart.js for charts.