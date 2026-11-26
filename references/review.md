# Review and hand-over

Read this at stage 5, and for review-only or audit requests.

## Self-check first

Before anyone else looks, render the work and check it yourself, in batches:

1. Render at the widths that matter (at least 390 and 1280; add 768 and 1920 for full pages).
2. Run every hard rule and craft check in `quality-floor.md` against that render, and count the AI tells.
3. Walk the main flow end to end, including one failure (a wrong input, an empty list, a failed save), with the mouse and with the keyboard.
4. For anything that saves data: save, reload, confirm it reads back.
5. Fix everything found in one batch, then render once more to confirm.
6. Run the project's type checks and linter. Run the full build and test suite only if the person asks.

A screenshot that was saved but not looked at is not a check.

## The fresh-eyes review

New pages and redesigns get one review from a reviewer who did not build them: a separate agent with no memory of the build, when one can be started, and able to see images. Small edits and polish get the self-check only.

Give the reviewer only:
- the screenshots (desktop and phone, plus key states),
- the brief in the person's own words,
- the mode of the surface,
- the hard rules and the AI-tell list from `quality-floor.md`.

Do not give the reviewer the plan, the reasoning, or what you think is good about it. Ask for:
1. **A verdict word:** *ship*, *fix* (specific issues, same direction), or *rethink* (the direction itself is not working).
2. **The three biggest problems**, most damaging first, each pointing at a visible place in a screenshot.
3. **The AI-tell count** with each tell named.
4. **A score out of 10** for how designed (not generated) it looks, and what would raise it by two points.

If the page has a main task flow (signing up, checking out, filling a form), ask a second reviewer to work out the page's purpose from the screenshots alone and walk the main path, reporting where they hesitated. Do not tell them the intended path.

Fix from the most damaging problem down. Re-check what changed yourself; another full review is optional. If no separate reviewer is available, review the screenshots yourself as a demanding outsider would, and write "not independently reviewed" in the delivery note.

## Review-only requests

When the person only asks for a review or audit, deliver evidence and recommendations and stop: no new directions, no edits. Group findings by hard-rule failures, AI tells and craft issues, each with where it is, why it matters and the suggested fix. Offer to fix the top two or three.

## The delivery note

Five short parts, in the person's language:

1. **Direction:** what was chosen and why, in two or three sentences.
2. **What was done:** pages, components and states built or changed, and the motion added.
3. **What is not real yet:** placeholder images, sample data, actions not connected to anything, missing proof slots and what belongs in each (with sizes for images).
4. **Checks:** what was verified, the AI-tell count, the review verdict and score, and anything that could not be checked (for example "visual result not checked", "motion not watched in a browser", "not independently reviewed").
5. **Next steps:** up to three options the person can pick, the first marked as recommended, each saying what it delivers and what it costs (time, new files, paid image credits). For example: "Build the pricing page (recommended): reuses this page's navigation, colours and components; adds one new page file." End with a line inviting them to reply with a number or describe a change.

Skip next steps for small edits, when stopping at a confirmation point, or when the person already said what comes next.

## Ask for the one missing piece

Close full-path builds by naming the one asset whose arrival would lift the page the most (a real product photo, a real customer quote with a name, actual usage numbers), and where it would go.
