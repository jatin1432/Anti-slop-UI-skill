# Intake: what to know before designing

Read this at stage 2 of a full-path task. The goal is to learn the four things that change the design, in one message at most, and never to stall on questions the project already answers.

## Look before asking

Check these first, in this order. Each one can answer a question so it never has to be asked.

1. `DESIGN.md` or `PRODUCT.md` in the project. If present, they decide tone, tokens and audience.
2. The prompt itself. A specific prompt often answers everything.
3. The project's existing look: stylesheet variables, Tailwind config, font links, component library, brand assets in `public/` or `assets/`.
4. The real product, if it can be reached: a running dev server, a URL, screenshots in the repo. Pictures of the real thing beat anything drawn.

## The four questions

Ask only the ones still open, together, in one short message.

1. **Material.** What do we have to put on the page? Product captures or a screen recording, photos, real numbers (customers, prices, uptime), a quote with the name of the person who said it, logos the client may use. Say plainly that nothing will be invented: missing material becomes a clearly marked placeholder.
2. **Audience.** Which people is this for, and what is on their mind when they land here?
3. **The one action.** What should a visitor do before leaving? Book, buy, sign up, read on, get in touch.
4. **Tone.** Ask for something specific, not "clean and modern": calm, technical, playful, luxurious, rugged, editorial, warm, severe. Invite a few words of vibe and a colour they already own, if any.

Always offer the way out: "Or say *go ahead* and I'll choose, and tell you what I chose."

## When not to ask

- The prompt or project files already answer the open points.
- The request is a small edit, a polish, a review or motion only.
- Nobody can answer (a scheduled or unattended run). Choose, then state the choices at the top of the reply.

Guessing is acceptable for audience, action and tone. **Facts are never guessed.** Figures, quotations and logos appear only when someone supplied them.

## The material inventory

Before designing, write one line in three parts. It decides the shape of the page more than any style choice.

- **Real:** every concrete thing available (product name, claims the client makes, prices, locations, dates, photos).
- **Pictures:** each visual the page will carry, and its origin: the client's files, screenshots of the product, the product rebuilt in code, or stock photography as a stand-in to be replaced.
- **Missing:** proof the page will not have (no reviews, no logos, no usage numbers). The design must work without it, not paper over it.

A page with strong pictures should lead with them. A page with only words should be built from type, structure and facts, not from decorative blobs pretending to be imagery.

## Detect the stack

Read `package.json` and the lockfile for React, Next, Vue, Nuxt, Svelte, Astro, Tailwind version, an existing component library (shadcn, Radix, Base UI, React Aria, reka-ui) and motion libraries (Motion, GSAP, Lenis). If there is no project yet and the stack matters, ask once. For a standalone mock-up with no constraints, one self-contained HTML file is the default.

## Pick the mode

Using the table in SKILL.md, record the mode of this surface: Sell, Work, Read or Show. One product can have surfaces in several modes; decide per screen.
