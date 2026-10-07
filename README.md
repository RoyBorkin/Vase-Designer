# 3D Vase Designer

Sketch the outline of a vase and watch it become a 3D model in real time. When you like what you see, download it as an `.stl` file ready for 3D printing or further editing in Blender, Fusion 360, or any slicer.

**Live demo:** https://royborkin.github.io/vase-designer/

## How it works

The app uses a classic *lathe* technique. You draw one side of the vase's silhouette (its profile) on a 2D canvas, and the app spins that line 360° around a vertical axis to produce a solid of revolution — the same way a potter's wheel or a woodworking lathe shapes an object.

1. **Draw** — on the left pane, draw the **right half** of the vase in one continuous stroke, starting near the red dashed center axis.
2. **Preview** — release the mouse (or lift your finger) and the 3D model appears on the right, slowly auto-rotating. Drag to orbit, scroll to zoom.
3. **Style** — switch between Clay, Glass, Metal and Wireframe materials.
4. **Export** — click **Download 3D (.stl)** to save `my_vase.stl`.

Each new stroke replaces the previous profile. Use **Clear** to start over.

## Features

- Freehand profile drawing with mouse or touch
- Live 3D preview built with Three.js `LatheGeometry`
- Orbit controls with auto-rotate
- Four preview materials: clay, glass, metal, wireframe
- One-click STL export
- Responsive layout — panes stack vertically on narrow screens
- Single HTML file, no build step, no install

## Running locally

There's nothing to install. Either:

- Open `index.html` directly in a modern browser, **or**
- Serve the folder locally:

  ```bash
  npx serve .
  # or
  python3 -m http.server 8000
  ```

  then visit `http://localhost:8000`.

An internet connection is required, since the libraries load from CDNs.

## Deploying to GitHub Pages

1. Push this repository to GitHub as `vase-designer`.
2. Go to **Settings → Pages**.
3. Under **Source**, choose **Deploy from a branch**, select `main` and `/ (root)`, then save.
4. After a minute the app is live at `https://<your-username>.github.io/vase-designer/`.

## Tech stack

| Library | Purpose |
| --- | --- |
| [Three.js r128](https://threejs.org/) | 3D rendering, `LatheGeometry`, materials |
| OrbitControls | Camera orbit / zoom |
| STLExporter | Exporting the mesh as STL |
| [Tailwind CSS](https://tailwindcss.com/) (Play CDN) | UI styling |
| [Font Awesome 6](https://fontawesome.com/) | Icons |

## Project structure

```
vase-designer/
├── index.html   # The entire app: markup, styles and script
├── LICENSE      # MIT License
├── README.md
└── .gitignore
```

## Tips for printable vases

- Close the bottom: end your stroke back at the center axis so the vase has a floor.
- Exported STL units correspond to the preview scale (1 canvas pixel ≈ 0.2 units). Scale the model to your target size in your slicer.
- The model is a single surface with no wall thickness. Print it in **vase mode / spiralize outer contour**, or add thickness in a 3D editor (e.g. Blender's *Solidify* modifier).

## Roadmap ideas

- Real multi-step undo
- Wall-thickness control for direct printing
- Profile smoothing (spline fitting)
- Save/load profiles as JSON
- Custom export filename and real-world size in mm

## License

Copyright © 2026 Roy Borkin.

Released under the [MIT License](LICENSE). You're free to use, modify and distribute this project, provided the copyright notice and license text are kept.

## Author

**Roy Borkin** — [royborkin.github.io](https://royborkin.github.io/) · [GitHub](https://github.com/royborkin)
