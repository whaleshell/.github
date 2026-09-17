<h1 align="center">zorneth</h1>

<p align="center">
  <strong>Agent sandboxes in Go</strong><br>
  Policy-bound containers for Cursor, Claude, Codex — and anything you bring.
</p>

<p align="center">
  <a href="https://opensource.org/licenses/MIT"><img src="https://img.shields.io/badge/License-MIT-yellow.svg" alt="License"></a>
  <a href="https://github.com/zorneth/osg-cli"><img src="https://img.shields.io/badge/Go-1.27+-00ADD8?logo=go" alt="Go Version"></a>
  <a href="https://github.com/zorneth/osg-cli/actions/workflows/ci.yml"><img src="https://github.com/zorneth/osg-cli/actions/workflows/ci.yml/badge.svg" alt="osg-cli CI"></a>
</p>

---

## osg

**osg** runs coding agents inside hardened Docker sandboxes. YAML policy controls filesystem and egress; an egress sidecar enforces it; an optional gateway provides registry, provider compose, and relayed exec.

```bash
go install github.com/zorneth/osg-cli/cmd/osg@latest
osg sandbox create --name demo --workspace . --policy policies/default.yaml
```

### Repositories

| Repo | Role |
|------|------|
| [osg-cli](https://github.com/zorneth/osg-cli) | `osg` CLI, policies, agent images |
| [osg-core](https://github.com/zorneth/osg-core) | Policy schema + egress engine |
| [osg-providers](https://github.com/zorneth/osg-providers) | Provider profiles + compose |
| [osg-proxy](https://github.com/zorneth/osg-proxy) | Egress sidecar + `policy.local` |
| [osg-driver](https://github.com/zorneth/osg-driver) | Docker compute driver |
| [osg-runtime](https://github.com/zorneth/osg-runtime) | Sandbox glue, `osg-init`, images |
| [osg-gateway](https://github.com/zorneth/osg-gateway) | Control-plane HTTP daemon |
| [osg-display](https://github.com/zorneth/osg-display) | noVNC helpers |
| [osg-sdk](https://github.com/zorneth/osg-sdk) | Go client |
| [osg-python](https://github.com/zorneth/osg-python) | Python client |

### Images (GHCR)

```text
ghcr.io/zorneth/osg/gateway
ghcr.io/zorneth/osg/sandboxes/{base,gui,gpu,cursor,claude,codex}
```

### Design

- **Multi-repo** — each module is its own git remote (not a monorepo)
- **Default deny** — L4/L7 egress allowlists in `osg-core`
- **OpenShell-shaped** — host-gateway alias `host.osg.internal`, provider attach, BYOC

MIT © zorneth
