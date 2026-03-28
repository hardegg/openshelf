# AI Agent Roles for OpenShelf

> This file defines how AI agents (Claude Code, Codex, etc.) should approach different tasks in this repo.

## Feature Development

**Context**: Read CLAUDE.md first for full architecture overview.

**Process**:
1. Understand the feature request — ask clarifying questions if ambiguous
2. Read existing related code (use Grep/Glob to find relevant modules)
3. Plan the implementation — identify which files to modify, what new code to write
4. Implement incrementally — small changes, verify each step
5. Test in browser (front view + 3D view + export)

**Conventions**:
- Vanilla JS, IIFE module pattern
- Coordinates in millimeters, scaled by 0.001 for Three.js
- Keep files under 400 lines — split if larger
- No external dependencies beyond Three.js

## Bug Fix

**Process**:
1. Reproduce the issue — understand the expected vs actual behavior
2. Trace the code path from user action to rendering
3. Identify root cause before writing any fix
4. Fix with minimal changes — don't refactor unrelated code
5. Verify the fix doesn't break other features

## Code Review

**Focus areas**:
- Does the change match user intent?
- Are coordinates and dimensions in correct units (mm)?
- Does it handle edge cases (0 columns, 1 row, empty merges)?
- Performance: avoid creating objects in render loops
- No hardcoded values that should come from config

## Documentation

- README.md: user-facing, marketing tone
- CLAUDE.md: AI-facing, technical and precise
- CONTRIBUTING.md: contributor-facing, practical
- Code comments: only where logic is non-obvious
