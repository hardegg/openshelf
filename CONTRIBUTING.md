# Contributing to OpenShelf

Thank you for your interest in contributing!

## Development Setup

1. Fork and clone the repo
2. Open `src/index.html` in your browser — no build step needed
3. Edit files in `src/js/` and refresh to see changes

## Contributing with Claude Code (Recommended)

This project is built AI-natively. The fastest way to contribute:

```bash
cd openshelf
claude                    # Reads CLAUDE.md automatically for full context
```

Then describe the feature or fix you want to implement. Claude Code understands the full architecture from CLAUDE.md and follows the conventions in AGENTS.md.

## How to Contribute

- **Bug reports** — open an issue with steps to reproduce
- **Feature requests** — open an issue describing the use case
- **Pull requests** — fork, create a branch, make changes, submit PR

## Code Style

- Vanilla JavaScript (ES5 compatible)
- IIFE module pattern
- No external dependencies beyond Three.js (loaded via CDN)
- Keep functions small and well-named
- Comments only where logic is non-obvious
- Keep files under 400 lines

## Pull Request Process

1. Create a feature branch from `main`
2. Make your changes
3. Test in browser (front view + 3D view)
4. Submit PR with a clear description of what changed and why

## Reporting Security Issues

See [SECURITY.md](SECURITY.md).
