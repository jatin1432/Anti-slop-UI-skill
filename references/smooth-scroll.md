# Smooth scroll

Read this only for Sell and Show pages whose scroll drives animation: pinned scenes, scrubbed sequences, parallax, or WebGL that follows the scroll. The library covered is [Lenis](https://github.com/darkroomengineering/lenis), which evens out wheel and trackpad scrolling on top of the browser's own scroll. Because native scrolling stays in place, sticky elements, anchor links, in-page search and assistive technology are unaffected.

## When to use it, and when not

| Use smooth scroll | Do not |
| --- | --- |
| A landing or brand page with a scroll-driven story | Dashboards, admin screens, editors, forms |
| Scrubbed or pinned animation (for example with GSAP ScrollTrigger) | Documentation and long reading pages |
| WebGL or canvas scenes that must stay in step with the scroll | A page that only needs smooth jumps to anchors: CSS `scroll-behavior: smooth` is enough there |

Smooth scroll is a tool for evenness, not an effect in itself. If the page has no scroll-driven motion, leave the native scroll alone.

## Setup checklist

1. **Install the package** using whichever package manager the project already uses. A single package serves plain JavaScript, React, Vue and Nuxt.
2. **Load its stylesheet** (`lenis/dist/lenis.css`). Skipping it breaks things more often than anything else, because it takes care of page height, overflow while paused, nested scrolling areas and iframes.
3. **Choose exactly one frame driver.** Lenis only moves when it is told to advance each frame:
   - nothing else runs a frame loop: let Lenis run its own;
   - GSAP is on the page: turn Lenis's own loop off and advance it from GSAP's ticker;
   - the project has its own loop: advance Lenis from that loop.
   Two drivers at once make scrolling jumpy.
4. **Use the framework wrapper** where there is one: in React and Next.js a root-level provider in the main layout; in Vue and Nuxt the equivalent component or module. Use the root option so it scrolls the page itself.
5. **Clean up:** destroy the instance when its owning page or component unmounts.

## With GSAP ScrollTrigger

- Update ScrollTrigger from Lenis's scroll event.
- Advance Lenis from GSAP's ticker, converting GSAP's seconds to the milliseconds Lenis expects.
- Turn off GSAP's lag smoothing so scrubbed animations do not drift behind the scroll after a slow frame.

## Common problems

- **Jittery or doubled speed:** two frame drivers are running.
- **Inner panels will not scroll** (modals, code blocks, dropdown lists): mark them so Lenis leaves their scrolling to the browser.
- **Anchors jump instead of gliding:** enable Lenis's anchor handling or call its scroll-to method from the link.
- **Stutter in scroll callbacks:** the callback is doing too much work per frame. Read values and write styles directly; no layout reads, no framework state updates on every frame.

## Reduced motion

When the person prefers reduced motion, do not start smooth scrolling at all, and turn scrubbed sequences into simple, readable static sections. Native scroll is always the safe fallback.
