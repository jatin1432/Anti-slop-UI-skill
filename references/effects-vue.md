# Effects and motion in Vue and Nuxt

Read this when a Vue or Nuxt project needs motion or animated effects. The rules in `motion.md` apply to everything here, and the effect budget in `effects-react.md` applies unchanged. Library steps change over time: confirm them against each library's current docs.

## Pick the route

| The project has... | Route |
| --- | --- |
| shadcn-vue components, or components built on reka-ui | Animate UI's Vue package (`@animate-ui/vue`), which gives reka-ui primitives built-in motion through Motion for Vue (`motion-v`) |
| A section that needs a visual effect (background, text effect, gallery, cursor, device mockup) | One Inspira UI component, copied into the project |
| Custom markup, or nothing above fits | Hand-written motion with `motion-v`, Vue's own `<Transition>`, or CSS, following `motion.md` |

Use what is already installed first. Never add a second library for the same job.

## Animate UI for Vue

Swap reka-ui primitive imports for Animate UI's Vue versions of the same primitives, and remove the component's own enter and exit animation classes so two animations do not run at once. The component API stays the same; only the motion changes. Check [Animate UI's docs](https://animate-ui.com/docs) for the current Vue setup.

## Inspira UI

[Inspira UI](https://inspira-ui.com) is a free collection of more than 150 animated components for Vue and Nuxt, many of them Vue ports of popular React effect libraries. It is not installed as a package of components: you set up Tailwind CSS and its few supporting libraries (`motion-v` and VueUse among them), then copy the components you need into the project and adapt them. Its current version targets Tailwind CSS v4; an older version exists for v3.

Because the code is copied in, it becomes the project's code. Rename props and classes to the project's conventions, and replace any colours with the project's tokens.

Its components fall into families. How each fits this skill:

| Family | Examples | Use when | Avoid when |
| --- | --- | --- | --- |
| Text effects | text reveal, flip words, letter pull-up, typewriter, morphing text | The hero's one living moment or a single key line | On every heading; "sparkles" or glitch text without a reason in the subject |
| Backgrounds | aurora, particles, stars, silk, vortex, grid patterns, liquid backgrounds | The subject is atmospheric or technical and the background means something | As filler behind a weak hero; glow with no source |
| Galleries and carousels | 3D carousel, circular gallery, expandable gallery, images slider, photo gallery | There are many real images and browsing them is the point | Holding stock or placeholder images |
| Cards and hover | 3D card, spotlight card, glare card, direction-aware hover | A grid of real work or products that rewards exploring | Ordinary feature lists; nested cards |
| Cursors | fluid, smooth, tailed, image-trail cursors | Show pages (portfolios, art, playful brands) on fine-pointer devices only | Work screens; any page where precision matters |
| Mockups | iPhone, Safari frames | Showing real screenshots of the real product | Holding drawn or empty screens |
| Scroll and layout | container scroll, tracing beam, timeline, scroll island | A story that unfolds with the scroll on a Sell or Show page | Docs and tools |
| Social proof | logo cloud, marquee, animated testimonials | Real logos and real, attributed quotes | Anything invented |
| Data and maps | globe, world map, animated beam | The product truly spans places or connects systems | Decorative "global" signals |

## Nuxt specifics

- Animate only on the client: wrap browser-only effects in `<ClientOnly>` or load them as client components, and give them a sensible static fallback so the server HTML is not empty.
- Read reduced motion and screen size in a way that matches between server and client, so hydration does not throw the page away and re-render it.
- Pause canvas and WebGL backgrounds when off screen or when the tab is hidden; these are the heaviest effects in the collection.
