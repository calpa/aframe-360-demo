# 360° Cathedral Image Gallery (A-Frame + Vite)

[![A-Frame](https://img.shields.io/badge/A--Frame-1.5.0-ff4081?logo=aframe&logoColor=white)](https://aframe.io/)
[![Vite](https://img.shields.io/badge/Vite-Bundled-646cff?logo=vite&logoColor=white)](https://vitejs.dev/)
[![TypeScript](https://img.shields.io/badge/TypeScript-Enabled-3178c6?logo=typescript&logoColor=white)](https://www.typescriptlang.org/)
[![Code License](https://img.shields.io/badge/Code%20License-MIT-green)](./LICENSE)
[![Image Licenses](https://img.shields.io/badge/Images-See%20Flickr%20Authors-informational)](https://www.flickr.com/groups/equirectangular/pool/with/54892836686)

This project is a **small 360° photo gallery of cathedrals** that runs in the browser.

When you open the site you stand “inside” a 360° photograph. Three text buttons in front of you let you switch between different cathedral interiors.

![Screenshot of the 360° cathedral gallery demo](public/website.jpg)

## Images used in this gallery

This gallery currently showcases **three cathedral interiors**, each coming from the
Flickr _equirectangular_ pool:

- _Cathédrale Sainte-Croix d'Orléans 360° Panorama_  
  <https://www.flickr.com/photos/lcsalcedo/54861274496/in/pool-equirectangular/>
- _Holy Metropolitan Church of Hypapanti of Thira (interior)_  
  <https://www.flickr.com/photos/hapephotographix/54878222652/in/pool-equirectangular/>
- _Cathedral of Saint John the Baptist (interior)_  
  <https://www.flickr.com/photos/hapephotographix/54892836881/in/pool-equirectangular/>

All three images are equirectangular 360° photos, so they wrap cleanly around the
viewer when mapped onto the A-Frame sky.

## What this project is based on

This gallery was **originally inspired by** the A-Frame 360° Image Gallery example,
but now uses a different layout and its own image set.

- Original demo: <https://github.com/aframevr/aframe/blob/master/examples/docs/360-gallery/index.html>
- Guide: <https://aframe.io/docs/1.7.0/guides/building-a-360-image-gallery.html>

## What’s different from the original demo

- **Custom content**

  - Uses three cathedral panoramas instead of the original example images.
  - Images are sourced from the **Flickr equirectangular pool**, for example:
    - <https://www.flickr.com/groups/equirectangular/pool/with/54892836686>

- **Simplified UI**

  - Three horizontal black bars stacked in **three rows**.
  - Each bar contains the **name of a cathedral**.
  - Clicking a bar changes the 360° background to that cathedral.
  - The currently selected bar is highlighted so you can see which image is active.

- **No thumbnails or cards**
  - The original demo used three card-like images in a row.
  - This project instead uses simple text labels, which are easier to control for long names.

## How it works (high-level)

- The page uses **[A-Frame](https://aframe.io/)**, a web framework for building 3D / VR scenes with HTML-like tags.
- A large sphere (A-Frame’s `a-sky`) shows a 360° photo as its texture, so you feel like you are standing inside the scene.
- Three clickable entities in front of the camera act as **buttons**:
  - When you click one, we:
    - Change the `a-sky` image.
    - Update the visual “active” state of the selected button.

You can think of it as a normal single-page site with three buttons that swap the background panorama.

## Tech stack

- **Vite + TypeScript** – for fast local development and bundling.
- **A-Frame 1.5.x** – loaded via CDN in `index.html`.
- A-Frame community components (also via CDN):
  - `aframe-template-component` – to reuse the HTML for each label.
  - `aframe-event-set-component` – to change properties in response to events.
  - `aframe-proxy-event-component` – to trigger fade animations on the sky.
  - `aframe-layout-component` – still available but the current layout uses manual positioning.

## Project structure

- **`index.html`**
  - Loads A-Frame and components from CDNs.
  - Registers a small `link-active-state` component that highlights the selected label.
  - Defines the 360° scene: assets, sky, three labels, camera, and cursor.
- **`src/main.ts`**
  - Imports global CSS only; there is no React/Vue/etc. The scene is defined directly in HTML.
- **`src/style.css`**
  - Makes the A-Frame canvas fill the whole browser window with a black background.

## Running the gallery locally

1. Install dependencies:

   ```bash
   npm install
   ```

2. Start the dev server:

   ```bash
   npm run dev
   ```

3. Open the URL printed by Vite (usually <http://localhost:5173/>) in a modern browser.

4. Use the mouse to look around and the central cursor to point at one of the three labels. Click to switch between cathedral panoramas.

## Building for production

Create an optimized build:

```bash
npm run build
```

Preview the built site locally:

```bash
npm run preview
```

## Credits & licenses

- 360° gallery example and engine by the **A-Frame** team.
- Project code is released under the **MIT License** (see [`LICENSE`](./LICENSE)).
- Panoramic cathedral images from the **Flickr equirectangular pool**:
  - _Cathédrale Sainte-Croix d'Orléans 360° Panorama_  
    <https://www.flickr.com/photos/lcsalcedo/54861274496/in/pool-equirectangular/>
  - _Holy Metropolitan Church of Hypapanti of Thira (interior)_  
    <https://www.flickr.com/photos/hapephotographix/54878222652/in/pool-equirectangular/>
  - _Cathedral of Saint John the Baptist (interior)_  
    <https://www.flickr.com/photos/hapephotographix/54892836881/in/pool-equirectangular/>

Please make sure to respect the licenses and attribution requirements of the original Flickr photographers if you reuse or publish this project.
