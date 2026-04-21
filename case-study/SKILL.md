---
name: case-study
description: Help designers and design engineers write portfolio case studies as markdown files. Use this skill whenever someone wants to write a case study, portfolio piece, project write-up, or craft essay about something they designed or built. Triggers on "case study," "portfolio piece," "write up what I built," "document this feature," "craft post," or any request to turn shipped (or unshipped) design work into a presentable markdown page. Also triggers when someone mentions a git branch, PR, or diff in the context of writing about their work, or wants to pull analytics data to quantify impact. Works for all designer types — UX, product, visual, interaction, design systems, research, and design engineering. This is a portfolio coach that asks the right questions, not a template filler.
compatibility: Requires git for design engineer mode. Optionally uses analytics MCP servers (Amplitude, PostHog, Mixpanel) for metrics discovery.
metadata:
  author: jakubsalmik
  version: "1.1.0"
  url: https://jakubsalmik.com/case-study-skill
---

# Case Study Skill

Help designers present their work and their way of working. Outputs a single `.md` file with screenshot placeholders and capture instructions.

A good case study is not a job application. It is a window into how someone thinks, makes decisions, and relates to craft. When a case study does that well, hiring takes care of itself.

This skill has **two modes**, detected automatically from the user's prompt:

- **Designer mode**: the user describes a project, uploads Figma screens, or talks about work they did. The agent coaches them through the right questions and structures the narrative.
- **Design engineer mode**: the user provides a git branch, diff, or PR. The agent reads the code changes, asks context questions, discovers metrics via analytics MCP if available, and writes the case study grounded in what actually shipped.

The agent always asks questions first. It never fills sections with assumptions.

## Philosophy

Core principles:

- **Be a coach, not a template.** Ask questions, challenge weak answers, suggest what's missing. Don't fill in blanks with generic text.
- **Show the thinking, not just the result.** The work itself is half the case study. The other half is how the designer got there, what they believed, what they struggled with, and what they learned.
- **Find the interesting part and build around it.** Not every project has the same story shape. Some are about a hard design decision. Some are about craft. Some are about navigating ambiguity. Structure the case study around what makes this project worth reading about.
- **Specific beats vague.** "Checkout abandonment dropped from 67% to 41%" beats "significantly improved conversion." "`translateY(-2px)` on hover with 120ms ease-out" beats "improved micro-interactions."
- **Honest beats impressive.** Show rejected directions. Admit trade-offs. Say "this didn't ship" if it didn't. Skip sections that would be filler.
- **Short.** Target 800 to 1,500 words. 5 to 8 minute read.

For additional context on what hiring managers specifically look for, read `references/hiring-rubric.md`. Useful calibration, not the primary lens.

## Step 1: Detect mode and designer type

Read the user's prompt and determine:

**Mode**: did they provide or mention a git branch, diff, PR, or codebase? If yes, this is design engineer mode. If no, designer mode.

**Designer type**: what kind of designer are they? This changes which questions to ask and how to structure the output. Read `references/structure-guide.md` for type-specific guidance. The types are:

- **UX designer**: process-heavy, research-driven, user-centered framing
- **Product designer**: outcome-first, tradeoffs with PM/Eng, business + user impact
- **Visual / brand designer**: image-first, minimal text, system-in-context shots
- **Interaction / motion designer**: video-first, timing and state documentation
- **Design systems designer**: architecture decisions, adoption metrics, governance
- **UX researcher**: insight-led, impact on product decisions
- **Design engineer**: code + design, craft details, performance metrics

If the type is unclear from the prompt, ask. One question, not a quiz.

## Step 2: Ask the right questions

Do NOT dump all questions at once. Ask 2 to 3 at a time, conversationally. Adapt based on answers. Skip questions the user has already answered in the conversation.

### Understanding the work

1. **What did you make?** One sentence. What is it?
2. **What was the problem?** What was broken, missing, slow, confusing? Ground it in something observable.
3. **Who was this for?** End users, internal team, specific persona, another audience?
4. **What was your role?** What did you personally own vs. contribute to vs. support? Who else was on the team? Use calibrated verbs: led, co-led, contributed to, supported.
5. **What were the constraints?** Timeline, tech stack, team size, scope, a11y requirements, politics. Every project has constraints.

### Understanding the thinking

6. **What made this problem interesting or hard from a design perspective?** Not just "what was the problem" but why it wasn't obvious, why standard solutions didn't fit, what made it a design challenge rather than just an execution task.
7. **What do you believe about this problem space that shaped your approach?** Their point of view, their design principles for this context. The difference between a designer who executes and one who has opinions.
8. **What did you try that didn't work?** Rejected approaches, killed prototypes, ideas that looked good in Figma but fell apart in testing or code. Push for specifics if the answer is vague.
9. **What was the messy part?** Pivots mid-project, moments of being stuck, debates with the team, unexpected findings that changed direction. Not a clean "we explored A, B, C and chose B" narrative. The real shape of the project.
10. **What decision felt risky at the time?** The moment they had to make a call without certainty and commit to it.

### Understanding the craft

11. **What are you proudest of?** The craft detail, the clever solve, the research insight, the interaction that feels right.
12. **What's the detail that took disproportionate effort and most people won't notice?** The invisible work that separates good from great. This tells you more about a designer than any hero shot.
13. **Show me the thing you think is actually good and tell me why.** Not "what's the most impressive thing" but "what do you genuinely think is good work." This reveals taste.

### Understanding the outcome and growth

14. **What was the outcome?** Metrics if available, qualitative feedback if not. Be specific or skip it. "Users liked it" is not an outcome. (If metrics are central to the story, read `references/metrics-guide.md`.)
15. **What would you do differently?** Honest trade-offs, shortcuts, known debt.
16. **How did this project change how you think about design?** Not a section to check off. What they carry forward. How this project made them a different designer.

### Additional questions by type

Read `references/structure-guide.md` for type-specific follow-up questions.

### NDA-constrained work

If the user mentions they can't show visuals or specifics:
- Focus on thinking, decisions, and the messy middle rather than deliverables
- Describe the problem type and constraints generically
- Share qualitative outcomes without naming the product
- Get written permission for a subset of screens if possible
- Label clearly as "Confidential project" with honest framing

Never encourage them to show more than they're comfortable with.

## Step 2b: Design engineer mode (git + metrics)

If the user is in design engineer mode, also run these steps:

### Read the diff

```bash
git diff main...feature-branch --stat
git diff main...feature-branch -- '*.tsx' '*.ts' '*.css' '*.scss' '*.mdx' '*.md'
git log main...feature-branch --oneline --no-merges
```

Focus on frontend-relevant files. Skip lockfiles, configs, generated code. If the diff is huge (>500 lines), summarize by file and read the interesting hunks.

### Discover metrics (when they strengthen the story)

Not every project is a metrics story. Before running the discovery, ask: "Is this project better told through numbers or through the work itself?"

**Metrics strengthen the story**: performance work, conversion optimization, adoption of a new feature, simplification that reduced errors.

**Metrics are noise**: craft-focused work (a beautiful interaction doesn't need a conversion funnel), early-stage exploration, design system foundations before adoption data exists, work where the value is in the thinking.

If metrics are relevant, read `references/metrics-guide.md` for the full discovery process.

### Additional design engineer questions

- What's the most interesting technical problem you solved?
- Any performance improvements you can quantify? (Bundle size, LCP, FCP, TTI)
- What interaction details are you proud of? (Specific easing curves, spring parameters, transition timing)

## Step 3: Find the story shape

This is the most important step. Before writing, identify what makes this project worth reading about.

Ask the user: **"What's the most interesting part of this project?"**

Their answer determines the structure. Different projects have different story shapes:

- **A hard design decision**: structure around the decision, the alternatives, the reasoning. The decision is the climax.
- **A craft achievement**: lead with the result, then unpack how you got there. Let the work carry the argument.
- **A research discovery**: structure around the insight. What did you find that nobody expected? How did it change the direction?
- **A messy process with a good outcome**: show the pivots, the being-stuck moments, and how you navigated through.
- **A collaboration challenge**: how you aligned, negotiated, and got the work out the door.
- **A systemic change**: the before/after at the system level. What was the world before your work, and what is it now?

Read `references/structure-guide.md` for narrative frameworks (BLUF, Minto Pyramid, Freytag's arc, magazine feature, craft essay) and match the framework to the story shape.

**Do not default to the same section order for every project.** If every case study in a portfolio reads the same way, it signals the designer is executing a template rather than thinking about what makes each project distinct.

## Step 4: Challenge and fill gaps

Before writing, review what you have. Challenge weak spots:

- **"I improved the user experience"** -> Push for specifics. What exactly improved? How do you know?
- **"The team decided to..."** -> What was your role in that decision? What did you push for?
- **No rejected approaches or messy middle** -> "Everything went according to plan?" The struggle is often the most interesting part.
- **Vague outcomes** -> Better to say "too early to measure" or "project was deprioritized" than to invent metrics.
- **No point of view** -> "What do you believe about this that others might disagree with?" Even a small opinion makes the work feel authored rather than executed.
- **No craft detail** -> "What's the thing you spent time on that nobody will notice?" If they can't answer, maybe this project isn't a craft story, and that's fine.

## Step 5: Write the case study

Generate a single `.md` file. Structure follows the story shape from Step 3, not a fixed template.

### Frontmatter

```yaml
---
title: "Clear, specific title"
description: "One sentence. What you built and why it matters."
date: YYYY-MM-DD
tags: ["relevant", "tags"]
role: "Your role title"
team: ["team composition"]
duration: "timeframe"
---
```

### Building blocks

These are available for the case study. Use what the story needs. Order them to serve the narrative. Every block is optional except the title and intro.

**Title + intro**: outcome-forward or question-forward. 2 to 4 sentence hook. What you made, in what context, and why it's worth reading about.

**Hero visual** (screenshot placeholder): the finished work in its best state, or the key moment of the interaction.

**The problem**: what was broken or missing. 2 to 4 sentences grounded in evidence. Can be merged into the intro.

**Before state** (screenshot placeholder): the old UI or previous state, if the comparison is clear and fair.

**Your role + team**: one paragraph or metadata block. Who did what. Calibrated verbs.

**Point of view**: what the designer believed about this problem space that shaped their approach. 2 to 4 sentences. Optional but when present, elevates the entire case study.

**The work**: the core. 3 to 6 paragraphs. Adapt heading to designer type. Mix decisions with their reasoning.

**The messy middle**: pivots, debates, moments of being stuck, unexpected findings. Makes a case study feel real rather than performed. Can be woven into "the work" or standalone.

**Craft details**: the invisible effort. Micro-interactions, edge cases, the detail that took disproportionate time. For design engineers: code snippets (5 to 15 lines, interesting bits only).

**Key visuals** (screenshot placeholders): interactions, components, states, flows. Every visual needs a caption.

**What you explored and killed**: 2 to 3 rejected approaches with reasons.

**Trade-offs**: what you'd do differently with more time or knowledge. Honest.

**Impact**: metrics (before/after format), qualitative feedback, or honest "too early to measure." Only when metrics strengthen the story. For craft-focused projects, the work itself is the proof.

**What this changed**: how the project changed the designer's thinking. What they carry forward.

**Credits**: name collaborators and what they did.

### Screenshot placeholder format

```markdown
<!-- SCREENSHOT: {label}
     Capture: {exactly what to photograph}
     Specs: {dimensions, mode, crop guidance}
     Tip: {tool suggestion, optional} -->
```

For video/animation:

```markdown
<!-- VIDEO: {label}
     Capture: {the interaction to record}
     Specs: <=6s, muted, loop, .mp4 or .webm
     Tip: Screen Studio for smooth motion -->
```

For analytics charts (when relevant):

```markdown
<!-- CHART: {label}
     Capture: {metric and date range}
     Specs: export PNG from analytics tool, annotate deploy date
     Tip: Amplitude "Share chart" > "Download PNG" -->
```

### Writing rules

1. First person, past tense. "I chose X because Y."
2. No filler adjectives. Cut "robust," "seamless," "intuitive," "elegant."
3. Name tools and tech specifically. "Framer Motion `layoutId`" not "smooth animations."
4. Code is seasoning (design engineer mode). 5 to 15 lines max per snippet.
5. Every visual earns its place. No decorative screenshots.
6. Skip empty blocks. Never write "Impact: TBD."
7. Each case study should feel editorially distinct from every other case study in the same portfolio.

## Step 6: Review and deliver

1. Read the draft back to the user
2. Flag sections that feel thin or performed
3. Ask: "Does this sound like you? Does it capture what was actually interesting about this project?"
4. Confirm metrics are accurate (design engineer mode)
5. Save the file as `case-study-{slug}.md` in the user's working directory or preferred output location

## Reference files

- `references/structure-guide.md` -- Section ordering and emphasis by designer type, narrative frameworks, visual asset guidance, NDA strategies.
- `references/hiring-rubric.md` -- What hiring managers evaluate, red flags, what separates strong from weak portfolios. Useful calibration.
- `references/metrics-guide.md` -- How to discover, pull, and present impact metrics. Analytics MCP connection instructions. Use when metrics strengthen the story.

## What this skill does NOT do

- Generate changelogs or release notes
- Create slide decks or presentations
- Build the portfolio site itself
- Invent metrics or outcomes
- Fill sections with assumptions instead of asking
- Write in third person or corporate voice
- Apply the same structure to every project
