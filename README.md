# Chapter 8 Software Testing

An animated, 3D 16-slide presentation website for Chapter 8 Software Testing: development testing, test-driven development, release testing and user testing.

Western University · Course: SDLC · Instructor: Roeun Mesa · Team: OEUN RASMEI, KHOUN KHEYDET

**Live version:** https://claude.ai/artifact/EFL1rYhXDqmtBo1go85wBu (private until you share it from its Share menu)

Everything is in one file, `index.html`. The 3D background uses Three.js and the fonts come from Google Fonts, so the page needs an internet connection the first time it loads.

## Presenting

| Key | Action |
|---|---|
| `→` `Space` `PageDown` | Next slide (works with most presentation clickers) |
| `←` `PageUp` | Previous slide |
| `N` | Speaker notes panel |
| `O` | Overview of all slides (click one to jump) |
| `F` | Fullscreen |
| `Home` / `End` | First / last slide |

On a phone or a narrow window, the deck becomes a scrolling page. Swipe left or right in slide mode on a tablet. Add `#12` to the URL to open slide 12 directly.

Interactive slides: the clickable table of contents (slide 2), the TDD cycle demo (slide 9), the scenario test log (slide 12) and the load-test simulator (slide 13).

A PDF of every slide is in `Chapter-8-Software-Testing-Slides.pdf`.

## Publishing with GitHub Pages

1. On GitHub, open **Settings → Pages**.
2. Under **Build and deployment**, choose **Deploy from a branch**.
3. Pick this branch and the `/ (root)` folder, then save.

After a minute the site is live at `https://<your-username>.github.io/sdlc-chapter-8-software-testing/`.

You can also just double-click `index.html` to open it in a browser.

## Files

- `index.html`: the slideshow (styles, slides, speaker notes and scripts)
- `assets/`: AI-generated slide images (made with Higgsfield, 2000×1131), also embedded in `index.html`
- `Chapter-8-Software-Testing-Slides.pdf`: all slides as a PDF at 2560×1440
- `RESEARCH.md`: study notes for the chapter, the extra research added to the deck, and sources

## Editing

Each slide is a `<section class="slide">` in `index.html`. Speaker notes live in the `<aside class="notes">` inside each slide. The `data-shape` attribute picks the 3D particle shape behind the slide (for example `globe`, `torus`, `wave`, `check`).
