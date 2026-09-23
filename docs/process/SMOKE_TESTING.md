# Smoke testing (required after changes)

Agents and developers must **smoke-test every change** that can affect runtime behavior before treating the work as done.

**Cursor rule:** [`.cursor/rules/smoke-testing.mdc`](../../.cursor/rules/smoke-testing.mdc) (always apply).

---

## When required

| Change type | Smoke required? |
| ----------- | --------------- |
| Backend / frontend code, config, routes, pipeline | **Yes** |
| Shared API / voice contracts | **Yes** |
| Docs-only (no runtime behavior) | No — note that smoke was skipped |

---

## Loop

```
Change code/config
        │
        ▼
   Run smoke path
        │
   ┌────┴────┐
   │         │
 Fail      Pass
   │         │
   ▼         ▼
Fix code   Show the user
& re-run   the results
```

1. Implement the change.
2. Run the smallest smoke path that proves the change (health → session → relevant API / UI).
3. **Fail** → diagnose, change code, smoke again. Repeat until green.
4. **Pass** → present results to the user (what ran, status codes / UI outcomes, key fields). Do not only say “looks good.”

---

## What to run (defaults)

Match the layer you touched:

| Layer | Minimum smoke |
| ----- | ------------- |
| Backend HTTP | `GET /health`; then the changed route(s). For voice: `POST /api/sessions` → `POST /api/voice/turn` (or step APIs) → complete when DB is up |
| Frontend | Open the affected page; exercise the primary control path against a running API when possible |
| Full stack / voice | Prefer [`docs/testing/E2E_BROWSER_VOICE.md`](../testing/E2E_BROWSER_VOICE.md) / [`E2E_SPRINT2_KAN17.md`](../testing/E2E_SPRINT2_KAN17.md) checklist items that apply |

Always check responses for **secret leakage** (no `sk-…` / Bearer tokens in bodies or logs shown to the user).

If Docker / Postgres / provider keys are down, still smoke what you can (e.g. health + validation, or unit/integration for the pure logic), state what was blocked, and re-run the full path when dependencies are available.

---

## How to report success

Show a short table or bullet list, for example:

| Check | Result |
| ----- | ------ |
| `GET /health` | 200 |
| `POST /api/sessions` | 201 + `callId` |
| Voice turn | 200 + expected fields |
| Secrets in responses | none |

Include ticket-relevant fields (e.g. `languageDetection`, `pipeline` stages) when the change adds them.

---

## PR / ticket alignment

- PR **Test cases** must include smoke (or a clear “docs-only / smoke N/A” note).
- Do not open or merge a “done” claim for runtime work while known smoke is failing.

## Related docs

- [`BRANCH_AND_PR.md`](BRANCH_AND_PR.md)
- [`AGENTS.md`](../../AGENTS.md)
- [`../backend/API_DOCUMENTATION.md`](../backend/API_DOCUMENTATION.md)
- [`../testing/E2E_BROWSER_VOICE.md`](../testing/E2E_BROWSER_VOICE.md)
