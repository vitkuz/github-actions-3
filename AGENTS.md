# AGENTS.md

Guidance for the AI agent (Pi, running on DeepSeek `deepseek-v4-pro`) in GitHub Actions.

## What this repo is

A **Vite + React 19 + TypeScript** single-page app (scaffolded with the Vite
`react-ts` template). UI code lives in `src/` — `src/main.tsx` is the entry,
`src/App.tsx` is the root component, styles in `src/App.css` / `src/index.css`,
static assets in `public/` and `src/assets/`. ESLint is configured in
`eslint.config.js`.

Features arrive via pull requests you (the AI agent) open, triggered by a GitHub
Issue/comment (`/pi ...`) or the manual dispatch workflow.

## Coding rules

- Match the existing React + TypeScript style already in `src/`.
- Function components with hooks (no class components). Explicit types for props
  and non-trivial values; keep components small and focused.
- Put new components in their own files under `src/` (e.g. `src/components/`),
  with co-located CSS or CSS modules; wire them into `App.tsx`.
- Keep changes minimal and scoped to the task. Don't reformat unrelated files.

## How to implement a task

1. Make the change by editing/adding files under `src/`.
2. Wire new components into `src/App.tsx` (or the relevant parent).
3. If you add a runtime dependency, add it to `package.json` and run `npm install`.
4. Run `npm run build` (`tsc -b && vite build`) and make sure it succeeds before finishing.

## Pull request rules

- **Never push to `main`.** The workflow branches, commits, and opens the PR.
- Keep the change scoped to the task; use a clear PR title and short description.
