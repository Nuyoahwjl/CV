# AGENTS.md

Operational guide for agentic coding tools in this repository.
Use this file as default policy unless a higher-priority rule file appears.

## 1) Repository Overview

- Type: static single-page resume site.
- Primary editable file: `index.html`.
- Primary local asset: `avatar.jpg`.
- No build system, package manager, or test runner is configured.
- No CI workflow files were found at analysis time.

## 2) Rule File Integration (Cursor/Copilot)

At analysis time, none of the following were present:

- `.cursor/rules/`
- `.cursorrules`
- `.github/copilot-instructions.md`

If any are added later, treat them as higher-priority instructions and update this file.

## 3) Source Of Truth

- `index.html` is the source of truth for markup, styles, and content.
- Keep structure/style edits localized to relevant sections.
- Preserve current visual direction (fixed sidebar, readable content column, serif/sans pairing, warm accents).

## 4) Setup And Preview

Preferred local preview command:

```bash
python -m http.server 8000
```

Open `http://localhost:8000`.

Alternative if Python is unavailable:

```bash
npx serve .
```

## 5) Build Commands

- Build command: none (N/A).
- Production artifact: checked-in static files.
- Do not add bundlers/toolchains unless explicitly requested.

## 6) Lint / Format Commands

No in-repo linter/formatter config exists.

Optional ad-hoc checks:

```bash
npx prettier --check index.html
```

Optional ad-hoc auto-format:

```bash
npx prettier --write index.html
```

If formatting is run, verify semantic HTML and intended content are unchanged.

## 7) Test Commands (Including Single Test)

No automated tests are configured.

- Full test command: none (N/A).
- Single test command: none (N/A).

Important: if an agent asks for single-test execution, explicitly report that no runnable unit/integration test target exists in this repo.

## 8) Manual Validation Checklist (Test Substitute)

Use after non-trivial edits:

1. Start local server.
2. Verify page renders without layout breakage.
3. Confirm anchors `#about`, `#education`, `#skills`, `#projects`, `#honors` scroll correctly.
4. Confirm `avatar.jpg` loads and `alt` text remains meaningful.
5. Check responsive behavior around the `1080px` breakpoint.
6. Ensure external icon/image failures do not collapse layout.

## 9) Scope And Change Discipline

- Prefer minimal diffs; avoid broad rewrites.
- Keep content and style changes coherent in the same change.
- Do not rename files or IDs unless explicitly requested.
- Keep commented-out sections unless asked to remove them.

## 10) HTML Guidelines

- Preserve semantic tags already used (`main`, `section`, `article`, `aside`, `nav`).
- Preserve heading hierarchy (`h1` once, then `h2`, then `h3`).
- Keep attributes double-quoted.
- Keep IDs stable because nav links depend on them.
- Keep markup readable; avoid unnecessary wrapper nesting.
- Add comments only when intent is non-obvious.

## 11) CSS Guidelines

- Reuse `:root` custom properties before adding new values.
- Prefer responsive units (`rem`, `%`, `clamp`) over hard-coded `px` where practical.
- Preserve existing motion style (`riseIn`) and keep animation subtle.
- Maintain visible and accessible hover/focus states.
- Avoid utility-style class sprawl.
- Keep media-query behavior aligned with current mobile adaptations.

## 12) JavaScript, Types, Imports, Naming

- Current state: no JavaScript/TypeScript files.
- Do not introduce JS/TS unless explicitly requested.
- If JS is added, keep it progressive and avoid global pollution.
- If TS is added, include explicit config (`tsconfig.json`) in the same change.
- External dependencies are currently CDN-based (Google Fonts and icon URLs).
- Prefer no new dependencies for simple content/style updates.
- CSS class names should be kebab-case (example: `skill-icon-cell`).
- IDs should be short, semantic, and stable (example: `projects`, `honors`).

## 13) Formatting, Error Handling, Accessibility, Performance

- Match existing indentation/style in `index.html`.
- Preserve ASCII unless there is a clear reason to add Unicode.
- Graceful degradation required: missing external icons/fonts must not break layout.
- Keep links valid and explicit (`target`/`rel` where needed).
- Preserve meaningful `alt` text and keyboard-visible focus states.
- Maintain readable contrast and avoid hover-only critical information.
- Keep page lightweight; avoid large new assets and heavy runtime code.
- Use `loading="lazy"` for non-critical images when applicable.

## 14) Git / PR Guidance

- Keep commits focused and explain why changes were made.
- Avoid unrelated refactors in the same change.
- In PR descriptions, include what changed, why, and local validation performed.

## 15) Agent Workflow

Before editing:

1. Read relevant `index.html` sections.
2. Check whether targeted IDs/classes are referenced by nav/styles.

After editing:

1. Run manual validation checklist.
2. Review diff for minimality and unintended edits.
3. Note limitations (for example, no automated tests available).

## 16) Non-Goals

- Do not migrate this site to a framework by default.
- Do not add package management/tooling without explicit request.
- Do not perform whole-file reformat-only changes unless requested.
