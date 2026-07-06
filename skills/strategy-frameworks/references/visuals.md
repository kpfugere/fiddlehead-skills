# Visual Rendering Guide for Strategy Frameworks

When applying strategy frameworks, **always consider whether a visual would make the analysis clearer.** Many of these frameworks were designed to be seen, not just read. A well-placed diagram can communicate in seconds what paragraphs of text cannot.

## When to Create Visuals

**Always visualize** when applying: BCG Matrix, SWOT, Business Model Canvas, Strategy Canvas (Blue Ocean), or the Three Horizons curve — these frameworks lose impact without their canonical layout.

**Visualize when helpful** for: Porter's Five Forces (force strength diagram), Core Competencies (Venn or heatmap), JTBD (job map flow), Golden Circle (concentric rings).

**Skip visuals** when the analysis is brief, conversational, or when the user is clearly looking for a quick answer rather than a deliverable.

## Output Format

Create visuals as **React (.jsx) artifacts** — they render inline, are interactive, and look polished. Use Tailwind utility classes for styling. For simpler diagrams, HTML is also fine.

If producing a **document deliverable** (Word/PDF), describe the visual layout clearly in text and include a simplified table or ASCII representation.

---

## Framework Visual Templates

### SWOT Matrix (2×2 Grid)

The classic four-quadrant layout. Internal factors on top, external on bottom. Helpful/positive on left, harmful/negative on right.

```
┌─────────────────────┬─────────────────────┐
│     STRENGTHS       │     WEAKNESSES      │
│     (Internal +)    │     (Internal −)     │
│                     │                     │
│  • Item 1           │  • Item 1           │
│  • Item 2           │  • Item 2           │
│  • Item 3           │  • Item 3           │
├─────────────────────┼─────────────────────┤
│   OPPORTUNITIES     │      THREATS        │
│     (External +)    │     (External −)     │
│                     │                     │
│  • Item 1           │  • Item 1           │
│  • Item 2           │  • Item 2           │
│  • Item 3           │  • Item 3           │
└─────────────────────┴─────────────────────┘
```

**Design notes:**
- Use color coding: green tint for Strengths, amber/yellow for Weaknesses, blue for Opportunities, red for Threats
- Bold or highlight the 1-2 highest-priority items per quadrant
- Optionally add a header row labeling "Helpful / Harmful" and a side label for "Internal / External"

### BCG Growth-Share Matrix (2×2 with Bubbles)

Axes: Market Growth Rate (vertical, high→low top→bottom) × Relative Market Share (horizontal, high→low left→right).

```
         High Share ◄────────────► Low Share
    ┌─────────────────┬─────────────────┐
H   │                 │                 │
i   │     ★ STARS     │  ? QUESTION     │
g   │                 │    MARKS        │
h   │   (Invest)      │  (Decide)       │
    ├─────────────────┼─────────────────┤
G   │                 │                 │
r   │  🐄 CASH COWS   │  🐕 DOGS        │
o   │                 │                 │
w   │   (Harvest)     │  (Divest)       │
t   │                 │                 │
h   └─────────────────┴─────────────────┘
```

**Design notes:**
- Plot each product/unit as a **circle (bubble)** positioned by its growth rate and relative share
- Size the bubble by revenue contribution — bigger circles = bigger business
- Color-code by quadrant (e.g., gold for Stars, green for Cash Cows, orange for Question Marks, gray for Dogs)
- Add labels inside or next to each bubble with the product/unit name
- Include axis labels and a midpoint line or threshold marker

**Interactive enhancement:** On hover/click, show details for each bubble (revenue, growth %, share ratio, strategic recommendation).

### Business Model Canvas (9-Block Grid)

The canonical layout with the specific block arrangement matters — don't rearrange it.

```
┌──────────┬──────────┬──────────────┬──────────┬──────────┐
│          │          │              │          │          │
│   KEY    │   KEY    │    VALUE     │ CUSTOMER │ CUSTOMER │
│ PARTNERS │ACTIVITIES│ PROPOSITIONS │RELATIONS │ SEGMENTS │
│          │          │              │          │          │
│          ├──────────┤              ├──────────┤          │
│          │          │              │          │          │
│          │   KEY    │              │ CHANNELS │          │
│          │RESOURCES │              │          │          │
│          │          │              │          │          │
├──────────┴──────────┴──────┬───────┴──────────┴──────────┤
│                            │                             │
│       COST STRUCTURE       │       REVENUE STREAMS       │
│                            │                             │
└────────────────────────────┴─────────────────────────────┘
```

**Design notes:**
- Value Propositions sits in the CENTER, bridging left (operations) and right (market)
- Left side = infrastructure/cost. Right side = customer/revenue. This spatial meaning matters.
- Use sticky-note-style cards inside each block (colored backgrounds, short text)
- Color-code left side vs. right side (e.g., blue-tinted left, green-tinted right, gold center)
- Keep text concise — short phrases, not paragraphs. The canvas should be scannable.

### Strategy Canvas (Blue Ocean Line Chart)

A line chart comparing value curves across competitors and your proposed strategy.

```
Offering
Level
  High │         ╱╲
       │   ╱╲  ╱  ╲        ╱
       │  ╱  ╲╱    ╲      ╱
       │ ╱          ╲    ╱    ── Industry Average
       │╱            ╲  ╱     ── Your Blue Ocean Move
  Low  │              ╲╱
       └──┬──┬──┬──┬──┬──┬──┬──
         F1  F2  F3  F4  F5  F6  F7
              Competitive Factors
```

**Design notes:**
- X-axis: Key competitive factors in the industry (6-12 factors)
- Y-axis: Offering level (Low to High)
- Draw one line per competitor/strategic group + one line for the new strategy
- Use **dashed lines** for competitors, **bold/colored line** for the proposed blue ocean move
- The blue ocean curve should look **dramatically different** from competitors — that's the whole point
- Label the factors clearly on the x-axis
- Highlight the ERRC actions: mark factors being Eliminated (×), Reduced (↓), Raised (↑), Created (★)

**Use Recharts** `<LineChart>` with multiple `<Line>` series for a clean implementation.

### Porter's Five Forces (Radial/Pentagon Diagram)

Show the five forces as a radial diagram with strength indicators.

```
                 Threat of
                New Entrants
                    ▲
                   ╱│╲
                  ╱ │ ╲
    Supplier     ╱  │  ╲    Buyer
    Power ◄─────┤ RIVALRY ├─────► Power
                 ╲  │  ╱
                  ╲ │ ╱
                   ╲│╱
                    ▼
                 Threat of
                Substitutes
```

**Design notes:**
- Center: Competitive Rivalry (the core force)
- Four surrounding forces arranged around it
- For each force, show a **strength indicator** (Low / Medium / High) with color coding (green = low threat/power, red = high)
- Can be rendered as a radar/spider chart using Recharts `<RadarChart>` — each axis is a force, the filled area shows overall competitive pressure
- Alternative: Simple card layout with 5 cards, each showing the force name, strength rating (as a colored bar or badge), and 2-3 key drivers

### Three Horizons (Timeline Curve)

The classic S-curve diagram showing three overlapping growth curves across time.

```
Value/
Revenue
    │           H3 ......╱
    │              ...╱
    │    H2 ──────╱
    │      ╱─────
    │  H1╱
    │  ╱──────────────── (declining)
    │╱
    └────────────────────────────────►
     Now    2-3yr    5yr     10yr+
                    Time
```

**Design notes:**
- Three overlapping S-curves, each starting later and peaking later
- H1: Tallest curve, already peaked or peaking, begins declining
- H2: Mid-height, currently in growth phase
- H3: Smallest, just beginning to emerge
- Color each horizon distinctly (e.g., blue H1, green H2, purple H3)
- Label each curve with the actual initiatives/products mapped to that horizon
- Add a vertical "today" line showing current position
- Show the 70/20/10 resource allocation as a small sidebar or legend

**Use Recharts** `<AreaChart>` with three stacked or overlapping `<Area>` series.

### Golden Circle (Concentric Rings)

Three concentric circles with Why at center.

```
    ┌─────────────────────────┐
    │         WHAT            │
    │   ┌─────────────────┐   │
    │   │      HOW        │   │
    │   │   ┌─────────┐   │   │
    │   │   │   WHY   │   │   │
    │   │   │         │   │   │
    │   │   └─────────┘   │   │
    │   └─────────────────┘   │
    └─────────────────────────┘
```

**Design notes:**
- Three concentric circles — Why (innermost, smallest), How (middle), What (outermost)
- Fill the center with the purpose statement, middle ring with values/methods, outer ring with products
- Use warm/bold color for the center (gold, orange) fading to cooler colors outward
- Add an arrow from center outward labeled "Communicate from the inside out"
- Keep text inside each ring brief — one sentence max per ring

### Core Competencies (Venn Diagram)

Three overlapping circles for the three tests.

```
        Broad Market        Customer
          Access              Value
           ╱  ╲            ╱  ╲
          ╱    ╲          ╱    ╲
         ╱   ┌──╲────────╱──┐  ╲
        ╱    │   ╲  CORE ╱   │   ╲
       │     │    ╲─────╱    │    │
       │     │     ╲   ╱     │    │
        ╲    │      ╲ ╱      │   ╱
         ╲   └───────╳───────┘  ╱
          ╲         ╱ ╲        ╱
           ╲       ╱   ╲      ╱
            ╲     ╱     ╲    ╱
              Hard to
              Imitate
```

**Design notes:**
- Center overlap (all three circles) = true core competencies. Highlight prominently.
- List candidate capabilities in the appropriate regions
- Color the center intersection distinctly (gold/bold) vs. partial overlaps (lighter)
- Can use SVG circles for clean rendering

### JTBD Job Map (Horizontal Flow)

A linear flow of the 8 job steps with annotations.

```
Define → Locate → Prepare → Confirm → Execute → Monitor → Modify → Conclude
  │        │        │         │         │         │         │         │
  ▼        ▼        ▼         ▼         ▼         ▼         ▼         ▼
[pain]   [pain]   [ok]     [pain]    [ok]      [pain]    [pain]    [ok]
```

**Design notes:**
- Horizontal flow of 8 steps as connected boxes or a timeline
- Below each step: annotate with satisfaction level (underserved → adequately served → overserved)
- Color-code steps by opportunity level (red = underserved/high opportunity, green = well-served)
- Optionally add the customer's outcome statements below each step
- Can use a simple flexbox layout with cards and connecting arrows

---

## Multi-Framework Dashboards

When combining 2-4 frameworks in a single analysis, consider creating a **unified dashboard** that shows all visuals together on one page. This is especially powerful for deliverables.

**Layout suggestion for 4-framework analysis:**
```
┌─────────────────┬─────────────────┐
│   SWOT Matrix   │  Porter's Five  │
│   (2×2 grid)    │  Forces (radar) │
├─────────────────┼─────────────────┤
│   BCG Matrix    │ Three Horizons  │
│  (bubble chart) │  (area chart)   │
└─────────────────┴─────────────────┘
        Key Takeaways & Recommendations
```

Use a 2×2 grid of chart components in React, with a shared color scheme and a synthesis section below. This gives executives a single-page strategic overview.

## Implementation Notes

- **Recharts** is available for all chart types (line, area, radar, bar, scatter/bubble)
- **Tailwind CSS** handles layout, spacing, and color
- **lucide-react** has useful icons (Star, TrendingUp, AlertTriangle, Target, etc.)
- For the BMC grid and SWOT matrix, use CSS Grid or Tailwind grid utilities rather than a charting library
- Keep labels short and scannable — the visual should communicate structure; the surrounding text provides detail
- Always include a legend when using color coding or multiple series
- Use consistent colors across related visuals in the same analysis (e.g., if "your company" is blue in one chart, keep it blue in all charts)
