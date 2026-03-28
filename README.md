# OpenShelf

**Design your bookshelf in 3D. Export to your carpenter.**

OpenShelf is a free, open-source bookshelf designer that lets you visually create custom bookshelf layouts with real-time 3D preview, dimension labels, and exportable specs.

## Features

- **Visual Designer** — drag boards to adjust cell widths and heights
- **3D Preview** — switch between front view and 3D view, click to open doors
- **Templates** — start from presets (classic 5-column, simple 3-column, low cabinet, etc.)
- **Full Customization** — rows, columns, board thickness, depth, drawer/shelf/door types
- **Dimension Labels** — auto-generated measurements for every cell
- **Export** — download PNG screenshot or JSON config to share with your carpenter
- **Undo/Redo** — Ctrl+Z / Ctrl+Shift+Z

## Getting Started

```bash
git clone https://github.com/user/openshelf.git
cd openshelf
open src/index.html
```

No build step. No dependencies. Just open in a browser.

## Tech Stack

- Vanilla JavaScript (no framework)
- [Three.js](https://threejs.org/) for 3D rendering
- Pure CSS layout
- Static files — deploy anywhere

## Self-Hosting

Drop the `src/` folder on any static hosting (Vercel, Netlify, GitHub Pages, S3, etc.).

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

## License

[AGPL-3.0](LICENSE) — free to use, modify, and self-host. If you run a modified version as a public service, you must release your changes under the same license.
