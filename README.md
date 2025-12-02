# A-Frame 360° Image Gallery (Vite Demo)

This project is a small Vite + TypeScript wrapper around the official **A-Frame 360° Image Gallery** demo.

The core scene markup and behavior come from the A-Frame example:

- Original example source: <https://github.com/aframevr/aframe/blob/master/examples/docs/360-gallery/index.html>
- Official guide: <https://aframe.io/docs/1.7.0/guides/building-a-360-image-gallery.html>

The page loads A-Frame and several community components from CDNs and renders a 360° sky with clickable thumbnail links that switch between different panoramic images.

## Features

- 360° photos displayed as an `a-sky` background
- Thumbnail image links arranged with `aframe-layout-component`
- Image switching using `aframe-template-component` and `aframe-event-set-component`
- Click sound feedback when selecting an image
- Camera with `look-controls` and interactive cursor (`a-cursor` + `raycaster`)

## Tech Stack

- [Vite](https://vitejs.dev/) + TypeScript (for dev tooling and bundling)
- [A-Frame](https://aframe.io/) 1.5.x (loaded via CDN in `index.html`)
- A-Frame community components:
  - `aframe-template-component`
  - `aframe-layout-component`
  - `aframe-event-set-component`
  - `aframe-proxy-event-component`

## Project Structure

- `index.html`
  - Loads A-Frame and the components from CDNs
  - Defines the 360° scene (`<a-scene>`, `<a-assets>`, `<a-sky>`, image links, camera + cursor)
- `src/main.ts`
  - Imports global styles only (no UI logic; rendering is controlled by `index.html`)
- `src/style.css`
  - Ensures the `<a-scene>` fills the viewport and the background is black

## Running the Demo

1. Install dependencies:

   ```bash
   npm install
   ```

2. Start the Vite dev server:

   ```bash
   npm run dev
   ```

3. Open the URL printed by Vite (typically <http://localhost:5173/>) in a modern browser.

4. You should see a full-window 360° environment with three image thumbnails in front of you.

   - Move your mouse or headset to look around.
   - Use the central cursor to hover over a thumbnail and click to switch the 360° image.

## Production Build

To create an optimized build:

```bash
npm run build
```

Then preview it locally:

```bash
npm run preview
```

## Credits

- Original 360° gallery demo and assets by the **A-Frame** team.
- See the official guide for more detail and customization ideas:
  <https://aframe.io/docs/1.7.0/guides/building-a-360-image-gallery.html>
