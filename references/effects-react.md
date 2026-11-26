# Effects and motion in React and Next.js

Read this when a React or Next.js project needs motion or animated effects. The rules in `motion.md` apply to everything here. Library commands change over time: confirm them against each library's current docs before running them.

## Pick the route

| The project has... | Route |
| --- | --- |
| shadcn/ui components (a `components.json` file) and wants them animated | Animate UI's CLI, which swaps the components' primitives for animated ones |
| Components written by hand on top of a primitive library (Radix, Base UI, React Aria) | Change the import to Animate UI's animated version of the same primitive |
| A section that needs a visual effect (background, text effect, marquee, device mockup) | One Magic UI component, installed through the shadcn registry |
| Custom markup, or nothing above fits | Hand-written motion with the Motion library (or CSS), following `motion.md` |

Use what is already installed before adding anything. Never add a second animation library alongside one the project already uses for the same job.

## Animate UI (motion for primitives)

[Animate UI](https://animate-ui.com) offers animated versions of the common primitive libraries (Radix, Base UI, React Aria), keeping each library's API unchanged and adding motion, using the Motion library.

- **shadcn/ui projects:** add `@animate-ui/react` and `motion`, then run the Animate UI CLI's `animate` command on the components (preview first with its dry-run option). It rewrites the imports and removes the CSS animation classes it replaces. Do not hand-edit what it changed; if the output looks wrong, report it.
- **Hand-built on a primitive library:** swap the import path to Animate UI's version of that primitive and remove the component's own enter and exit animation classes, so two animations do not fight.
- **Whole-app pace:** a single provider setting scales the speed of all its animations together. Reach for it when the complaint is about the app as a whole ("everything feels slow"), instead of tuning each duration.
- Its licence lets you use the components in any app or site; it does not allow reselling the components themselves.

## Magic UI (section effects)

[Magic UI](https://magicui.design) is a registry of animated components for React with Tailwind. It installs through shadcn, so the project needs shadcn initialised first. Components land in the project's `components/ui` folder and are edited like the project's own code.

Customise through props and classes; keep the component's internals unless there is a clear reason to change them. Add any keyframes or extra packages the component's docs list.

## The effect budget

Effect libraries make it easy to stack exactly the flourishes that make a page look generated. Hold to these limits:

- **One high-motion effect per screen,** and it should be the page's signature or support it. Start with one core effect and at most one supporting effect for the whole page.
- **No effect that fakes proof.** A logo marquee needs real logos the client may use; an animated counter needs a real number; a testimonial carousel needs real, attributed quotes.
- **Text stays readable** over animated backgrounds: check contrast on the busiest frame.
- **Decoration never on Work screens.** Dashboards and tools take feedback motion only.

How common effect families fit this skill:

| Effect family | Examples | Use when | Avoid when |
| --- | --- | --- | --- |
| Text reveals and rotations | blur fade, word rotate, text animate | The hero's one living moment, or a single key line | On every heading; sparkle text in general |
| Ambient backgrounds | grid or dot patterns, particles, flickering grid, warp | The subject is technical or spatial and the pattern means something | As filler behind a weak hero; glowing blobs with no light source |
| Marquees and rails | marquee, logo rail | Real logos, real work samples, or the brand name as a design element | Fake or placeholder logos |
| Shiny and shimmer buttons | shimmer, shiny, rainbow buttons | Rarely, for a single playful brand | As the default primary button |
| Device and browser mockups | phone, browser frames | Showing real screenshots of the real product | Holding drawn or empty placeholder screens |
| Numbers | number ticker | A real figure supplied by the client | Invented statistics |
| Globes, beams, orbits | globe, animated beam, orbiting circles | The product truly connects places or systems | Generic "AI" or "global" decoration |

## Hand-written motion

When writing motion directly with Motion or CSS:

- Put motion code in client components (`'use client'` in Next.js) and keep server pages server-side by moving only the animated part into its own component.
- Read reduced motion and screen size with hooks that are safe during server rendering, so the first render matches the server's HTML.
- Wrap exiting elements so their exit can play, and put the exit transition on the exit itself.
- Animate the primitive's own element (for example by passing `asChild` on Radix parts) rather than wrapping it, so its data attributes and styling hooks still apply.
- Name one value per motion role (press, popover, dialog, sheet, page) in the tokens and reuse it.
