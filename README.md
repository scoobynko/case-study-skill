# Case Study Skill

A portfolio coach for designers and design engineers. Asks the right questions, structures the narrative around what makes the work interesting, and outputs a `.md` file with screenshot placeholders.

## Install

```bash
# Claude Code
gh skill install scoobynko/case-study-skill case-study --agent claude-code

# Cursor
gh skill install scoobynko/case-study-skill case-study --agent cursor

# GitHub Copilot
gh skill install scoobynko/case-study-skill case-study

# Codex
gh skill install scoobynko/case-study-skill case-study --agent codex

# Gemini CLI
gh skill install scoobynko/case-study-skill case-study --agent gemini
```

Or manually (works with any agent that follows the Agent Skills spec):

```bash
git clone https://github.com/scoobynko/case-study-skill.git /tmp/cs
cp -r /tmp/cs/case-study ~/.claude/skills/case-study    # Claude Code
cp -r /tmp/cs/case-study ~/.cursor/skills/case-study     # Cursor
cp -r /tmp/cs/case-study ~/.codex/skills/case-study      # Codex
rm -rf /tmp/cs
```

## What it does

One skill, two modes:

**Designer mode** (UX, product, visual, interaction, design systems, research): you describe a project. The skill coaches you through targeted questions based on your designer type, challenges vague answers, and writes a structured `.md` case study with screenshot instructions.

**Design engineer mode**: you provide a git branch or diff. The skill reads the code, asks context questions, discovers which metrics to pull from Amplitude/PostHog/Mixpanel via MCP, and writes the case study grounded in what shipped.

## How it works

The skill is agent-like. It asks 2 to 3 questions at a time instead of dumping a form. It pushes back on weak answers ("Everything you tried worked the first time?"). It skips sections that would be filler.

It finds the story shape of each project and structures around that, not a fixed template. Some projects are about a hard design decision. Some are about craft. Some are about navigating ambiguity. The case study should reflect what made the work interesting.

## What's inside

```
case-study/
├── SKILL.md                     # The coach (273 lines)
└── references/
    ├── hiring-rubric.md         # How design leaders read portfolios
    ├── structure-guide.md       # Emphasis by designer type, narrative frameworks
    └── metrics-guide.md         # Impact metrics discovery, analytics MCP connections
```

## Usage

```
"Help me write a case study about the onboarding redesign I did"

"Write a case study from my feature branch feat/command-palette"

"I need to document a design system I built but it's under NDA"

"Turn this diff into a portfolio piece and pull metrics from Amplitude"
```

## Credits

Built by [Jakub Salmik](https://jakubsalmik.com).
