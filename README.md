# Anti-slop UI

An agent skill that makes AI-built interfaces look designed, not generated.

Ask an AI to build a website and you can usually tell: cream backgrounds, tiny all-caps labels over every heading, three icon cards in a row, a pulsing green dot, the same fade-up on every section, statistics nobody measured. Anti-slop UI replaces those defaults with decisions drawn from the subject, the audience and the one thing a visitor came to do, and then checks the rendered result before calling it done.

It works with Claude Code and other agents that support skills, on React, Next.js, Vue, Nuxt and plain HTML/CSS.

## What it does

- **Sizes every request first.** A one-line fix is just fixed. A new page goes through the full path. A review stays read-only.
- **Sets ambition by mode.** Selling pages may be bold; dashboards and tools get precision instead of spectacle.
- **Plans before it builds.** A six-line plan, tested against the generic AI looks and a "would a similar prompt get this exact design?" check.
- **Gives the hero real options.** Eight hero layouts and six techniques (monumental type, image layered over text, one light source, strict grids with generous space, gathered controls, one living moment), chosen by the material available. Light or dark comes from the brand and use scene, never by default.
- **Holds a hard floor.** Fourteen rules that never bend, including no invented proof, visible focus, reduced motion, contrast and no sideways scrolling.
- **Counts AI tells.** 36 named tells in five groups; two or more and the page gets reworked.
- **Handles motion properly.** Motion decided by purpose and frequency of use, with rules for focus, keyboard, touch and reduced motion.
- **Knows the effect libraries.** Routes to Animate UI and Magic UI for React, Animate UI and Inspira UI for Vue, and Lenis for smooth scroll, with an effect budget so the flourishes don't take over.
- **Ships safe.** Quick browser-side security checks for raw HTML, cross-window messages, tokens in storage and third-party scripts.
- **Reviews with fresh eyes.** One independent review for new work, and a clear delivery note that says what is real, what is a placeholder and what was not checked.

## Install

With the [skills CLI](https://skills.sh):

```bash
npx skills add jatin1432/Anti-slop-UI-skill
```

Or clone it straight into your agent's skills directory. For Claude Code, for all projects:

```bash
git clone https://github.com/jatin1432/Anti-slop-UI-skill ~/.claude/skills/anti-slop-ui
```

For a single project, clone it into `.claude/skills/anti-slop-ui` inside that project instead.

## Use

Just ask for interface work; the skill activates on its own. For example:

- "Build a landing page for our trail-running shoe."
- "Redesign this dashboard, it looks AI-made."
- "Review the checkout flow for UX and accessibility."
- "Animate the dialog and tabs in this shadcn project."
- "Add a scroll-driven story section to the homepage."

## Files

```
Anti-slop-UI-skill/
├── SKILL.md                    Triage, modes, hard rules, workflow, stack routing
└── references/
    ├── intake.md               What to know before designing, and when not to ask
    ├── direction.md            The six-line plan, hero layouts and techniques
    ├── craft.md                Layout, type, colour, imagery, copy, responsive
    ├── motion.md               When and how things move, on any stack
    ├── effects-react.md        Animate UI and Magic UI routes, the effect budget
    ├── effects-vue.md          Animate UI for Vue and Inspira UI routes
    ├── smooth-scroll.md        Lenis: when to use it and how to set it up
    ├── quality-floor.md        Hard rules, the AI-tell list, craft checks
    ├── ship-safe.md            Browser-side security checks
    └── review.md               Self-check, fresh-eyes review, delivery note
```

The skill loads only the reference files a task needs, stage by stage.

## Contributing

Spotted a new AI tell, or a hero pattern that works? Open an issue or a pull request with an example of the problem and the fix. Keep additions in plain language and specific: a rule should say what to look for and what to do instead.

## License

MIT. See [LICENSE](LICENSE).
