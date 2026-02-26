# Image Gallery — Build Plan

A responsive image gallery with directional navigation and a lightbox, built in small reviewable steps.

---

## Step 1 — Static HTML skeleton ✅
Created `index.html` with a `.gallery` div containing 10 `<img>` tags using Picsum placeholder images (`seed/N/600/400` for consistent, repeatable photos).

## Step 2 — Basic grid layout ✅
Added `styles.css` with a responsive CSS grid (`auto-fill`, `minmax(260px, 1fr)`), dark purple background (`#2e1a47`), light purple buttons (`#c9a7eb`), and `aspect-ratio: 3/2` + `object-fit: cover` for uniform thumbnails. Lightbox HTML scaffold added but hidden. CSS custom properties (`--bg`, `--btn`, `--lightbox-bg`, `--radius`) established as the shared color system.

## Step 3 — Gallery item hover + selected state ✅
Gallery images wrapped in `<button class="gallery-item">` elements. `:hover img` lifts to `scale(1.04)` with a drop shadow. `.selected img` scales to `scale(1.08)` with a light purple `outline` ring. JS toggles `.selected` on click. GitHub Pages enabled for live preview.

## Step 4 — Lightbox HTML + CSS ✅
Lightbox card restructured: `✕` close button positioned absolute top-right, expanded image centered, Prev/Next buttons in a row below. Fade-in animation (`opacity 0→1`, `scale 0.97→1`) on `.lightbox.active`. `.active` class hardcoded temporarily for visual review, removed in Step 5.

## Step 5 — Open/close lightbox ✅
JS opens the lightbox on gallery image click (sets `.active`, updates `lightboxImg.src`). Closes on `✕` button click or backdrop click (`e.target === lightbox` guard). All buttons given `type="button"` to prevent default submit behavior across browsers.

## Step 6 — Directional navigation + dot indicators ✅
Index-based navigation with `currentIndex` and wraparound arithmetic (`% imgs.length`). Navigation dots generated dynamically (one `<button class="dot">` per image), active dot syncs with current image and is also directly clickable. Fixed a `type="button"` missing attribute bug that was preventing nav buttons from firing.

## Step 7 — Keyboard accessibility ✅
Gallery items (`<button>` wrappers) open the lightbox on `Enter`/`Space` natively. `document` keydown listener handles `ArrowLeft`, `ArrowRight` (with `e.preventDefault()` to stop page scroll), and `Escape`. Focus management: `requestAnimationFrame(() => btnClose.focus())` moves focus into the lightbox on open; `galleryBtns[currentIndex].focus()` returns it on close. `enterGuard` flag prevents the opening `Enter` keypress from immediately re-triggering `btnClose`. Yellow `:focus-visible` outline (`#f5e100`) applied to all buttons and gallery items — keyboard-only, invisible to mouse users. First gallery image pre-selected on load as a keyboard starting point.

## Step 8 — Polish and responsive tweaks ✅
- **Crossfade**: navigating fades the lightbox image out (150ms), swaps `src`, fades back in via CSS `opacity` transition. `navTimeout` debounce prevents stacked calls on rapid key presses.
- **Responsive layout**: tablet breakpoint (`≤768px`) tightens column minimum; mobile breakpoint (`≤520px`) forces a 2-column grid, compacts lightbox padding, shrinks buttons and dots.
- **`scroll-margin-top`** on `.gallery-item` gives breathing room when focus scrolls a thumbnail into view after closing the lightbox.
- **`prefers-reduced-motion`** disables all CSS transitions and animations for users with that system preference.
- **`width: 100%`** on `.gallery-item` ensures grid cells fill correctly across all browsers.
