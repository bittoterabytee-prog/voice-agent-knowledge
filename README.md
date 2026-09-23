# Voice Agent Knowledge (shared)

Central **AI agent knowledge** and **MCP setup** for the AI Voice Appointment Agent POC.

| Code repository | Role | GitHub |
| --------------- | ---- | ------ |
| `voice-agent` | Express / TypeScript backend API | https://github.com/bittoterabytee-prog/voice-agent |
| `voice-agent-frontend` | React / Vite dashboard + browser voice UI | https://github.com/bittoterabytee-prog/voice-agent-frontend |
| **`voice-agent-knowledge`** (this repo) | Shared docs, process, MCP client config | https://github.com/bittoterabytee-prog/voice-agent-knowledge |

## Why this repo exists

- **One MCP setup** for the whole product (not duplicated in FE and BE folders)
- **Cross-repo context** so agents see frontend + backend together
- **Shared process** (sprint, tickets, branch/PR) in one place

Implementation detail still lives next to code in each app repo. Prefer those sources when editing APIs or UI; use **this** repo for MCP, process, and product overview.

## Quick start (Cursor MCP)

1. Create a [GitHub PAT](https://github.com/settings/tokens) with **read** access to the three repos above.
2. Copy `.cursor/mcp.json.example` → `.cursor/mcp.json` and replace `YOUR_GITHUB_PAT`.
3. Open **this** repo (or a multi-root workspace that includes it) in Cursor and reload MCP.
4. Confirm Settings → MCP shows the read-only `github` server.

Full guide: [`docs/mcp/MCP_SETUP.md`](docs/mcp/MCP_SETUP.md)

Do **not** commit `.cursor/mcp.json` (gitignored).

## Knowledge map

| Path | Contents |
| ---- | -------- |
| [`AGENTS.md`](AGENTS.md) | What agents should read first |
| [`docs/overview/PRODUCT.md`](docs/overview/PRODUCT.md) | End-to-end product picture |
| [`docs/process/`](docs/process/) | Sprint, backlog, tickets, branch/PR |
| [`docs/backend/`](docs/backend/) | Backend architecture, API, SRD, voice pipeline |
| [`docs/frontend/`](docs/frontend/) | Frontend architecture, structure, mic, UI |
| [`docs/testing/`](docs/testing/) | E2E runbooks (backend + frontend) |
| [`docs/mcp/MCP_SETUP.md`](docs/mcp/MCP_SETUP.md) | MCP install + verification |

## Sync policy

When architecture, APIs, or process change in a code repo:

1. Update the **code repo** docs (source of truth for that layer).
2. Update the matching copy or index under this knowledge repo in the same change set (or a follow-up PR the same day).
3. Keep MCP setup **only** here — not in `voice-agent` or `voice-agent-frontend`.

## Security

- Read-only GitHub MCP by default
- Never commit PATs, `.env`, or provider keys
