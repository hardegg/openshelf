# OpenShelf — AI Assistant Context

## What is this project?
OpenShelf is an open-source, browser-based 3D bookshelf designer. Users configure dimensions, rows, columns, and board positions to design custom bookshelves, then export specs for a carpenter.

## Tech Stack
- Vanilla JavaScript (no framework, no build step)
- Three.js r128 for 3D rendering (loaded via CDN)
- Pure CSS for UI layout
- Single-page app: `src/index.html` loads all JS modules

## Architecture
All code is in `src/js/` as IIFE modules (no ES modules):
- `config.js` — data model, templates, compute()
- `builder.js` — generates Three.js 3D meshes from config
- `renderer.js` — Three.js scene, camera, lights, render loop
- `labels.js` — dimension label sprites
- `panel.js` — left sidebar parameter UI
- `interaction.js` — board dragging via raycasting
- `history.js` — undo/redo stack
- `export.js` — PNG/JSON export
- `app.js` — main entry, wires everything together

## Key Concepts
- **Config**: a plain JS object describing the shelf (width, height, rows, columns, board thickness, merges, etc.)
- **dividerXs**: per-row array of vertical board X positions (null = computed from global layout)
- **Stagger**: alternating shelf rows offset board positions by half a column width
- **Merges**: regions where cells are combined (can be type "door" for cabinet doors)

## Development
```bash
open src/index.html  # No build step needed
```

## Conventions
- ES5-compatible JavaScript
- IIFE module pattern (var Module = (function() { ... })())
- Coordinates in millimeters internally, scaled by 0.001 for Three.js scene
