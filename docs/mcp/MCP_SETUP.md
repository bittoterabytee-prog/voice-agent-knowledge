# MCP Setup (shared)

Configure an MCP-compatible client so an AI coding agent can **read** the Voice Agent GitHub repos (backend, frontend, and this knowledge repo).

Official server: [github/github-mcp-server](https://github.com/github/github-mcp-server)

## Goals

- Discover structure + docs across **frontend and backend**
- Read issues/PRs when needed
- **Read-only by default** (no accidental writes via MCP)
- **Single setup location** — do not duplicate `.cursor/mcp.json` inside `voice-agent` or `voice-agent-frontend`

## Repos the agent should know

| Repo | URL |
| ---- | --- |
| Knowledge (this) | https://github.com/bittoterabytee-prog/voice-agent-knowledge |
| Backend | https://github.com/bittoterabytee-prog/voice-agent |
| Frontend | https://github.com/bittoterabytee-prog/voice-agent-frontend |

## Cursor setup

1. Create a [GitHub Personal Access Token](https://github.com/settings/tokens) with **read** scopes for the private repos (fine-grained: Contents + Issues + PRs recommended).
2. In **this** knowledge repo:

   ```bash
   cp .cursor/mcp.json.example .cursor/mcp.json
   ```

3. Replace `YOUR_GITHUB_PAT` in `.cursor/mcp.json`.
4. Restart Cursor / reload MCP servers.
5. Settings → MCP → confirm `github` (read-only) tools appear.

`.cursor/mcp.json` is gitignored. Only `.cursor/mcp.json.example` is committed.

### Option A — Remote GitHub MCP (recommended)

Uses `https://api.githubcopilot.com/mcp/readonly` so write tools are not advertised. See `.cursor/mcp.json.example`.

### Option B — Local Docker (read-only)

```json
{
  "mcpServers": {
    "github": {
      "command": "docker",
      "args": [
        "run",
        "-i",
        "--rm",
        "-e",
        "GITHUB_PERSONAL_ACCESS_TOKEN",
        "-e",
        "GITHUB_READ_ONLY=1",
        "-e",
        "GITHUB_TOOLSETS=repos,issues,pull_requests",
        "ghcr.io/github/github-mcp-server"
      ],
      "env": {
        "GITHUB_PERSONAL_ACCESS_TOKEN": "YOUR_GITHUB_PAT"
      }
    }
  }
}
```

## Verification checklist

| ID | Check |
| -- | ----- |
| TC-001 | Client lists GitHub MCP tools after connect |
| TC-002 | Agent can list files in `voice-agent-knowledge` |
| TC-003 | Ask “How does FE talk to BE?” → `docs/overview/PRODUCT.md` |
| TC-004 | Ask “What sprint are we in?” → `docs/process/SPRINT_PLAN.md` |
| TC-005 | Ask “Where is `/api/voice/turn`?” → backend `API_DOCUMENTATION.md` / code |
| TC-006 | Ask “Where is the Voice Agent UI?” → frontend `/calls` + architecture |
| TC-007 | Write tools unavailable in read-only mode |

## Security

- Never commit PATs or put them in docs/screenshots
- Keep MCP read-only until the team explicitly enables write toolsets
- Code-repo `.env` files stay gitignored; do not paste secrets into MCP prompts

## Related

- [`AGENTS.md`](../../AGENTS.md)
- [`docs/overview/PRODUCT.md`](../overview/PRODUCT.md)
- Backend code: https://github.com/bittoterabytee-prog/voice-agent
- Frontend code: https://github.com/bittoterabytee-prog/voice-agent-frontend
