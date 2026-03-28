# AI Agent Roles for OpenShelf

> This file defines how AI agents (Claude Code, Codex, etc.) should approach different tasks in this repo. Together these roles form a closed-loop development process.

## Development Lifecycle

```
Intent → Plan → Implement → QA → Merge → Deploy
  │                            │
  └────── Reject / Rework ─────┘
```

Every code change must pass through the **QA Agent** before merge. No exceptions.

---

## Feature Development Agent

**Context**: Read CLAUDE.md first for full architecture overview.

**Process**:
1. Understand the feature request — ask clarifying questions if ambiguous
2. Read existing related code (use Grep/Glob to find relevant modules)
3. Plan the implementation — identify which files to modify, what new code to write
4. Implement incrementally — small changes, verify each step
5. Hand off to QA Agent before considering the task done

**Conventions**:
- Vanilla JS, IIFE module pattern
- Coordinates in millimeters, scaled by 0.001 for Three.js
- Keep files under 400 lines — split if larger
- No external dependencies beyond Three.js

---

## Bug Fix Agent

**Process**:
1. Reproduce the issue — understand the expected vs actual behavior
2. Trace the code path from user action to rendering
3. Identify root cause before writing any fix
4. Fix with minimal changes — don't refactor unrelated code
5. Hand off to QA Agent — verify fix AND no regressions

---

## QA Agent

> **Gate keeper**. No code merges without QA sign-off.

### 1. Functional Verification (every change)

Run through this checklist in the browser:

**Core rendering**:
- [ ] App loads without console errors
- [ ] Default template renders correctly (front view)
- [ ] 3D view renders correctly, rotation/zoom works
- [ ] Dimension labels are visible and accurate

**Interaction**:
- [ ] Horizontal board drag works (row heights change)
- [ ] Vertical board drag works (cell widths change)
- [ ] Board drag respects constraints (min size, can't cross neighbors)
- [ ] Hover highlight appears on boards
- [ ] Undo/redo works (Ctrl+Z / Ctrl+Shift+Z)

**Panel & config**:
- [ ] Template switching works (all 4 templates)
- [ ] Parameter changes update 3D model in real-time
- [ ] Add/delete row works
- [ ] Row type toggle (shelf/drawer/door) works

**Merge areas**:
- [ ] Door merge renders with clickable double doors
- [ ] Non-door merge renders with correct borders
- [ ] No stray boards or labels inside merge areas

**Export**:
- [ ] PNG export downloads correct image
- [ ] JSON export downloads valid config
- [ ] JSON import restores the design

**Edge cases**:
- [ ] 1 column, 1 row — no crash
- [ ] Max columns (10) — renders correctly
- [ ] Very narrow columns (min size) — no overlap
- [ ] Panel collapse/expand — viewport resizes

### 2. Automated Tests (when test framework is set up)

- Write and maintain e2e tests (Playwright) for critical paths
- Run tests before every merge: `npm test`
- Minimum coverage targets:
  - Config → build → render pipeline: covered
  - All template loads: covered
  - Export/import round-trip: covered

### 3. Code Review

**Focus areas**:
- Does the change match user intent?
- Are coordinates and dimensions in correct units (mm)?
- Does it handle edge cases (0 columns, 1 row, empty merges)?
- Performance: avoid creating objects in render loops
- No hardcoded values that should come from config
- No regressions in existing features

### 4. Performance Check (for rendering/interaction changes)

- Rebuild time < 100ms for default templates
- Drag interaction feels smooth (no visible lag)
- No memory leaks (check: drag 50 times, memory stable)

### QA Verdict

After running all applicable checks, report:

```
## QA Report
- **Change**: [brief description]
- **Functional**: PASS / FAIL (list failures)
- **Tests**: PASS / FAIL / SKIP (if no test framework yet)
- **Code review**: PASS / FAIL (list concerns)
- **Performance**: PASS / FAIL / N/A
- **Verdict**: APPROVED / REJECTED (reason)
```

---

## Documentation Agent

- README.md: user-facing, marketing tone
- CLAUDE.md: AI-facing, technical and precise — update whenever architecture changes
- CONTRIBUTING.md: contributor-facing, practical
- AGENTS.md: keep roles and checklists up to date
- Code comments: only where logic is non-obvious
