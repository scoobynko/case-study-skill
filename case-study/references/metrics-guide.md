# Metrics Discovery and Analytics Guide

Design engineer mode only. Read this after understanding the feature from the diff and conversation.

## How to think about metrics

Most designers either skip metrics entirely or grab a vanity number that doesn't prove anything. This guide helps the agent think like a data analyst: map changes to behaviors, pick the right metric type, define the comparison window, and present results honestly.

## Step 1: Map code changes to user behaviors

Read the diff. Ask: what user-facing action does this touch?

Examples:
- New search component: search usage, result clicks, time-to-result, zero-result rate
- Redesigned onboarding: completion rate, drop-off by step, time-to-first-value
- Performance optimization: page load time, interaction latency, bounce rate
- New navigation: navigation depth, pages-per-session, search-after-landing rate
- Simplified form: form completion rate, error rate, time-to-complete, abandonment step

## Step 2: Pick the right metric type

| Change type | Primary metric | Secondary metrics |
|---|---|---|
| Interaction redesign | Funnel conversion or task completion rate | Time-on-task, error rate, rage clicks |
| Performance work | LCP, FCP, TTI, or p50/p95 response time | Bundle size delta, bounce rate |
| Information architecture | Navigation depth or pages-per-session | Bounce rate on affected pages, search-after-landing |
| New feature (didn't exist before) | Adoption rate (DAU who used it / total DAU) | Frequency of use, retention of adopters vs non-adopters |
| Removal or simplification | Error rate or time-to-complete | Support ticket volume, completion rate |
| Design system component | Adoption count (teams/products using it) | Bug reports per component, designer satisfaction |

## Step 3: Define the comparison window

Pick a time range that's fair:
- **Minimum**: 2 weeks before, 2 weeks after
- **Align day-of-week**: compare Monday-to-Monday, not Monday-to-Friday
- **Watch for seasonality**: don't compare Black Friday week to a normal week
- **Flag confounders**: if other changes shipped in the same window, say so

If a gradual rollout or feature flag was used, cohort comparison (users who saw new vs old) is stronger than before/after on the same users.

## Step 4: Present the metrics brief

Before writing the case study, present this to the user for confirmation:

```
METRICS BRIEF
Feature: [name from the diff]
Affected behavior: [what user action this touches]

Recommended metrics (ranked by signal strength):
1. [Primary metric]
   Why: [why this one matters most for this feature]
   Query: [the event/funnel/query to run]
   Before: [date range]
   After: [date range]

2. [Secondary metric]
   Why: [supporting evidence for the story]
   Query: [the event/funnel/query to run]

3. [Guardrail metric]
   Why: [confirming we didn't break something else]
   Query: [the event/funnel/query to run]

Confounders to acknowledge: [other changes in the window]
Skip if: [conditions where this metric would be misleading]
```

## Connecting to analytics tools

Check if an analytics MCP server is connected. If yes, pull data directly. If no, write the query instructions for the user to run manually.

### Amplitude

```
# Official MCP server (OAuth, recommended)
MCP URL: https://mcp.amplitude.com/sse

# Community MCP (API key based)
npx amplitude-mcp --amplitude-api-key=KEY --amplitude-secret-key=SECRET

# Amplitude MCP Marketplace (Claude Code)
# /plugin marketplace add amplitude/mcp-marketplace
# For other agents, configure MCP URL in your agent's settings
```

Key tools available via Amplitude MCP:
- `search`: find dashboards, charts, experiments
- Event segmentation with filters and breakdowns
- Funnel analysis between events
- Retention queries
- Cohort comparison

### PostHog

```
# Official MCP server
MCP URL: https://mcp.posthog.com/sse

# Supports HogQL for custom SQL queries
# Trends, funnels, retention, paths, lifecycle
```

Key tools:
- Custom HogQL queries (SQL-like, full flexibility)
- Trend analysis with breakdowns
- Funnel creation between events
- Retention by cohort
- Session replay links (for qualitative evidence)

### Mixpanel

```
# Official MCP server (remote, OAuth)
# Available via Mixpanel settings
```

Key tools:
- Event queries with property filters
- Funnel analysis
- Retention
- User segmentation

### Multi-platform

```
# engageable: wraps GA4, Mixpanel, PostHog, Amplitude
pip install engageable
engageable-mcp
```

### No analytics MCP available

If no analytics tool is connected:
1. Still run the metrics discovery (Steps 1 to 3)
2. Present the metrics brief with specific query instructions
3. Tell the user exactly where to go in their analytics tool
4. Ask them to paste the numbers back into the conversation
5. Write the Impact section once numbers are confirmed

## Writing metrics into the case study

### Format rules

- **Always show the baseline.** "87% completion rate" means nothing without "up from 64%."
- **Name the metric precisely.** "Funnel conversion from `/onboarding/step-2` to `/onboarding/complete`" not "improved onboarding."
- **One primary, one or two supporting.** Don't dump a wall of numbers.
- **Percentages for rates, absolutes for counts.** "Completion rate: 64% to 87%" but "daily active search users: ~120 to ~340."
- **Acknowledge confounders.** "Other changes shipped in this period, so this isn't a clean A/B, but the timing aligns with deployment."
- **Never invent numbers.** If data isn't available, say "too early to measure" or "no analytics were instrumented for this flow."

### Impact section template

```markdown
## Impact

{Primary metric}: {before} to {after} ({timeframe, e.g., "two weeks post-deploy"}).

{One sentence explaining why this metric matters.}

{Secondary metric}: {before} to {after}. {One sentence of context.}

{Optional guardrail}: {Metric name} held steady at {value}, confirming
{what you didn't break}.

{If no data}: This shipped {timeframe ago}. {Reason no data is available:
no analytics instrumented / too early to measure / project was deprioritized
before launch}. Qualitative signal: {teammate feedback, user quotes, or
support ticket trends if available}.
```

### Analytics chart placeholder

```markdown
<!-- CHART: impact comparison
     Capture: [metric name] chart showing [date range before] through [date range after]
     Specs: export as PNG, crop to relevant date range, annotate deploy date
     Tip: Amplitude "Share chart" > "Download PNG" or PostHog insight export -->
```

## Metrics for non-engineer designers

Even without code access, designers can strengthen their case studies with metrics. Guide them to ask their PM or analyst for:

- Task completion rate from usability testing (before/after redesign)
- Support ticket volume for the affected feature area
- NPS or CSAT scores if tracked per feature
- Time-on-task from user testing sessions
- Adoption rate of a new feature or flow
- Error rate or form abandonment rate

Frame the ask: "You don't need to own the dashboard. You need one number with a baseline and a date."
