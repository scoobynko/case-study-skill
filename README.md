# Case Study Skill

A portfolio coach for designers and design engineers. Asks the right questions, finds the story shape of your project, and outputs a `.md` file with screenshot placeholders.

## Install

```bash
gh skill install scoobynko/case-study-skill case-study
```

## Two modes

**Designer**: describe a project, get coached through questions tailored to your type (UX, product, visual, interaction, design systems, research). The skill challenges vague answers and structures the narrative around what makes the work interesting.

**Design engineer**: provide a git branch or diff. The skill reads the code, asks context questions, discovers metrics from Amplitude/PostHog/Mixpanel via MCP, and writes the case study grounded in what shipped.

## What's inside

```
case-study/
├── SKILL.md                     # The coach
└── references/
    ├── hiring-rubric.md         # How design leaders read portfolios
    ├── structure-guide.md       # Emphasis by designer type, narrative frameworks
    └── metrics-guide.md         # Impact metrics discovery, analytics MCP
```

## Credits

Built by [Jakub Salmik](https://jakubsalmik.com).
