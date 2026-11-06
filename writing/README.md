# Writing

Hand-maintained static section. No build step.

## Adding a post

1. Copy `hello-world/index.html` to `<slug>/index.html`. Slugs are lowercase, hyphenated, and permanent.
2. Update: `<title>`, `description`, canonical URL, Open Graph tags, `article:published_time`, and the JSON-LD block (`headline`, `description`, `url`, `@id`, `mainEntityOfPage`, dates).
3. Write the body inside `<article>`. First paragraph gets `class="lede"`. Use `h2` for sections. Links to PDFs go in `/pubs/`; images go in `<slug>/` alongside the page.
4. Add an entry to the top of the list in `index.html` (title, date, summary) with `data-tags="tag-a tag-b"` and matching `<a class="tag">` links. Put the same tags under the post byline and in the JSON-LD `keywords`.
5. Add an `<item>` to the top of `feed.xml` and bump `lastBuildDate`. Dates are RFC 822, e.g. `Thu, 05 Nov 2026 00:00:00 +1100`.
6. Check the page locally (`python3 -m http.server` from the repo root), then PR.

## Tags

Lowercase hyphenated slugs, added as needed. The filter list on `/writing/` is built from the
`data-tags` attributes at load time, so there is no separate list to maintain. `/writing/?tag=<slug>`
is a linkable filtered view. Keep the set small and reuse before inventing. In use so far:

- `site` — notes about this site itself
- `aeo-forum-2026` — companion pieces to talks at the Advancing Earth Observation Forum 2026, Hobart
- `earth-observation` — EO sector, systems and policy
- `space-infrastructure` — orbital computing, communications and shared platforms

## Conventions

- Dates shown as `5 November 2026`, with a matching `<time datetime="YYYY-MM-DD">`.
- Summary is one sentence; it is reused as the meta description and feed description.
- Shared styles live in `/assets/site.css`. Add article styles there, not inline.
- `og.png` is the default social image. A post-specific image can override it in the Open Graph and JSON-LD `image` fields.
