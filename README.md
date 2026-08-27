# Data Analyst Portfolio — Single-File SPA

A self-contained, single-page portfolio site for a Data Analyst job search.
No build tools, no framework, no dependencies besides two Google Fonts.
Works by just opening `index.html` in a browser.

## What's in this zip

```
index.html   ← the entire site (HTML + CSS + JS, all in one file)
README.md    ← this file
```

Everything — structure, styling, and behavior — lives in `index.html`,
organized into clearly labeled sections so you can find things fast with
Ctrl+F / Cmd+F.

## 1. Edit your content (5 minutes)

Open `index.html` in any text editor and search for:

```
EDIT YOUR DATA HERE
```

That's the top of a single JavaScript object called `CONFIG`, near the
bottom of the file. It contains **all** the text on the site:

- `personal` — name, title, tagline, email, phone, LinkedIn, GitHub, résumé link
- `heroStats` — the three small stats under the hero buttons
- `heroChart` — the bar chart inside the spreadsheet hero (tool + %)
- `about` — your summary paragraphs + 3 highlight cards
- `skills` — your skill list with category + proficiency (0–100)
- `projects` — your case studies (business question, tools, impact, link)
- `experience` — your work history timeline
- `education` / `certifications`

Change the values inside `CONFIG`, save, and reopen the file — the whole
page rebuilds itself from that data. **You never need to touch the HTML or
CSS to update your content.**

A few things worth doing before you send this to anyone:

- [ ] Replace every placeholder link (`"#"`) with real URLs — especially
      `resumeUrl`, `linkedin`, and `github` in `personal`.
- [ ] Replace the sample projects with your real projects. Each one should
      have a genuine business question and a real, specific outcome —
      that's what makes a data portfolio credible to hiring managers.
- [ ] Double check `skills[].level` values are honest — they're meant to
      hold up against your projects.

## 2. Edit colors / fonts (optional)

Near the top of the file, search for:

```
DESIGN TOKENS
```

That's a block of CSS custom properties (`--color-...`, `--font-...`,
`--space-...`). Changing a value there updates it everywhere on the site.
For example, to swap the accent blue for a different color, just change:

```css
--color-accent: #2F5CFF;
```

## 3. Preview it locally

Just double-click `index.html`, or from a terminal:

```bash
# any static file server works, e.g.:
python3 -m http.server 8000
# then open http://localhost:8000
```

## 4. Deploy it (free options)

Any static host works since there's no build step:

- **Netlify / Vercel**: drag the folder onto their dashboard, or connect
  a GitHub repo containing this file.
- **GitHub Pages**: push this file to a repo as `index.html`, enable Pages
  in the repo settings.
- **Cloudflare Pages**: same idea — point it at a repo or upload directly.

## Design notes

The hero is built as a literal spreadsheet (column letters, row numbers, a
typing formula bar, and a live bar chart in a "chart cell") because that's
the actual daily material of a data analyst's job — it's meant to *show*
the skill set rather than just list it. Motion is limited to a handful of
purposeful moments (the formula bar typing once on load, bars filling in
as you scroll to them, numbers counting up) and everything respects
`prefers-reduced-motion` for users who've turned that on.

Browser support: standard CSS Grid/Flexbox, `IntersectionObserver`, and
`requestAnimationFrame` — all supported in current Chrome, Edge, Firefox,
and Safari. No bleeding-edge CSS features are used, so it degrades
gracefully on slightly older browsers too (animations just won't run if
`IntersectionObserver` is unavailable — content is still fully visible).
