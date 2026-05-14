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

## Contributing

Releases are automated by [release-please](https://github.com/googleapis/release-please), which derives the next version from [Conventional Commits](https://www.conventionalcommits.org/). The commit message (or PR title, if you squash-merge) determines the bump:

| Prefix | Example | Effect |
|---|---|---|
| `fix:` | `fix: handle empty diff in design-engineer mode` | patch (1.4.1 → 1.4.2) |
| `feat:` | `feat: add metrics-guide reference` | minor (1.4.1 → 1.5.0) |
| `feat!:` or `BREAKING CHANGE:` in body | `feat!: rename SKILL.md frontmatter` | major (1.4.1 → 2.0.0) |
| `chore:`, `docs:`, `refactor:`, `test:`, `ci:` | `docs: clarify install step` | no release |

Use the imperative mood ("add", not "added"). Keep the subject under ~72 chars; put rationale in the body.

### Enforcement

PR titles are linted by `.github/workflows/lint-pr-title.yml` — non-conforming titles block the merge. For direct pushes to `main`, write a conforming commit message; non-`feat`/`fix` commits are simply ignored by release-please rather than rejected.

## Credits

Built by [Jakub Salmik](https://jakubsalmik.com).
