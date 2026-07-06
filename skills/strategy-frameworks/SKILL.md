---
name: strategy-frameworks
description: |
  Comprehensive strategy analysis skill that applies proven business frameworks (SWOT, Porter's Five Forces, BCG Matrix, Blue Ocean, Business Model Canvas, Jobs-to-be-Done, Golden Circle, Three Horizons, Core Competencies) to evaluate companies, products, markets, and strategic decisions. Automatically selects and synthesizes 2-4 complementary frameworks for a holistic view. Use this skill whenever the user asks about competitive analysis, market strategy, business model evaluation, product positioning, portfolio management, growth planning, innovation strategy, strategic planning, company analysis, or any question that benefits from structured strategic thinking — even if they don't mention a specific framework by name. Triggers on phrases like "analyze this company," "what's our competitive position," "should we enter this market," "help me think through our strategy," "evaluate this business model," "where should we invest," or any request for strategic advice or business analysis.
---

# Strategy Frameworks Skill

You have access to 9 proven strategy frameworks. Your job is to pick the right combination, apply them with rigor, and deliver clear strategic insight — not academic summaries.

## Available Frameworks

| Framework | Best For | Reference File |
|-----------|----------|----------------|
| **SWOT Analysis** | Quick situational assessment; internal vs. external factors | `references/swot.md` |
| **Porter's Five Forces** | Industry attractiveness; competitive dynamics | `references/porters_five_forces.md` |
| **BCG Matrix** | Portfolio management; resource allocation across products/units | `references/bcg_matrix.md` |
| **Blue Ocean Strategy** | Finding uncontested markets; escaping head-to-head competition | `references/blue_ocean.md` |
| **Business Model Canvas** | Mapping how a business creates, delivers, and captures value | `references/business_model_canvas.md` |
| **Jobs-to-be-Done** | Understanding customer motivations; product-market fit | `references/jobs_to_be_done.md` |
| **Golden Circle** | Purpose-driven strategy; brand positioning; internal alignment | `references/golden_circle.md` |
| **Three Horizons** | Balancing short-term performance with long-term innovation | `references/three_horizons.md` |
| **Core Competencies** | Identifying and leveraging unique organizational strengths | `references/core_competencies.md` |

**Visual Rendering Guide**: `references/visuals.md` — Templates, layout specs, and implementation notes for each framework's canonical diagram (matrices, canvases, charts, radars). Read this before creating any visual output.

## How to Use This Skill

### Step 1: Understand the Strategic Question

Before selecting frameworks, clarify what the user actually needs to figure out. Common strategic questions map to different framework combinations:

**"Should we enter this market?"**
→ Porter's Five Forces (industry attractiveness) + SWOT (our readiness) + JTBD (customer need validation)

**"How should we allocate resources across our portfolio?"**
→ BCG Matrix (portfolio positioning) + Three Horizons (time-horizon balance) + Core Competencies (where we have an edge)

**"How do we differentiate / escape commodity competition?"**
→ Blue Ocean (value innovation) + JTBD (unmet customer needs) + Business Model Canvas (how to deliver differently)

**"What's our competitive position?"**
→ Porter's Five Forces (industry structure) + SWOT (internal vs. external) + Core Competencies (sustainable advantages)

**"How do we define / refine our strategy?"**
→ Golden Circle (purpose and positioning) + Business Model Canvas (operational model) + Three Horizons (short vs. long term)

**"How should we think about this product / feature?"**
→ JTBD (what job does it solve?) + Blue Ocean (where's the whitespace?) + Business Model Canvas (how does it fit the model?)

**"Evaluate this company"** (broad analysis)
→ SWOT (situational snapshot) + Porter's Five Forces (industry context) + BCG Matrix or Business Model Canvas (business model / portfolio) + Core Competencies (sustainable edge)

These are starting points, not rigid rules. Adapt based on what the user shares and what will actually be useful.

### Step 2: Select and Load Frameworks

Pick 2-4 frameworks that complement each other for the question at hand. The goal is a multi-lens view, not framework overload. Read the relevant reference files before applying them — each contains the framework's components, how to apply it, and common pitfalls.

**Selection principles:**
- Pair an **external** lens (Porter's, Blue Ocean) with an **internal** one (SWOT, Core Competencies, BMC) for balance
- Pair a **diagnostic** framework (SWOT, Porter's, BCG) with an **action-oriented** one (Blue Ocean, JTBD, Three Horizons) so the analysis leads somewhere
- If the user mentions a specific framework, start there but suggest complementary ones
- If unsure, SWOT + one other framework is always a safe starting combo

### Step 3: Apply Frameworks with Real Substance

For each framework you use:

1. **Ground it in specifics.** Use real data, context from the conversation, and concrete examples. Never produce a generic template with placeholder text. If you lack information, say what you'd need to fill the gap, or make reasonable inferences and flag them as assumptions.

2. **Connect the frameworks.** The synthesis is the valuable part. Show how insights from one framework inform or reinforce another:
   - "Porter's analysis shows supplier power is high — which SWOT confirms as a key weakness..."
   - "The JTBD analysis reveals an underserved emotional job — which maps to a Blue Ocean opportunity..."
   - "Core Competencies in X suggest Horizon 2 bets should focus on adjacent markets where X applies..."

3. **End with actionable takeaways.** Every analysis should conclude with clear strategic implications: what to do, what to stop, what to watch, or what to investigate further. Frameworks are means, not ends.

### Step 4: Choose the Right Output Format

- **Conversational by default**: For focused questions or when the user is exploring, deliver the analysis inline with clear structure but without unnecessary formality.
- **Document when warranted**: If the analysis is substantial (3+ frameworks, deep dive), or the user asks for a deliverable, produce a formatted document (Word doc or PDF using the appropriate skill). Structure it as an executive-ready strategy brief.
- **Visuals — use them liberally**: Most of these frameworks were designed to be *seen*. Read `references/visuals.md` for detailed rendering guidance, templates, and implementation notes for each framework's canonical diagram.

### Step 5: Render Visual Diagrams

**Always create a visual** when applying: BCG Matrix, SWOT, Business Model Canvas, Strategy Canvas (Blue Ocean), or Three Horizons — these frameworks lose significant impact without their canonical layout.

**Create a visual when it helps** for: Porter's Five Forces (radar chart of force strength), Core Competencies (Venn diagram), JTBD (job map flow), Golden Circle (concentric rings).

**Best practices for visuals:**
- Build as **React (.jsx) artifacts** using Recharts for charts, Tailwind for layout, and lucide-react for icons
- For 2+ framework analyses, consider a **unified dashboard** — a 2×2 grid of charts with a synthesis section below gives executives a single-page strategic overview
- Keep labels short and scannable — the visual communicates structure; surrounding text provides detail
- Use consistent colors across related charts in the same analysis
- Populate with **real data from the analysis**, not generic placeholders — a BCG matrix with the user's actual products plotted is 10× more valuable than a template

## Framework Synergy Patterns

These are battle-tested combinations that reinforce each other:

**The Full Company Assessment** (broad strategic review)
SWOT → Porter's Five Forces → Core Competencies → Three Horizons
*Flow: Situational snapshot → Industry context → What makes us special → Where to invest across time*

**The Innovation Play** (finding new growth)
JTBD → Blue Ocean → Business Model Canvas
*Flow: What do customers really need? → Where's the whitespace? → How do we build it?*

**The Portfolio Optimizer** (resource allocation)
BCG Matrix → Core Competencies → Three Horizons
*Flow: Where are we now? → What are we best at? → How do we sequence bets?*

**The Brand & Purpose Reset** (identity and positioning)
Golden Circle → JTBD → Blue Ocean
*Flow: Why do we exist? → What job do we fulfill? → How do we own that space?*

**The Market Entry Assessment** (go/no-go decisions)
Porter's Five Forces → SWOT → JTBD → Business Model Canvas
*Flow: Is the industry attractive? → Are we positioned to win? → Is there real demand? → What's the business model?*

## Important Reminders

- **Frameworks are thinking tools, not checklists.** Apply judgment. Skip sections of a framework that aren't relevant. Go deeper where it matters.
- **Acknowledge limitations.** If you're working with limited information, say so. Offer to refine the analysis if the user can provide more data.
- **Avoid framework jargon soup.** Use the framework terminology where it adds clarity, but translate it into plain strategic language. The user wants insight, not a business school lecture.
- **Challenge assumptions.** Good strategy analysis should surface uncomfortable truths and non-obvious connections, not just organize what's already known.
- **Be opinionated.** After laying out the analysis, give your assessment. "Based on this analysis, the strongest move appears to be X because..." is more valuable than "here are the factors to consider."
