# Agent guide (shared)

Before changing **backend** or **frontend**, read:

1. [`docs/overview/PRODUCT.md`](docs/overview/PRODUCT.md) — how FE + BE fit together
2. [`docs/process/SPRINT_PLAN.md`](docs/process/SPRINT_PLAN.md) — current sprint
3. [`docs/process/TICKET_STANDARDS.md`](docs/process/TICKET_STANDARDS.md) — Jira format
4. [`docs/process/BRANCH_AND_PR.md`](docs/process/BRANCH_AND_PR.md) — branch / PR workflow
5. Layer docs:
   - Backend work → [`docs/backend/`](docs/backend/) (especially `ARCHITECTURE.md`, `SYSTEM_FLOW.md`, `SRD_BACKEND.md`, `API_DOCUMENTATION.md`)
   - Frontend work → [`docs/frontend/`](docs/frontend/) (especially `ARCHITECTURE.md`, `SYSTEM_FLOW.md`, `PROJECT_RULES.md`)
6. MCP: [`docs/mcp/MCP_SETUP.md`](docs/mcp/MCP_SETUP.md)

### Code remotes

- Backend: https://github.com/bittoterabytee-prog/voice-agent
- Frontend: https://github.com/bittoterabytee-prog/voice-agent-frontend

Prefer **repository docs + source** in the repo you are editing over assumptions. Backend availability is the source of truth for appointments.

### Starting implementation

1. Confirm the Jira ticket key (ask if missing).
2. Branch in the **correct** code repo: `feat/{KEY}-…`, `fix/{KEY}-…`, or `bugfix/{KEY}-…`.
3. When pushing shared work, open a pull request.
4. After process/architecture changes, update **this** knowledge repo so agents stay accurate.

### Required on every change (code repos)

1. Map ticket test cases / acceptance criteria
2. Add or update tests
3. Update knowledge in the code repo **and** sync relevant files here when shared docs change
4. Backend HTTP routes → update Postman in `voice-agent`
