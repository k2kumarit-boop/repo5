A small blog website in a soft, light, visionOS-inspired style. It is a **single `index.html` file** with no build step and no dependencies other than a Google Fonts link.

**Author:** [@k2kumarit-boop](https://github.com/k2kumarit-boop)

## Features

- Frosted glass panels with a soft highlight that follows the pointer
- Left floating tab bar that expands on hover (becomes a bottom bar on phones)
- Smooth scroll animations: rising headlines, fade-in cards, drifting background shapes, scroll progress line
- Essays page with live search and topic filter
- Illustrated cover on every essay
- Author, date, and reading time on each essay
- Pull quote inside each essay
- "On this page" floating panel with active section highlight (wide screens)
- Floating **Copy link** and **Back to top** bar
- Related essays, matched by topic
- Equal-size cards across the whole site
- Light and dark mode that follow the system setting
- Respects `prefers-reduced-motion`

## Pages

| Page | Link |
|---|---|
| Home | `#home` |
| Essays (search and filter) | `#essays` |
| Individual essays | `#read-slowly`, `#keep-a-journal`, and so on |
| About | `#about` |
| Contact | `#contact` |

The site uses hash links, so it works on any static host without server setup.

## Run locally

Open `index.html` in a browser. That is all.

## Publish on GitHub Pages

1. Create a repository, for example `marginalia`.
2. Upload `index.html` and `README.md` to the `main` branch.
3. Go to **Settings → Pages**, choose the `main` branch and the `/ (root)` folder, then save.
4. After a minute the site is live at `https://k2kumarit-boop.github.io/marginalia/`.

## Add a new essay

All content is in the `P` array inside the `<script>` tag. Add an object like this before the `about` entry:

```js
{
  id: 'my-new-essay',            // link: #my-new-essay
  par: 'essays',                 // keeps "Essays" highlighted in the tab bar
  d: 'Nov 20, 2026',             // date shown under the title
  q: 'A sentence for the pull quote.',
  cat: 'Reading',                // topic (see the HUE list below)
  m: '3 min',                    // reading time
  n: 'My new essay',             // title on cards
  sum: 'One sentence summary for the card.',
  s: 'Reading',
  h: 'My new essay.',            // big headline on the essay page
  l: 'Reading · 3 min read',
  b: [
    { t: 'article', p: [
      'First paragraph.',
      '## A section heading',    // lines starting with ## become headings
      'Another paragraph.'
    ]},
    { t: 'more', h: 'Keep reading' }
  ]
}
```

The essay appears on the Home page, the Essays page, and the topic filter automatically.

> New topic? Add it to the `HUE` object (for example `Travel: 200`) so it gets a cover color.

## Block types

| `t` | What it shows |
|---|---|
| `article` | Cover, glass article panel, pull quote, and author card |
| `latest` | The newest essays (`n` = how many) |
| `more` | Two related essays |
| `index` | Search box, topic buttons, and all essays |
| `cols` | Cards with a title and text: `[title, text]` |
| `follow` | A "Follow along" card linking to GitHub |
| `link` | A centered button: `[label, url]` |

## Change the colors

Colors are CSS variables at the top of the `<style>` tag.

```css
:root{
  --text:#1d1d1f;     /* main text */
  --muted:#6e6e73;    /* secondary text */
  --accent:#0071e3;   /* buttons and active items */
  --b1:#cfe0ff;       /* background shape colors */
  --b2:#ffe1d6;
  --b3:#e4dcff;
}
```

Dark mode values are in the `@media (prefers-color-scheme:dark)` block directly below. Update both so the themes match.

## Notes

- The essays and dates are sample content. Replace them with your own writing.
- The Follow card links to GitHub because the site has no email or newsletter service behind it.
- Fonts load from Google Fonts. Without internet, the site falls back to system fonts.

## License

MIT

