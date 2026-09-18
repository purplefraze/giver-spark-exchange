# Package the Giver project for an external review

## Goal
Deliver one downloadable ZIP containing an EXACT snapshot of the current Giver build — nothing modified, simplified or cleaned up — so it can be uploaded to ChatGPT for a full front-to-back review.

## What goes in the ZIP (full project, verbatim)
- All application source: `src/` — components, routes/pages, navigation, state stores, styling/design system (`styles.css`), data/business logic, server code, validation
- All project assets: `src/assets/` (photos and image pointers), `public/` (favicon, robots.txt)
- All configuration: `package.json`, `bun.lock`, `tsconfig.json`, `vite.config.ts`, `capacitor.config.ts`, `components.json`, `eslint.config.js`, `.prettierrc`, `.prettierignore`, `bunfig.toml`, `.gitignore`
- All docs and internal notes: `README.md`, `AGENTS.md`, `src/routes/README.md`
- Project history artifacts: the entire `.lovable/` folder (plans, snapshots, settings) since it documents design decisions
- `ws.png` and any other files at the project root

## What stays out (the only exclusions)
- `node_modules/` — installed third-party packages; already declared in `package.json`/`bun.lock`, and they'd make the ZIP enormous
- Secrets and credentials — environment variable values are checked before packaging; only safe configuration ships
- Git internals (`.git/`) — not needed to understand the build

## Steps
1. Stage a full copy of the project (everything except the exclusions above) in a temp folder, preserving file contents byte-for-byte.
2. Create `giver-source.zip` in temp and list every entry, including hidden files, to verify the snapshot is complete and contains no secrets.
3. Copy the verified ZIP to Files as `giver-source.zip` and present it for download.
