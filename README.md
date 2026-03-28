# OpenShelf

**Design your bookshelf in 3D. Export to your carpenter.**

> This project is built AI-natively with [Claude Code](https://claude.ai/claude-code). The entire codebase — architecture, implementation, debugging — is developed through human-AI collaboration. See [CLAUDE.md](CLAUDE.md) and [AGENTS.md](AGENTS.md) for how it works.

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
git clone https://github.com/hardegg/openshelf.git
cd openshelf
open src/index.html
```

No build step. No dependencies. Just open in a browser.

## Tech Stack

- Vanilla JavaScript (no framework)
- [Three.js](https://threejs.org/) for 3D rendering
- Pure CSS layout
- Static files — deploy anywhere

## AI-Native Development

This project uses **Claude Code as the primary development tool**, not a supplement. The workflow:

1. **CLAUDE.md** is the project's brain — it tells the AI everything about the architecture, conventions, and key concepts. Every session starts by reading it.
2. **AGENTS.md** defines agent roles for different tasks (feature dev, bug fix, code review).
3. **Human provides intent**, AI writes code, human reviews and steers.
4. All code is structured to be AI-friendly: small focused files, clear naming, explicit interfaces between modules.

### Develop with Claude Code

```bash
cd openshelf
claude   # starts a session, reads CLAUDE.md automatically
```

Then describe what you want to build. Claude Code has full context of the project via CLAUDE.md.

## Self-Hosting

Drop the `src/` folder on any static hosting (Vercel, Netlify, GitHub Pages, S3, etc.).

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md). AI-native contributions via Claude Code are welcome.

## License

[AGPL-3.0](LICENSE) — free to use, modify, and self-host. If you run a modified version as a public service, you must release your changes under the same license.
