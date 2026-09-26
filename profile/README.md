<h1 align="center">whaleshell</h1>

<p align="center">
  <strong>Agent sandboxes in Go</strong><br>
  Policy-bound containers for Cursor, Claude, Codex — and anything you bring.
</p>

<p align="center">
  <a href="https://whaleshell.github.io/whaleshell-docs/"><img src="https://img.shields.io/badge/docs-whaleshell.github.io-3F51B5?logo=materialformkdocs&logoColor=white" alt="Documentation"></a>
  <a href="https://opensource.org/licenses/MIT"><img src="https://img.shields.io/badge/License-MIT-yellow.svg" alt="License"></a>
  <a href="https://github.com/whaleshell/whaleshell-cli"><img src="https://img.shields.io/badge/Go-1.27+-00ADD8?logo=go" alt="Go Version"></a>
  <a href="https://github.com/whaleshell/whaleshell-cli/releases"><img src="https://img.shields.io/badge/status-alpha-critical" alt="alpha"></a>
</p>

---

## Documentation

**[whaleshell.github.io/whaleshell-docs](https://whaleshell.github.io/whaleshell-docs/)** — shared docs for all modules (EN / RU).

| | |
|--|--|
| English | [Home](https://whaleshell.github.io/whaleshell-docs/) · [Get started](https://whaleshell.github.io/whaleshell-docs/get-started/) |
| Русский | [Главная](https://whaleshell.github.io/whaleshell-docs/ru/) · [Быстрый старт](https://whaleshell.github.io/whaleshell-docs/ru/get-started/) |
| Docker | [EN](https://whaleshell.github.io/whaleshell-docs/providers/docker/) · [RU](https://whaleshell.github.io/whaleshell-docs/ru/providers/docker/) |
| Podman | [EN](https://whaleshell.github.io/whaleshell-docs/providers/podman/) · [RU](https://whaleshell.github.io/whaleshell-docs/ru/providers/podman/) |

Source: [whaleshell-docs](https://github.com/whaleshell/whaleshell-docs) (Material for MkDocs).

---

## whaleshell

**whaleshell** runs coding agents inside hardened Docker sandboxes. YAML policy controls filesystem and egress; an egress sidecar enforces it; an optional gateway provides registry, provider compose, and relayed exec.

```bash
curl -fsSL https://raw.githubusercontent.com/whaleshell/whaleshell-cli/main/install.sh | bash
whaleshell sandbox create --name demo --workspace . --policy policies/default.yaml
```

### Repositories

| Repo | Role |
|------|------|
| **[whaleshell-docs](https://github.com/whaleshell/whaleshell-docs)** | Shared docs → [site](https://whaleshell.github.io/whaleshell-docs/) |
| [whaleshell-cli](https://github.com/whaleshell/whaleshell-cli) | `whaleshell` CLI, policies, agent images |
| [whaleshell-core](https://github.com/whaleshell/whaleshell-core) | Policy schema + egress engine |
| [whaleshell-providers](https://github.com/whaleshell/whaleshell-providers) | Provider profiles + compose |
| [whaleshell-proxy](https://github.com/whaleshell/whaleshell-proxy) | Egress sidecar + `policy.local` |
| [whaleshell-driver](https://github.com/whaleshell/whaleshell-driver) | Docker / Podman compute drivers |
| [whaleshell-runtime](https://github.com/whaleshell/whaleshell-runtime) | Sandbox glue, `whaleshell-init`, images |
| [whaleshell-gateway](https://github.com/whaleshell/whaleshell-gateway) | Control-plane HTTP daemon |
| [whaleshell-display](https://github.com/whaleshell/whaleshell-display) | noVNC helpers |
| [whaleshell-sdk](https://github.com/whaleshell/whaleshell-sdk) | Go client |
| [whaleshell-python](https://github.com/whaleshell/whaleshell-python) | Python client |
| [slogx](https://github.com/whaleshell/slogx) | Structured slog helpers |

### Images (GHCR)

```text
ghcr.io/whaleshell/whaleshell/gateway
ghcr.io/whaleshell/whaleshell/sandboxes/{base,gui,gpu,cursor,claude,codex}
```

### Design

- **Multi-repo** — each module is its own git remote (not a monorepo)
- **Shared docs** — one Material for MkDocs site for all modules
- **Default deny** — L4/L7 egress allowlists in `whaleshell-core`
- **OpenShell-shaped** — host-gateway alias `host.whaleshell.internal`, provider attach, BYOC

MIT © whaleshell
