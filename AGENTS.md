# AGENTS.md — layer-charly-infrastructure (retired)

This repo is **retired**: it authors nothing and must not be edited except to
record a further move. It was the `charly-infrastructure` concept candy — a `true`-no-op
`plan:` plus 2 `skill:` routing nodes with their prose in `.agents/skills/`.
Under `AGENTS.md` Part II #5 a skill lives in the repo whose code, plugin or
config it describes, and none of them lived here, so every skill moved
byte-identically to the repo that holds the entity it documents:

- `tmux-layer` → `opencharly/layer-tmux`;
- `dbus-layer` → `opencharly/pod-dbus`.

The `/charly-infrastructure:<skill>` addresses are unchanged: family `infrastructure` is carried by the
destination nodes, so the dispatcher rows did not move meaning.

Canonical files:

- `charly.yml` — the drained `charly-infrastructure:` candy entity: a `true` no-op `plan:`
  plus a `true` no-op `check:` (it asserts nothing; it is a placeholder step). It
  exists only so this repo validated as a project before retirement.
- `README.md` — user overview only; never agent guidance; it is the destination map.
- `.github/workflows/tag-on-merge.yml` — CalVer tag + `CHANGELOG/` on merge.

## Modify this repo

- Don't. There is no skill, node or prose here to update. A change to a
  `infrastructure`-family skill is a change at its destination repo, in the same pull
  request as the entity it documents.

## Landing

- PR-only. Every change lands through a pull request; the org-required
  `charly/pr-validator` validates the diff and body and arms native auto-merge on
  PASS. Direct pushes to `main` are blocked.
- History lives in `CHANGELOG/` (written by `tag-on-merge` at merge time); the PR
  body IS the changelog.
- The authoritative rulebook is the umbrella `AGENTS.md` in
  `opencharly/opencharly` and `charly/AGENTS.md` in the charly repo. Do not
  restate its rules here.
