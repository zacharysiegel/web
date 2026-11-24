# Thoughts panel

A panel on `public/index.html` holding hand-picked copies of tweets from `@siegelzc`.

## Content

- Copies are static HTML pasted into the page; no JavaScript and no runtime dependency on X.
- Newest first.
- Source: `https://cdn.syndication.twimg.com/tweet-result?id=<tweet id>&token=a` returns text, UTC timestamp, quoted tweet, reply parent and image URLs.
- A thread is one entry flattened into prose: `n/n` markers removed, sentences split across tweets rejoined, the author's paragraph breaks kept. The date links to the first tweet.
- Displayed date: US Central. `datetime` attribute: the UTC timestamp.
- Images are saved under `public/thoughts/` as `<tweet-id>-<n>.<extension>`.

## Entry markup

```html
<article class="thoughts-entry">
    <blockquote class="thoughts-context"><a href="https://x.com/<handle>/status/<id>">@<handle></a>: quoted text</blockquote>
    <p>Text.</p>
    <img src="thoughts/<tweet-id>-1.jpg" alt="…" loading="lazy">
    <a class="thoughts-date" href="https://x.com/siegelzc/status/<tweet-id>"><time datetime="YYYY-MM-DDTHH:MM:SSZ">YYYY-MM-DD</time></a>
</article>
```

`blockquote` only for a reply or quote tweet; `img` only when the tweet has images.

## Layout

- Grid areas: `header` (name and position, full width), `main` (projects), `aside#thoughts`, `footer`.
- Wide viewports: `main` and `footer` in the left column, panel in the right column, `position: sticky` at the top with its own vertical scroll.
- Narrow viewports: one column ordered `header`, `main`, panel, `footer`.
