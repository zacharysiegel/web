# Microblog panel

A panel on `public/index.html` holding hand-picked copies of tweets from `@siegelzc`.

## Content

- Copies are static HTML pasted into the page; no JavaScript and no runtime dependency on X.
- Newest first.
- Text and date come from X's public oEmbed endpoint: `https://publish.x.com/oembed?url=<tweet URL>`.
- Images are saved under `public/microblog/` as `<tweet-id>-<n>.<extension>`.

## Entry markup

```html
<article class="microblog-entry">
    <blockquote class="microblog-context"><a href="https://x.com/<handle>/status/<id>">@<handle></a>: quoted text</blockquote>
    <p>Text; one paragraph per tweet of a thread.</p>
    <img src="microblog/<tweet-id>-1.jpg" alt="…" loading="lazy">
    <a class="microblog-date" href="https://x.com/siegelzc/status/<tweet-id>"><time datetime="YYYY-MM-DD">YYYY-MM-DD</time></a>
</article>
```

`blockquote` only for a reply or quote tweet; `img` only when the tweet has images.

## Layout

- Grid areas: `main` (projects), `aside#microblog`, `footer`.
- Wide viewports: `main` and `footer` in the left column, panel in the right column, `position: sticky` at the top with its own vertical scroll.
- Narrow viewports: one column ordered `main`, panel, `footer`.
