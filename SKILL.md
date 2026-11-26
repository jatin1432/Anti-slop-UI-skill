---
name: anti-slop-ui
description: Design, build, refine or review web interfaces so they look made by a skilled designer, not generated. Use for landing pages, product sites, dashboards, app screens, components, redesigns, UI audits, motion and animated effects in React, Vue or plain HTML/CSS. Not for backend-only work.
---

# Anti-slop UI

Generated interfaces look alike because they reach for the same defaults: the same fonts, the same cream or near-black backgrounds, the same rows of icon cards, the same fade-up on every section. This skill replaces those defaults with decisions. Every page it produces should be traceable to its subject, its audience and the one thing a visitor came to do.

Three beliefs drive everything below:

- **A choice beats a default.** Any pattern can be right for a brief. It is wrong when it appears because nobody decided anything.
- **Restraint is where boldness comes from.** Spend the page's energy on one memorable thing and keep the rest calm.
- **Looking is the only proof.** A design is finished when its rendered result has been checked at the sizes people will use, not when the code compiles.

## 1. Size the request first

Read only what the task needs. Decide the route before touching files.

| The request | Route |
| --- | --- |
| A named change to a named element ("make this button green", "more space here", "fix this typo") | Make the change. Look at the result if it changed colour, size or spacing. No plan, no questions, no review. |
| A vague complaint about existing UI ("this feels off", "make it better", "looks AI-made") | Audit first with `references/quality-floor.md` and the AI-tell list, report the top findings, then fix. |
| A new page, screen, flow or component with a visual identity to decide | Full path: stages 2 to 5 below. |
| A redesign of something that exists | Full path. Keep the content and behaviour; treat the current look as a record of what not to repeat. |
| Polishing an existing design without changing its identity | Stages 3 to 5. Keep the brand, the copy and everything outside the scope. |
| Motion only ("animate this", "add transitions") | `references/motion.md`, then the effects file for the stack. |
| A review or audit only | Stage 5 in read-only mode. Report findings with evidence and stop. Do not edit files. |

Refine and redesign are different jobs. Refining keeps the identity and improves it. Redesigning replaces the identity. Never blend the two into a polish of a look that should have been replaced.

## 2. Pick the mode of the surface

The mode is decided by what the visitor is doing on this specific screen, not by what kind of company it is. A developer tool's landing page is still a selling page.

| Mode | The visitor is... | Examples | How ambitious |
| --- | --- | --- | --- |
| **Sell** | deciding whether to act | landing, product, pricing, campaign pages | Full ambition: a clear point of view, one striking hero, art direction |
| **Work** | completing a task | dashboards, admin, settings, editors, tools | Ambition shows as precision: speed, scanability, familiar patterns, quiet brand details |
| **Read** | trying to understand | docs, articles, help, changelogs | Structure for comprehension first, then make reading pleasant |
| **Show** | experiencing the work itself | portfolios, galleries, showcases | The work leads from the first screen; the interface steps back |

The mode sets how much motion, decoration and expressive layout the page earns. Sell and Show may be bold. Work and Read move only to answer an action.

## 3. The hard rules (always, even if nothing else is read)

These never bend, whatever the brief or style. The full list with checks is in `references/quality-floor.md`.

1. Every colour, font, size step, radius and spacing value lives in a named token, defined once. Components use the tokens, not raw values.
2. Never invent proof. No made-up metrics, ratings, testimonials, client logos, awards or "trusted by" counts. Missing proof leaves a marked slot, not a fake.
3. Every interactive element shows a visible keyboard focus state at once.
4. Everything that moves has a reduced-motion version, and the content is readable with scripts off.
5. Text meets contrast: body text at least 4.5:1, large text at least 3:1.
6. No sideways scrolling at any width from 320px to 1920px.
7. Animate only transform and opacity (filter and clip-path when they stay smooth). Never `transition: all`.
8. The hero's headline, one sentence and the main action are visible without scrolling on a laptop screen and on a phone.
9. One real icon set at one stroke weight. Never emoji or unicode symbols as icons.
10. Controls have all their states: hover, focus, pressed, disabled, loading and, where relevant, error and empty.

## 4. The workflow

| Stage | What happens | Read |
| --- | --- | --- |
| 1. Triage | Size the request (section 1), pick the mode (section 2), detect the stack | this file |
| 2. Brief and direction | Gather material, audience, main action and tone in one message at most. Write the six-line plan. Check it against the AI defaults | `references/intake.md`, `references/direction.md` |
| 3. Build | Tokens first. Hero first, then the rest of the page. Real content throughout | `references/craft.md`, then `references/motion.md` and the effects file for the stack when the page moves |
| 4. Verify | Render it. Check every hard rule, count the AI tells, run the ship-safe checks | `references/quality-floor.md`, `references/ship-safe.md` |
| 5. Review and hand over | One review in fresh context for new or redesigned work. A delivery note that says what was decided and what is missing | `references/review.md` |

Load a reference only when its stage starts. Reading everything up front costs context and makes the result more generic, not less.

## 5. Route by stack

Detect the stack from the project files (`package.json`, lockfiles, framework config, `.vue` or `.tsx` files). Never assume one.

- **React or Next.js:** motion and effects from `references/effects-react.md`.
- **Vue or Nuxt:** motion and effects from `references/effects-vue.md`.
- **Plain HTML and CSS, or anything else:** hand-written CSS following `references/motion.md`. No library is required to make a page feel designed.
- **Smooth scrolling** only for Sell and Show pages whose scroll drives animation: `references/smooth-scroll.md`.

Work inside the project's existing system. Reuse its tokens, components and libraries. Never add a second library that does the same job as one already installed.

## 6. Project memory

Two files keep decisions across sessions. Read them first when they exist; offer to create them after a full-path build.

- `PRODUCT.md`: who the product is for, what they come to do, the tone, the facts and proof that may be shown.
- `DESIGN.md`: tokens, type, colour, spacing, motion values, the chosen direction and why, and any per-page overrides in their own section.

An existing `DESIGN.md` is the law for its project. Follow it, even where this skill would choose differently, and point out conflicts instead of silently overriding them.

## 7. Hand over

End every full-path task with a short delivery note (template in `references/review.md`): the direction and why, what was built, what is still a placeholder, which checks ran and which could not, and up to three next steps the person could ask for. Small edits get one or two sentences.

If the result could not be looked at (no browser, no screenshot), say "visual result not checked" plainly. Never claim a check that did not run.
