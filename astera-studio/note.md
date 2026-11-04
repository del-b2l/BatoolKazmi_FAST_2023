# ASTERA STUDIO: DESIGN NOTE

**Batool Kazmi | FAST-NUCES Karachi**

---

## 1. DESIGN APPROACH

The goal was for each device to get its own layout, not a shrunken desktop.

- **Navigation:** Icon sidebar on desktop, compact icon rail on iPad, bottom tab bar with safe-area padding on iPhone.
- **Dashboard:** KPIs form a 2×2 grid on phone and charts stack in one column. Status uses icon + colour + label, a "Last updated" label shows freshness, and a failed pipeline shows an inline banner with Re-run.
- **Pipeline detail (main focus):** Desktop/iPad get a node canvas with connectors, row counts and an edit panel. iPhone gets a vertical stepper of tappable cards with a bottom sheet to rename a step, change a filter or join key, toggle it, or re-run from it. Both layouts share the same data and edit functions.

  **Why:** Pan, zoom and drag-and-drop fight page scrolling on touch screens, and light editing doesn't need free-form node placement.
- **Personal touch:** Sample data from my own world (YouTube cover CTR, Fiverr orders by region) and an original SVG cat mascot, inspired by Pinterest and Behance references.

## 2. TRIED AND DROPPED

A horizontal swipe row for KPIs on mobile. At 375px, "Failed Runs", the most urgent number, was the fourth card and hidden off-screen, with no hint that more cards existed. I replaced it with a 2×2 grid so all four metrics are visible without a gesture. A common mobile pattern isn't automatically the right one.

## 3. AI TOOLS AND MANUAL WORK

**Tools:** Claude (planning, prompts, debugging); Antigravity (initial code).

**Key prompts:**
- "Build a single-file HTML/CSS/JS analytics tool with Chat, Dashboard and Pipeline views."
- "Use mock YouTube and Fiverr data, with a soft pastel style."
- "Show pipelines as a node canvas on desktop and a vertical stepper on phone."
- "Make everything touch-friendly, with 44px tap targets and no hover-only actions."

**Fixed by hand:**
- Bundled Chart.js locally after charts failed to render.
- Repaired UTF-8 encoding on corrupted symbols.
- Wired up dashboard filters and Re-run, synced across tabs.
- Added mark-all-as-read and refined icons.
- Fixed breakpoint logic: the canvas was cramped on tablet portrait, so below 768px uses the stepper and wider screens use the canvas.

I used AI as a starting point, then tested, found usability gaps, and made the final design decisions myself.