# Motion

Read this when the page moves, or when asked to animate something. Library routes are in `effects-react.md` and `effects-vue.md`; this file holds the rules that apply on any stack, including plain CSS.

## Decide whether it should move

Every motion needs a purpose you can name in one word:

- **Feedback:** it answers something the person did (press, toggle, submit).
- **Place:** it shows where something came from or went (a menu growing from its button, a sheet sliding from its edge).
- **State:** it shows that something changed (saved, copied, loaded).
- **Continuity:** it shows the same object moving or changing shape.
- **Delight:** an occasional moment that deserves some theatre (the hero's living moment, a success screen).

If no word fits and nobody explicitly asked for motion, leave it still. A direct request to animate something is always honoured; the only question is which form fits it best.

When a request names no level, offer three, with what each would look like on this component: **subtle** (quick, small, functional), **more** (noticeable, with some character), **expressive** (bold, playful, worth watching). In unattended runs, choose subtle and say so.

## How often it is used decides how fast it is

| Used | Examples | Treatment |
| --- | --- | --- |
| All day | buttons, toggles, tabs, tooltips, menus, hover highlights | Very quick (roughly 100 to 200ms), small distances, no waiting |
| Sometimes | dialogs, sheets, popovers, selects, toasts, accordions | Unhurried but brief (roughly 200 to 400ms), clear origin |
| Rarely | page entrances, success moments, onboarding, the hero moment | Free to take longer and have more character |
| Opened by keyboard many times a day | command palettes, global shortcuts | Barely there: a very brief opacity change with a hint of growth, or none at all |

These ranges are starting points; tune by eye in a slowed-down browser.

## How things move

- **Springs** suit things the person touches (presses, drags, popovers); a little overshoot makes them feel alive. Keep it small for frequent controls.
- **Ease-out** for things entering or leaving. Menus, accordions and sheets, which people watch as they open, take a gentler version of the curve.
- **Ease-in-out** for things that travel across the screen.
- **No ease-in for entrances.** It feels sluggish at the start, which is when people are watching.
- **Linear** only for constant motion (progress, marquees) and for following a finger.
- **Exits are quicker than entrances** and usually mirror them.

## Where things come from

- Menus, popovers and tooltips grow from their trigger, starting at about 70 to 90 percent of their size, not from the centre of the screen.
- Dialogs stay centred and appear from slightly smaller and transparent; their backdrop fades and blurs in from nothing.
- Sheets and drawers slide in from their edge by their own size.
- A swap of two states in place (copy to copied, play to pause) cross-fades, optionally with a light blur to hide the seam.
- A press scales down very slightly (about 97 percent; less for a whole card or row). Hover changes colour, background, border or shadow, not size.

## Quality rules (these are correctness, not taste)

1. **Reduced motion.** Under `prefers-reduced-motion: reduce`, movement goes; fades may stay. Things still appear and disappear.
2. **Focus survives motion.** Focus rings appear instantly and are never clipped by an animation's overflow. Things that are leaving or hidden cannot receive focus. Overlays move focus inside when they open and return it to the trigger when they close.
3. **The keyboard gets the same motion as the pointer.**
4. **Hover effects only on devices that can hover** with a fine pointer; touch screens never get stuck hover states.
5. **The control responds on the same frame** as the input. Animation never delays the actual result.
6. **Interruptible.** Triggering again mid-animation redirects it smoothly instead of restarting from zero.
7. **Loops pause off screen** and when the tab is hidden.
8. **Animate transform and opacity** (filter, clip-path and mask when they stay smooth). Height only for accordions where content must push what is below. Never width, top, left or margin; never `transition: all`; list the properties you transition.
9. **Nothing stretches.** When a box resizes, its text and images keep their proportions. Changing text fades or slides; it never scales.
10. **Content visible by default.** Entrance animations start from a visible state or reveal quickly; with scripts off or slow, nothing stays invisible. Never hide the main heading until hydration.
11. **Pointer and scroll values** are not routed through framework state on every frame; use the motion library's own values or direct style updates.

## Page-level motion

- **One authored moment per page** (the hero's living moment, or one orchestrated load) beats effects scattered everywhere.
- **No identical fade-up on every section.** If sections animate in, vary by content or let most of them simply be there.
- **Scroll-driven sequences** belong to Sell and Show pages that tell a story; pin a stage, scrub through it, release. They need `smooth-scroll.md` and a full reduced-motion path.
- **Work and Read surfaces** move only for feedback, place and state.

## Checking motion

- Slow animations down (browser dev tools at 10 to 25 percent) and look at middle frames, not only start and end: nothing passes over text it should not, neighbouring text does not jump, every part that changes state animates.
- Trigger twice quickly; it should redirect, not restart.
- Turn on reduced motion and repeat the main flow.
- Use the keyboard for the main flow.
- Without a browser, check the code against the rules above and say in the delivery note that motion was not watched.
