# Quality floor

Read this at stage 4, and when auditing existing UI. Part 1 is the hard rules, which never bend. Part 2 is the list of AI tells, which are defaults to avoid unless the brief asks for them. Part 3 is the craft checks.

All checks are made on the rendered result, together in one look: render, check everything, fix everything found, then look again. Do not re-render after every small tweak.

## Part 1: Hard rules

A failure here blocks delivery. A pinned brief cannot override these.

| # | Rule | How to check |
| --- | --- | --- |
| 1 | Every colour, font family, size step, radius, spacing and motion value comes from a named token | Search the styles for raw colour values and font families outside the token block |
| 2 | No invented proof: no made-up metrics, ratings, reviews, testimonials, client logos, awards or user counts | Every number, quote and logo traces to the person or the project; anything else is a marked slot |
| 3 | Visible keyboard focus on every interactive element, appearing instantly | Tab through the page |
| 4 | Reduced-motion version of everything that moves; content readable with scripts off | Turn on reduced motion; disable scripts and reload |
| 5 | Contrast: body and placeholder text at least 4.5:1, large text and icons at least 3:1 | Measure the actual pairs, including text over images |
| 6 | No sideways scrolling at widths from 320 to 1920px | Resize; long words and headings wrap |
| 7 | Motion uses transform and opacity (filter and clip-path when smooth). `transition: all` is not allowed, and layout properties (width, top, left, margin; height outside accordions) are not animated | Read the transitions and animations |
| 8 | Hero headline, its sentence and the main action visible without scrolling at 1280 by 800 and 390 by 844 | Render both |
| 9 | One real icon set, one stroke weight; no emoji or unicode symbols as icons | Look |
| 10 | Controls have hover, focus, pressed, disabled and loading states; forms and lists also have error and empty states | Trigger each one |
| 11 | Form fields have visible labels; errors appear next to the field and say how to fix them | Submit empty and wrong values |
| 12 | Body text 16px or more; touch targets at least 44 by 44px on touch screens | Measure |
| 13 | Content container capped and centred; at 1920px the margins grow, the line length does not | Render at 1920 |
| 14 | Images have meaningful alt text, or empty alt when decorative; the page has one `h1` and headings in order | Read the markup |

## Part 2: AI tells

Each of these is a default that generated pages reach for whatever the subject. One on its own is rarely fatal. **Count them.** Zero or one: fine. Two or more: the page will read as generated; remove them, starting with the most visible. When the brief explicitly asks for one, keep it and note that in the delivery note.

### Type and words
- A tiny all-caps label with wide letter spacing above a heading (an "eyebrow"). Treat this one as a near-ban: the heading should stand on its own.
- One word in a headline set in italic, a different colour or a gradient.
- Two-word or three-word sentence headings in a row ("Pure sound. Every moment.").
- Filler words that sound premium and say nothing: "quiet", "real", "seamless", "effortless", "elevate", "unlock", "crafted".
- The usual display font for this kind of page, chosen because it is usual (a fashionable serif on every "premium" page, the same geometric sans on every SaaS page).
- Monospace used for small labels to look technical when nothing is code or data.
- Meta lines joined with middle dots ("Titanium · Spatial · 60h battery").
- An arrow glued to every link and button label.
- Labels written as "WORD — fragment" with a spaced dash.

### Layout and structure
- Three cards in a row, each with an icon, a heading and a sentence. The single most common tell.
- Everything wrapped in bordered cards; worse, cards inside cards.
- Section numbers (01, 02, 03) when the content is not a sequence.
- The hero-stats template: a big number, a small label, a row of supporting stats.
- A badge pill above the headline ("New", "v2.4", "Now with AI").
- The default page run: hero, logo rail, three features, steps, testimonials, pricing, email signup, whatever the subject.
- Every section centred.
- A coloured thick left border on quotes, callouts and alerts.

### Surface and colour
- A warm cream background by default.
- A near-black background with one neon accent by default.
- Purple-to-blue gradients, gradient text, gradient washes as decoration.
- Blurry glowing blobs or orbs behind the hero with no light source.
- Glassmorphism used as decoration rather than to show layering.
- The same soft grey shadow under every element.
- Identical corner rounding on every element, large or small, outer or inner.
- Hard offset "neo-brutalist" shadows on a page that is not otherwise brutalist.
- Near-black tints (#0B0B0B, #111) used in place of a decided dark colour.

### Motion and decoration
- The same fade-and-slide-up on every section.
- Hover lift or scale on every card.
- Pulsing green "live" dots where nothing is live.
- Sparkle icons or emoji on buttons that have nothing to do with AI.
- Dithered or halftone photos used as a costume.
- Animated counters for numbers that matter little.

### Proof and content
- Made-up statistics (also a hard-rule failure).
- Placeholder logos in a "trusted by" rail (also a hard-rule failure).
- Generic stock photos of people pointing at laptops.
- Copy that could describe any product in the category.

## Part 3: Craft checks

Not blocking, but each one answered before delivery.

- **Hierarchy:** within three seconds, can you say what leads the first screen and what the main action is?
- **Spacing:** tight inside groups, generous between them, more space above headings than below. Read the computed values, not the intentions.
- **Type:** body line length 60 to 75 characters; obvious steps between levels; no single word alone on the last line of a heading; real copy tested at every width.
- **Colour:** one accent, used for meaning; secondary text tinted, not plain grey; dark mode checked separately if present.
- **Depth:** shadows have an offset and blur and are faint; no glow pretending to be depth.
- **Browser surfaces:** selection colour, caret, scrollbars, link underlines, form controls and focus rings are themed.
- **Real content:** names, numbers and dates of realistic, varied lengths; nothing reads as lorem ipsum.
- **Coverage:** every requirement in the brief is present and findable within a few seconds.
- **The memorable thing:** the page has one, and it is on the first screen.
- **Restraint:** before finishing, remove one decorative element. If the page is not worse, leave it out.
