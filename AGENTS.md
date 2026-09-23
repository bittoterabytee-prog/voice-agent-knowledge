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

### Before every task (knowledge + SRD + Jira)

On **every** implement / change / plan request:

1. Check this knowledge repo and the relevant **SRD** (`docs/backend/SRD_BACKEND.md` for backend; frontend architecture/UX docs for UI) before inventing scope.
2. Confirm the Jira ticket key (ask if missing) and read the current description.
3. **Update the Jira ticket description** when the user request changes scope, the ticket is incomplete vs [`TICKET_STANDARDS.md`](docs/process/TICKET_STANDARDS.md), or the ticket drifts from SRD/knowledge. Keep Purpose, Scope, High-Level Flow, Test Cases, and Acceptance Criteria in sync.
4. Prefer repo docs + source over assumptions. If product intent changed, update knowledge/SRD here as well.

See [`.cursor/rules/knowledge-srd-jira.mdc`](.cursor/rules/knowledge-srd-jira.mdc).

### Starting implementation

1. Confirm knowledge/SRD alignment and Jira sync (above).
2. Branch in the **correct** code repo: `feat/{KEY}-…`, `fix/{KEY}-…`, or `bugfix/{KEY}-…`.
3. When pushing shared work, open a pull request. PR body must follow [`BRANCH_AND_PR.md`](docs/process/BRANCH_AND_PR.md): **High-level diagram**, **Description** (scope in/out + Jira), and **Test cases** (every ticket TC) — not a Summary-only stub.
4. After process/architecture changes, update **this** knowledge repo so agents stay accurate.

### Required on every change (code repos)

1. Map ticket test cases / acceptance criteria
2. Add or update tests
3. Update knowledge in the code repo **and** sync relevant files here when shared docs change
4. Backend HTTP routes → update Postman in `voice-agent`
5. **Smoke test** the change ([`docs/process/SMOKE_TESTING.md`](docs/process/SMOKE_TESTING.md)): if smoke fails, fix and re-run; if it passes, **show the user the results**. See [`.cursor/rules/smoke-testing.mdc`](.cursor/rules/smoke-testing.mdc).
