# Package the Giver source code for an external review

## Goal
Deliver a single ZIP of the full build source (front to back) so it can be uploaded to ChatGPT for review.

## What goes in the ZIP
- All application source: `src/` (components, routes, data, hooks, lib, styles)
- Configuration: `package.json`, `bun.lock`, `tsconfig.json`, `vite.config.ts`, `capacitor.config.ts`, `components.json`, `eslint.config.js`, `.prettierrc`, `.prettierignore`, `bunfig.toml`
- Docs: `README.md`, `AGENTS.md`, `src/routes/README.md`

## What stays out
- `node_modules/` (dependencies — ChatGPT doesn't need them, and they'd make the file huge)
- Build/generated output
- `.git`, `.workspace`, `.lovable` (internal plans/snapshots/memory — not build code)
- `ws.png` and stray screenshots
- Any secrets/credential material (none should exist in source; the ZIP listing is checked before delivery)

## Steps
1. Stage a clean copy of the files above in a temp folder.
2. Create `giver-source.zip` in temp, then list every entry (including hidden files) to verify nothing unwanted or sensitive is inside.
3. Copy the verified ZIP to Files as `giver-source.zip` and present it for download.
