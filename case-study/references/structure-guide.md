# Case Study Structure Guide

## Narrative frameworks

Choose one based on the story shape of the project, not the designer's job title:

**Outcome-first (BLUF)**: lead with result and hero visual, then unpack process below. Best when the outcome is the most interesting part, or when brevity matters.

**Minto Pyramid**: answer first, then supporting evidence, then detail. Best for projects where the key insight or decision is the anchor.

**Freytag's dramatic arc**: setup, rising tension (constraints + exploration), climax (key decision or discovery), resolution (outcome). Best when the journey is the most interesting part.

**Magazine feature**: image-first, captions beside images, minimal text blocks. Best when the work is primarily visual and speaks for itself.

**Craft essay**: short, specific, demo-first. No formal sections, just thinking made visible. Best for design engineers and interaction designers. The Rauno Freiberg / Emil Kowalski / Paco Coursey tradition.

**The important thing**: the framework should serve the story, not the other way around. If the most interesting part of a project is a research discovery, don't bury it in section 7 because the template says "Research" comes after "Context." Lead with what matters.

## Emphasis shifts by designer type

Each designer type has a natural center of gravity. These are starting points, not rules.

### UX Designer

**Center of gravity**: the thinking process, research insights, problem reframing

**What makes a UX case study strong**: showing that you understood the problem deeply enough to question it. The key insight that changed the direction matters more than documenting every sticky note.

**Questions specific to UX**:
- What research method did you use and why that one?
- What was the single insight that most changed the direction?
- How did you validate before shipping?
- What did the data show after launch?
- What did you believe about the users that turned out to be wrong?

**Visual assets that earn their place**:
- Research synthesis (redraw for portfolio, don't paste raw sticky notes)
- User flow diagram with annotated decision points
- Exploration grid (3+ directions side by side)
- Before/after with pain points annotated on the before
- Key screens with callouts explaining decisions

**Typical ratio**: 60 to 80% text, 20 to 40% media

### Product Designer

**Center of gravity**: tradeoffs, business + user impact, decisions made under constraints

**What makes a product design case study strong**: showing the negotiation between what's ideal, what's feasible, and what's valuable. The tradeoff section is what separates product design from UX design in a portfolio.

**Questions specific to product design**:
- What tradeoffs did you negotiate with PM or engineering?
- What was the business case for this work?
- How did you scope? What did you cut?
- What would the PM or engineer on this project say about working with you?
- What was the hardest "no" you had to give or receive?

**Visual assets that earn their place**:
- Shipped product screenshots (multiple states)
- Before/after comparison (annotated)
- Decision framework or prioritization artifact
- Metrics chart with before/after

**Typical ratio**: 40 to 60% text, 40 to 60% media

### Visual / Brand Designer

**Center of gravity**: craft, system thinking, context sensitivity

**What makes a visual case study strong**: showing that the work is a system, not a set of pretty screens. Each case study should have its own visual treatment that reflects the brand context. Using one template for all projects signals the opposite of what a visual designer should show.

**Questions specific to visual design**:
- What was the brand's existing context and culture?
- What were the creative constraints?
- How does this system scale across touchpoints?
- What explorations did you kill? Why?
- What is this brand's personality and how did you arrive at it?

**Visual assets that earn their place**:
- Full-bleed hero image
- Typography studies and color explorations
- Grid construction
- Sketch pages (authenticity)
- System in use across multiple contexts (web, mobile, print, environmental)
- Detail crops showing craft decisions

**Typical ratio**: 80 to 90% visuals, 10 to 20% text

### Interaction / Motion Designer

**Center of gravity**: the interaction itself. Static screenshots cannot convey this work.

**What makes an interaction case study strong**: showing the exploration of different motion directions side by side with reasoning for why each was accepted or rejected. The timing, easing, and state documentation shows that the designer thinks about interaction as a system, not decoration.

**Questions specific to interaction design**:
- Can you record the key interaction? What should I look at?
- What timing curves and easing functions did you use? Be specific.
- What states does this interaction pass through?
- How does it degrade for reduced-motion preferences?
- Is there a live prototype I can link to?
- What was the moment it "felt right" and what changed to get there?

**Visual assets that earn their place**:
- Video loops of the key interaction (<=6s, muted, looping)
- Side-by-side comparison of motion alternatives
- State diagram showing interaction states and transitions
- Timing curve documentation
- Reduced-motion alternative demo
- Before/after of the interaction (video, not static)

**Typical ratio**: 70% video/interactive, 20% text, 10% diagrams

### Design Systems Designer

**Center of gravity**: architecture decisions, adoption reality, governance

**What makes a design systems case study strong**: showing not just the components but the coalition you built, the adoption strategy, and what didn't work. Design systems case studies that only show a pretty component library miss the hard part entirely.

**Questions specific to design systems**:
- What was the adoption strategy? How did you get teams to actually use it?
- How do you govern contributions? What's the process for adding or deprecating?
- What metrics do you track? (Nathan Curtis's four families: adoption/coverage, productivity, quality, satisfaction)
- What pushback did you face? What didn't work?
- How did you handle the political dimension of standardization?

**Visual assets that earn their place**:
- Audit collage showing the problem (before state)
- Architecture diagram (token layers, component hierarchy)
- Component spec sheet (properties, variants, states, a11y)
- Adoption dashboard or chart
- Documentation screenshot
- Before/after of a product using the old vs new system

**Typical ratio**: 40% text, 40% component visuals and diagrams, 20% metrics

### UX Researcher

**Center of gravity**: insights that changed decisions, not methods documentation

**What makes a research case study strong**: tracing every shown insight to a design move. Showing that the research actually changed something. The hardest section is impact on product decisions, and it's the most important one.

**Questions specific to UX research**:
- What product decision did this research directly inform?
- What was the finding that surprised the team most?
- What would have happened without this research?
- How did you communicate findings to stakeholders?
- What did you learn about the problem that nobody was asking about?

**Visual assets that earn their place**:
- Curated synthesis artifacts (redraw messy whiteboards, edit affinity clusters to the nodes that drove decisions)
- Key data visualizations
- Journey map or service blueprint (only if it drove a decision)
- Before/after of the product change the research informed

**Typical ratio**: 70 to 80% text, 20 to 30% curated artifacts

### Design Engineer

**Center of gravity**: code + design as one practice, craft details, what actually shipped

**What makes a design engineering case study strong**: showing that design decisions and implementation decisions are the same conversation. The interesting 8 lines of code, not the whole file. The interaction detail that took hours and nobody will notice. The performance number that proves the work is fast, not just pretty.

**Questions specific to design engineering**: (covered in SKILL.md Step 2b)

**Visual assets that earn their place**:
- Hero screenshot or video of the shipped feature
- Before/after comparison (same viewport)
- Micro-interaction video loops (<=6s, muted)
- Architecture diagram (original SVG, theme-aware)
- Analytics chart showing before/after deploy
- Code snippets with "why this matters" context above each

**Typical ratio**: 50% prose, 30% visuals/video, 20% code

## Before/after best practices

Before/after comparisons work when:
- The change is functional and visually clear
- You annotate pain points on the before and solutions on the after
- Both shots use the same viewport, mode, and crop

Before/after comparisons hurt when:
- The change is subjective (viewers may prefer the old version)
- The "before" wasn't yours (reads as dunking on someone else's work)
- Used without annotation (just two screenshots side by side says nothing)

**Placement**: middle of the narrative, never as the hero. Context first, comparison after.

## Projects that didn't ship

If the project was deprioritized, cancelled, or never launched:

1. Say so plainly. "This project was deprioritized after the acquisition."
2. Refocus on decisions, problem framing, the messy middle, and tradeoffs (these are still valid and often more interesting than shipped work)
3. Use usability test results as proxy outcomes
4. Label clearly as "Concept" or "Exploration"
5. Never invent metrics

Unshipped work can make some of the strongest case studies because the designer has more freedom to talk about process, thinking, and what they would have done differently.

## Visual guidelines

- Use CleanShot X with padding for still screenshots
- Use Screen Studio for interaction recordings (auto-zoom, smooth motion)
- Dark and light variants of all UI shots
- Device frames used sparingly (real browser chrome reads more honestly)
- Videos: muted, autoplay, loop, playsInline, <=6s for micro-interactions
- Every visual needs a caption explaining what to look at
- Crop tight to the interesting part. Full-page screenshots waste attention.
