# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

A single-page portfolio website for a UI/UX designer (하연정). No build tools, frameworks, or package managers — everything is vanilla HTML/CSS/JavaScript in one file.

## Running Locally

Open `index.html` directly in a browser, or serve it with any static file server:

```bash
python3 -m http.server 8080
# then open http://localhost:8080
```

There is no build step, no `npm install`, and no transpilation required.

## Architecture

Everything lives in `index.html` as a single self-contained file:

- **CSS** (lines ~11–1130): All styles are inline in a `<style>` block. CSS custom properties (`:root`) define the color palette and reused values.
- **HTML** (lines ~1132–1498): Five main sections — `#hero`, `#about`, `#skills`, `#life`, `#dreams` — plus a `.quote-wrap` and `<footer>`.
- **JavaScript** (lines ~1500–1705): All scripts are inline in a `<script>` block at the bottom.

The `mypage/` subdirectory is a separate nested git repository containing what appears to be an earlier iteration of the same page.

## Color System

All colors are CSS variables defined in `:root`:

| Variable | Value | Usage |
|---|---|---|
| `--dark-1` | `#04071A` | Page background |
| `--dark-2` | `#080D28` | Section backgrounds |
| `--dark-3` | `#0C1235` | Deeper section backgrounds |
| `--teal` | `#38EFD0` | Primary accent, gradients |
| `--sky` | `#64CFFF` | Secondary accent |
| `--coral` | `#FF6B9D` | Highlight accent |
| `--gold` | `#FFD166` | Tertiary accent |

## JavaScript Modules (inline)

| Feature | Description |
|---|---|
| Nav scroll | Adds `.scrolled` class to `<nav>` and highlights active link using section offsets |
| Canvas ripples | `<canvas id="heroCanvas">` draws animated water ripple rings; spawns automatically every 700 ms and on click/touch |
| 3D card tilt | Mouse-tracking `rotateX`/`rotateY` on `#h3dScene` using lerped animation loop |
| Parallax blobs | `.blob` elements translate on scroll at different speeds |
| Typing effect | Cycles through `phrases[]` with character-by-character type/delete loop |
| Scroll reveal | `IntersectionObserver` adds `.on` class to elements with `.r`, `.rl`, `.rr` to trigger CSS transitions |
| Dream progress bars | Second `IntersectionObserver` reads `data-width` attribute and sets `bar.style.width` when card enters viewport |

## Responsive Breakpoints

- `≤1100px`: Narrower hero grid, smaller 3D card
- `≤900px`: Single-column hero grid, centered layout, reduced padding
- `≤600px`: Floating badge chips hidden, smaller 3D card
- `≤500px`: Compressed nav links and hero tags

## Fonts

Loaded from Google Fonts:
- **Outfit** (weights 300–900): headings, labels, UI elements
- **Nunito** (regular/italic, weights 300–700): body text
