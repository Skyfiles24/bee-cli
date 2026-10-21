# AGENTS

Project notes for agents working in this repo.

- Runtime/build: Bun.
- Language: TypeScript with strict settings.
- Sources live in `/sources`; entry point is `sources/main.ts`.
- Subcommands live in `/sources/commands/<name>`.
- Shared helpers live in `/sources/utils`.
- Path alias: `@/` maps to `/sources`.
- Build: `bun run build` -> `dist/bee` (binary name `bee`).
- Package name: `bee-cli`.
- Typecheck: `bun run typecheck`.
- Commit after each successful step using Angular-style (conventional) commit messages.
- Before any commit: run `bun install`, `bun run typecheck`, and `bun run build`.

## Cursor Cloud specific instructions

- Bun 1.3.8 matches `.github/workflows/release.yml`. The environment install puts `bun` on `PATH`.
- Run `bun test` for the suite. `sources/lib/lib.e2e.test.ts` stays skipped unless `BEE_CLI_E2E=1`, and that case needs an existing `bee login` session.
- There is no database or dev server. Check the CLI with `bun ./sources/main.ts version --json`, or `./dist/bee version --json` and `./dist/bee status` after `bun run build`.
- `bee mcp serve` speaks JSON-RPC on stdin. Live Bee API commands need a logged-in session; unit tests do not.
