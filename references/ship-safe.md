# Ship-safe: browser-side security checks

Read this at stage 4 for any interface that renders user or third-party content, stores anything in the browser, embeds or is embedded by other sites, or loads outside scripts. These are quick checks a designer-developer can make before shipping. They are not a full security audit; for that, use a dedicated security review.

A finding needs two things: a source an attacker can influence, and a place where that input does something harmful. Name both. Framework escaping, the browser's same-origin rules and a content security policy are real protections; confirm whether they apply before raising alarm.

## 1. Raw HTML sinks

Check every place that inserts HTML as markup rather than text:

- React `dangerouslySetInnerHTML`, Vue `v-html`, `innerHTML`, `outerHTML`, `insertAdjacentHTML`, `document.write`.
- Markdown or rich-text renderers configured to allow raw HTML.
- URLs built from input and placed in `href` or `src` (watch for `javascript:` URLs).

Each one either receives only trusted content, or is passed through a well-known sanitiser first. Content that arrives from the URL, from storage, from another window or from an API that stores user input is not trusted.

## 2. Messages between windows

For every `message` event listener: it checks the sender's origin against an exact allowlist (not "contains" or "ends with"), and validates the shape of the data before acting on it. When sending, it names the target origin instead of `*` for anything sensitive.

## 3. Tokens and private data in the browser

- Login tokens, personal data and private API responses in `localStorage`, `sessionStorage`, IndexedDB or caches: are they cleared on logout and account switch, and could a less-trusted script on the same origin read them? Prefer short-lived tokens in secure, http-only cookies where the backend allows it.
- Service workers do not serve one user's cached private pages to another after logout or account switch.
- No secrets (API keys with write access, private tokens) in client-side code or public environment variables.

## 4. Third-party code

- Scripts and stylesheets loaded from a CDN pin an exact version, and use subresource integrity where the CDN supports it. This includes animation and scroll libraries loaded by URL.
- Analytics, chat and embed widgets are the ones the person asked for, loaded from their official sources.
- `target="_blank"` links to other sites carry `rel="noopener"` (modern browsers default to it; adding it costs nothing).

## 5. Being embedded

Pages with sensitive actions (payment, settings, deleting things) should refuse to be framed by other sites, through the `frame-ancestors` content security policy directive or the equivalent header, so a hostile page cannot overlay them with a disguise.

## 6. Forms

- Forms that change data are protected against cross-site requests, by the framework's built-in mechanism or same-site cookies.
- Validation in the browser is for the person's convenience only; the server validates again.
- Autocomplete attributes are set correctly, so password managers fill the right fields and never fill hidden ones.

## Reporting

In the delivery note, list each finding with the file and line, the source, where it lands, and the fix, marked as confirmed or "needs checking" when it depends on server behaviour or deployed headers that could not be seen. If nothing applied, say "ship-safe checks: nothing found" and which sections were relevant.
