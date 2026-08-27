# PersonalWebsite
Why I built, structure, how to improve, etc. 

## Why I built this

I wanted a portfolio site that actually says something about me instead of reading
like a resume template. The starting point was
[kentarobarnes.com](https://www.kentarobarnes.com/#experience) . I liked its dark,
minimal, developer-portfolio feel: bold section headers with a short accent underline, rounded bordered cards, a logo-and-line timeline for experience. I copied that *structure*, then made it mine, swapped in my own story (stats/econ;
journalism background; triathlon).

The core idea: one clean, fast, single-file site. No build step, no framework, no
dependencies beyond a Google Fonts link. If I ever forget how to run this, it's
just a static HTML file. Open it in a browser and it works.

## How the page is organized

Reading top to bottom, `index.html` is one long scroll broken into sections:

1. **Hero** — name, one-line intro, photo. This is the "who is this person" answer
   in under 5 seconds.
2. **`#about`** — three cards: *Currently* (what I'm doing right now), *Chat to me
   about* (personal interests — the stuff that makes me a person and not just a
   pipeline of skills), and *A little more about me* (professional angle, still a
   placeholder — I hadn't figured out how to phrase this when I first built the
   site).
3. **`#experience`** — a vertical timeline, one entry per role, each with a company
   logo, title, one-line description, and a row of skill tags. This is the section
   that matters most to anyone skimming for "is this person qualified" — so it's
   structured to be scannable, not read word-for-word.
4. **`#projects`** — same card pattern as experience, for things I built on my own
   time rather than for an employer.
5. **`#writing`** — this is the section that's different from a typical CS-student
   portfolio. Before switching into stats/econ I worked as a journalist at Free
   Malaysia Today (FMT), and I didn't want to bury that. It's a card grid of
   published articles, styled after FMT's own author-page layout, each one linking
   to the real published piece.
6. **Footer** — GitHub/LinkedIn, still placeholders.

The reasoning behind putting Writing *after* Experience and Projects rather than
before: recruiters skim top-down, and "can this person write clearly and work
independently" (journalism) is a supporting story, while "can this person do the
job" (experience, projects) is the headline.

## Technical choices, and why

- **Single HTML file, no framework.** For a portfolio this size, React or a static
  site generator would be more machinery than the problem needs. Everything —
  structure, styling, content — lives in `index.html`. Easier to reason about,
  easier to deploy, nothing to update or go stale.
- **CSS custom properties for the whole palette** (`--bg`, `--card`, `--accent`,
  etc. near the top of the `<style>` block). If I want to re-theme this later —
  different accent color, lighter theme — I change a handful of variables instead
  of hunting through the file.
- **`Space Grotesk` for headers, `Inter` for body text**, pulled from Google Fonts.
  Grotesk has the geometric, slightly technical feel that matches the dark
  developer-portfolio aesthetic; Inter is just a clean, high-legibility body font.
- **The article thumbnails are a mix of real and placeholder.** Ten of them have
  real images and publish dates — I got those by saving my FMT author page as a
  complete webpage and pulling the embedded structured data (JSON-LD) out of it,
  which had clean `headline` / `url` / `image` / `datePublished` fields for each
  article. The other ~46 articles only had their real URLs (extracted from the
  hyperlinks embedded in a PDF writing sample) but no image, so those use gradient
  placeholder thumbnails instead of a fabricated image. If I want real images for
  the rest: scroll the FMT author page further to lazy-load more articles, save
  the page again, and pull the same structured data out of the new batch.

## What's still unfinished

Being honest with future-me about what's placeholder vs. real:

- **`#experience`** — logos are in (`assets/logos/`), but double check each entry's
  title, subtitle, and tags are accurate and current.
- **`#projects`** — needs real projects, not the placeholder card.
- **"A little more about me" card** — still empty, marked for later.
- **Footer links** — GitHub and LinkedIn both point to `#`.
- **~46 article cards** — real links, but gradient placeholder thumbnails instead
  of real images (see above for how to fix this).

## Deploying

No build step — just push `index.html` and `assets/` and point a static host at
the repo root:

- **GitHub Pages**: Settings → Pages → deploy from `main`, root folder.
- **Netlify Drop**: drag the folder onto [app.netlify.com/drop](https://app.netlify.com/drop)
  for an instant preview URL.

