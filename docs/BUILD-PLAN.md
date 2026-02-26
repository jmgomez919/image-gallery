# Image Gallery — Build Plan

A responsive image gallery with directional navigation and a lightbox, built in small reviewable steps.

---

## Step 1 — Static HTML skeleton ✅
Create `index.html` with a `<div class="gallery">` containing 8–10 hardcoded `<img>` tags.
No CSS yet. Verify images render in a browser.

## Step 2 — Basic grid layout
Add CSS to make the gallery a responsive grid (`display: grid`, `repeat(auto-fill, minmax(...))`, `gap`).
Resize the browser window to confirm it reflows. Nothing interactive yet.

## Step 3 — Gallery item hover effect
Add a subtle scale or overlay on hover (`:hover` CSS). Purely cosmetic.
Verify it looks good before adding complexity.

## Step 4 — Lightbox HTML + CSS (no JS)
Add a hidden `<div class="lightbox">` with a large `<img>`, close button, and prev/next arrows to the HTML.
Style it with `position: fixed`, overlay backdrop, and centered image. Use `display: none` / `display: flex` toggled by a class.
Manually add the `.active` class in HTML to test the appearance.

## Step 5 — Open/close lightbox
Write JS to open the lightbox on gallery image click (set `.active`, update the `<img src>`), and close on the X button or backdrop click.
Test: click image → lightbox opens; click X → closes.

## Step 6 — Directional navigation
Write JS for prev/next buttons using an index variable to track the current image.
Clicking arrows updates the lightbox image.
Test: open any image, step forward and backward through all images.

## Step 7 — Edge cases + keyboard support
Add wraparound (last → first), disable arrow keys when lightbox is closed, and support `ArrowLeft` / `ArrowRight` / `Escape` keys.
Test each edge case explicitly.

## Step 8 — Polish and responsive tweaks
Adjust lightbox image sizing for small screens, add a fade/transition animation, and check on mobile viewport size.
