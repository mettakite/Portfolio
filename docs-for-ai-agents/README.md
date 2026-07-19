# Docs for AI agents

Developers increasingly don't read documentation alone — they ask Claude, Cursor, or ChatGPT to help them integrate with a platform. When that happens, the docs stop being just a human reading experience and become a retrieval source: if an AI assistant can't find accurate, current content, it generates wrong code, and the developer blames the platform.

This folder is a small, self-contained demonstration of how I structure documentation for that reality. It uses **Acme Payments**, a genericized API-first payments platform modeled on the real documentation I owned at Finix and Nium (sanitized the same way as my [Docs Drift Script](https://github.com/mettakite/Docs-Drift-Script) examples).

## What's here

- **[llms.txt](./llms.txt)**: A curated index of the Acme docs site in the [llms.txt convention](https://llmstxt.org/) used in production by developer platforms like Stripe and Anthropic. It front-loads the facts an assistant must get right (core objects, units, current API version), orders sections by integration priority, and writes each link description as a retrieval hint, not a marketing line.
- **[payment-lifecycle.md](./payment-lifecycle.md)**: One example documentation page written retrieval-first, based on the end-to-end lifecycle pages I wrote at Finix.

## The choices, and why

**Every page is self-contained.** The lifecycle page defines all five API objects inline before using them. A human might arrive from the previous page; an assistant retrieves one chunk with no surrounding context. Self-containment serves both — it's "Every Page Is Page One," which good docs need anyway.

**Headings are questions where readers have questions.** "How long can an Authorization be captured?" matches how both humans and assistants actually query. Question-shaped headings make chunks land on the right query.

**One canonical example per concept.** Assistants trained on docs repeat the examples they find. A single, correct, complete sequence beats five partial variations — variation reads as richness to a human and as a contradiction to a model.

**Facts an assistant must not guess are stated flatly and early.** Important details are presented front and center to ensure any code that gets gneerated is generated accuratly. Details include, units (minor units/cents), object names, state names, and version applicability.

**Freshness is a feature, not a hope.** Stale content doesn't just mislead readers anymore; it produces confidently wrong AI answers. That's why I built the [Docs Drift Script](https://github.com/mettakite/Docs-Drift-Script), which audits documentation against the OpenAPI specification to catch drift before users — human or machine — hit it. This folder and that tool are two halves of one position: structure content for retrieval, and keep it verifiably accurate.

## What I'd do on a real platform

Ship the llms.txt from the docs pipeline (generated from the sitemap plus curated descriptions, so it can't drift), serve every page as plain Markdown alongside HTML, add retrieval checks to the docs CI (does each page define its own terms? does each concept have exactly one canonical example?), and measure agent answer quality against the docs the same way you'd measure search success.