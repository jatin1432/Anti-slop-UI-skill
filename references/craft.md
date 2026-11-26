# Craft: building the page

Read this at stage 3. It covers tokens, layout, type, colour, imagery, copy, the browser's own surfaces and responsive behaviour. Motion lives in `motion.md`.

## Order of work

1. **Tokens first.** Define colour, type, spacing, radius, shadow and motion values as named variables before writing any component. Existing projects keep their token names.
2. **Hero first.** Build the navigation and the first screen, render it, fix it. Only then build the sections below. A weak hero is not rescued by strong sections.
3. **Main states before more pages.** The main flow must reach its result (submitted, saved, purchased), not only look good in its default state.
4. **The key picture before the layout around it.** Choose or make the main image first, then arrange type and actions around it. Never leave the picture as the last thing to fill in.

## Layout

- **Group with space before lines.** Related items sit close; groups sit far apart. If that is not enough, change size or weight. Only then change background. Borders and boxes are for things that are clickable as a whole, inputs, and surfaces that float. Never a box inside a box.
- **One container width,** capped and centred. On very wide screens the margins grow; line lengths and grids do not.
- **Consistency rules for the page:** a single column gap under the first screen, the same corner radius for elements at the same depth, and a single style for primary buttons everywhere.
- **Fewer, larger sections.** Six to nine sections for a Sell page, including hero and footer. Fullness comes from scale and pictures, not from more blocks of text.
- **Words per screen.** Aim for about 80 visible words per screen on a Sell page. A hero holds a headline (7 words or fewer is a good target), one sentence, and one or two actions.
- **Build from the category's own content.** A restaurant page is built around its menu and its room; a festival around its line-up and dates; a tool around the tool. Not around a default run of "features, steps, testimonials, email signup".
- **Align with intent.** Left-aligned text is the default for anything longer than a line. Centre only short statements, and never centre more heading groups than you left-align.
- **Headings sit closer to their content.** The gap before a heading is larger than the gap after it, so the heading reads as part of the section it opens.

## Type

- **One or two families.** If two, make them clearly different in role and shape. A third only for a single special role.
- **Choose on purpose.** Never pick a face because it is the usual choice for this kind of page. The face should come from the subject (a wide grotesque for engineering, a humane serif for books, a rounded face for a children's product) and be self-hosted or loaded properly.
- **A real scale.** Pick a ratio and stick to it. Make steps between levels obvious: a headline should not be "slightly bigger" than a subheading.
- **Body text:** 16px or more, line length roughly 60 to 75 characters, line height about 1.5 for sans and a little more for serif.
- **Display type:** tighten line height and letter spacing slightly as size grows; balance multi-line headlines so no line holds a single word.
- **Headings in one weight and one colour.** Emphasis comes from size, weight or position, never from one word in italic or a different colour.
- **Small text uses the main text font.** Labels, captions, table headers and navigation are set slightly smaller than body copy, in sentence case, with normal letter spacing. No widely spaced capitals.
- **Numbers** in tables and prices use tabular figures so columns line up.

## Colour

- **A small palette:** four to six named colours, each with a role (background, surface, text, muted text, accent, and a status colour if needed).
- **One accent, used for meaning.** It marks the main action, the current selection, or the one thing to notice. If everything is accented, nothing is.
- **Tinted neutrals.** Greys borrow a little of the brand hue so the page feels of a piece. On a coloured surface, secondary text is a lighter or darker shade of that surface, not plain grey.
- **Depth from light.** Shadows have an offset and a soft blur and are faint. A coloured halo with no offset is decoration, not depth.
- **Dark mode** is designed, not inverted: lift surfaces in steps instead of using shadows, reduce saturation of bright accents, check every contrast pair again.
- **No gradient text.** No purple-to-blue gradients by default. A gradient must come from something in the subject (a sky, a material, a light).

## Imagery

- **Real before fake.** In order of preference: the client's own photographs and footage; captures of the actual product; a faithful rebuild of the product in code; carefully chosen stock as a clearly replaceable stand-in.
- **Never drawn stand-ins for real things.** No vague blobs, no fake app windows drawn by hand when the real product exists, no cartoon people unless illustration is the brand.
- **Treat images consistently:** one crop logic, one colour treatment, one corner style across the page.
- **Cut-outs are real cut-outs.** If a product floats over type, use a proper transparent image of it. A circle or polygon mask pretending to follow an object's edge looks cheap.
- **Pictures take their share, not the whole page.** Below the hero, let type and structure carry most sections; avoid two photo-led sections in a row unless the page is a gallery.
- **Credit stock and library images** in the footer or as the licence requires.

## Copy

Words are part of the design. Write them with the same care as spacing.

- **Say what it is, plainly.** Name things the way users think of them ("notifications", not "webhook config").
- **Buttons say what happens:** "Save changes", "Book a table", "Download the report". An action is called by one name from start to finish: a "Publish" button leads to a "Published" message.
- **Errors sit beside the problem,** name the cause, and tell the person their next move. They do not apologise and are never vague.
- **Empty states invite the next step,** with an action, not a mood.
- **Sentence case, active voice, no filler.** Cut words that sound good and say nothing (see the AI-tell list in `quality-floor.md`).
- **Real content, not lorem ipsum.** Names, numbers and dates vary in length like real ones. Placeholder data is listed in the delivery note, never presented as real.

## The browser's own surfaces

Parts nobody draws still ship with the page. Theme them from the palette; small details like these are what separate a crafted page from a template.

- Text selection colour and the text caret.
- Focus rings (visible, on brand, instant).
- Link underline thickness and offset.
- Scrollbars on scrolling panels.
- Form controls (checkboxes, radios, selects, date inputs) styled to match.
- `theme-color` meta for mobile browser chrome, and a favicon.

## Responsive

- Check at 390, 768, 1280 and 1920 widths at least.
- On phones, controls and nav text get relatively larger, not smaller; touch targets at least 44 by 44px.
- Desktop sidebars and filter columns become a menu or a sheet, never squeezed columns.
- Grids holding images use flexible tracks that can shrink to zero, and long headings are allowed to wrap, so nothing forces sideways scrolling.
- Modals and sheets keep their main button reachable on a short phone screen and when the keyboard is open.
- Inputs use at least 16px text so phones do not zoom in on focus.

## Code hygiene that affects the look

- Watch selector specificity so section and component styles do not cancel each other (a common cause of uneven section spacing).
- New styles are appended to existing stylesheets in the project's own conventions; existing tokens are reused, not duplicated.
- Fix problems at their source token or component, not with one-off overrides.
