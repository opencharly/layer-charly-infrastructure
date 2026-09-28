# charly-infrastructure

The `charly-infrastructure` family — the infrastructure-service skill.

The `charly-infrastructure` candy is a **concept candy**: it ships no install
content and owns the `infrastructure` family of `skill:` entities whose names
have no namesake candy. It currently carries two entities:

- `dbus-layer` — the D-Bus session bus candy (inter-process communication and
  desktop notifications; backs the `dbus:` check verb).
- `tmux-layer` — the `tmux` terminal-multiplexer candy.

The rest of the `infrastructure` family is owned by sibling `layer-*` and
`pod-*` repos (e.g. `supervisord`, `redis`, `postgresql`, `traefik`, `gocryptfs`,
`gnupg`, `k3s`, `socat`, `sqlite`, `ssh-client`, `tailscale`, `vectorchord`,
`virtualization`, `keepassxc`). `candy/plugin-marketplace` regenerates the
standalone [opencharly/marketplace](https://github.com/opencharly/marketplace)
corpus from these entities, so the skills are authored here and projected there.

## What it provides

| Property | Value |
|---|---|
| Layer / candy | `charly-infrastructure` (concept candy) |
| Install content | none — a `true` no-op `plan:` |
| Owns | 2 `skill:` entities: `dbus-layer`, `tmux-layer` |
| Projected to | `marketplace/infrastructure/skills/` |
| Service / port | none |

## How to use it

This repo is consumed as a **skill source**, not as an image layer. Edit the
`skill:` entities in `charly.yml`; the marketplace regeneration projects them
into `/charly-infrastructure:*` pages. To reference the repo directly, compose
it in a box. A box is a `candy:` node that carries the box's `base:` image and a
nested `candy:` list of layer refs (the nested `candy:` is the composition list;
the outer `candy:` is the box body):

```yaml
my-box:
  candy:                  # the box body (an IMAGE is a `candy:` node carrying `base:`)
    base: fedora          # the box's base image
    candy:                # the box's composition list
      - '@github.com/opencharly/layer-charly-infrastructure:v2026.265.1906'
```

The services themselves are consumed through their own candies — compose
`layer-supervisord` for the process manager, `pod-redis` / `pod-postgresql` for
data services, and so on; the `dbus-layer` / `tmux-layer` skills here document
those two candies.

## Layout

- `charly.yml` — the `charly-infrastructure:` concept candy entity plus two
  `skill:` entities (`dbus-layer`, `tmux-layer`).
- `.github/workflows/tag-on-merge.yml` — CalVer tag + `CHANGELOG/` on merge.
- `README.md` — this user overview.

## Related

- Owning skills: `/charly-infrastructure:dbus-layer`,
  `/charly-infrastructure:tmux-layer`
- Authoring reference: `/charly-image:layer`
- Supervisord: `/charly-infrastructure:supervisord` (in `opencharly/layer-supervisord`)
- [`opencharly/marketplace`](https://github.com/opencharly/marketplace) — the projected corpus
- [`opencharly/charly`](https://github.com/opencharly/charly) — the charly CLI and image builder
- [`opencharly/opencharly`](https://github.com/opencharly/opencharly) — the umbrella
