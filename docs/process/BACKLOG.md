# Product backlog (by sprint)

Stories follow [`TICKET_STANDARDS.md`](TICKET_STANDARDS.md).  
**Sprint roadmap:** [`SPRINT_PLAN.md`](SPRINT_PLAN.md) — **current = Sprint 3 (Multilingual Voice)**.

Frontend work lives in the **separate frontend repository**; backend work in `voice-agent`.

---

## Sprint 1 — Foundation ✅

Complete: config, DB, MCP, architecture/process docs, backend SRD knowledge. See [`SPRINT_PLAN.md`](SPRINT_PLAN.md).

| Summary | Jira |
| ------- | ---- |
| Centralized config | [KAN-8](https://voiceagentai.atlassian.net/browse/KAN-8) |
| MCP setup | [KAN-9](https://voiceagentai.atlassian.net/browse/KAN-9) |

---

## Sprint 2 — Basic Voice Agent (wrap-up)

| # | Summary | Owner | Status | Jira |
| - | ------- | ----- | ------ | ---- |
| 7 | Implement Browser Microphone & Audio Capture | Frontend | Done | [KAN-10](https://voiceagentai.atlassian.net/browse/KAN-10) |
| 8 | Implement Speech-to-Text Integration | Backend/AI | Done | [KAN-11](https://voiceagentai.atlassian.net/browse/KAN-11) |
| 9 | Implement LLM Conversation Service | Backend/AI | Done | [KAN-12](https://voiceagentai.atlassian.net/browse/KAN-12) |
| 10 | Implement Text-to-Speech Integration | Backend/AI | Done | [KAN-13](https://voiceagentai.atlassian.net/browse/KAN-13) |
| 11 | Implement Real-Time Voice Conversation Pipeline | Backend | Done | [KAN-14](https://voiceagentai.atlassian.net/browse/KAN-14) |
| 12 | Implement Conversation Session & Context Management | Backend | Done | [KAN-15](https://voiceagentai.atlassian.net/browse/KAN-15) |
| 13 | Implement Voice Agent UI (+ backend CORS for :5174) | Frontend / Backend | CORS Done; UI in FE repo | [KAN-16](https://voiceagentai.atlassian.net/browse/KAN-16) |
| 14 | Implement End-to-End Browser Voice Conversation | Full Stack | Done | [KAN-17](https://voiceagentai.atlassian.net/browse/KAN-17) |
| 15 | Add Voice Pipeline Logging & Error Handling (+ est. cost / POC spend) | Full Stack | Done | [KAN-18](https://voiceagentai.atlassian.net/browse/KAN-18) |
| 16 | Add Postman collection for all HTTP APIs | Backend | Done | [KAN-21](https://voiceagentai.atlassian.net/browse/KAN-21) |

**E2E runbook (KAN-17):** [`../testing/E2E_BROWSER_VOICE.md`](../testing/E2E_BROWSER_VOICE.md).

---

## Sprint 3 — Multilingual Voice ← Now

**Epic:** [KAN-22](https://voiceagentai.atlassian.net/browse/KAN-22) — Sprint 3 — Multilingual Voice Agent  
**Labels:** `sprint-3`, `multilingual`, `voice`  
**Architecture:** one conversation engine (not separate EN/HI/Hinglish agents). **No appointment logic.**

| # | Summary | Owner | Status | Jira | Subtasks |
| - | ------- | ----- | ------ | ---- | -------- |
| 1 | Implement Language Detection | Backend/AI | Done | [KAN-23](https://voiceagentai.atlassian.net/browse/KAN-23) | [KAN-33](https://voiceagentai.atlassian.net/browse/KAN-33), [KAN-34](https://voiceagentai.atlassian.net/browse/KAN-34), [KAN-35](https://voiceagentai.atlassian.net/browse/KAN-35) |
| 2 | Implement Multilingual STT | Backend/AI | To Do | [KAN-24](https://voiceagentai.atlassian.net/browse/KAN-24) | [KAN-36](https://voiceagentai.atlassian.net/browse/KAN-36), [KAN-37](https://voiceagentai.atlassian.net/browse/KAN-37), [KAN-38](https://voiceagentai.atlassian.net/browse/KAN-38) |
| 3 | Implement Multilingual LLM Conversation | Backend/AI | To Do | [KAN-25](https://voiceagentai.atlassian.net/browse/KAN-25) | [KAN-39](https://voiceagentai.atlassian.net/browse/KAN-39), [KAN-40](https://voiceagentai.atlassian.net/browse/KAN-40), [KAN-41](https://voiceagentai.atlassian.net/browse/KAN-41) |
| 4 | Implement Multilingual TTS | Backend/AI | To Do | [KAN-26](https://voiceagentai.atlassian.net/browse/KAN-26) | [KAN-42](https://voiceagentai.atlassian.net/browse/KAN-42), [KAN-43](https://voiceagentai.atlassian.net/browse/KAN-43), [KAN-44](https://voiceagentai.atlassian.net/browse/KAN-44) |
| 5 | Implement Dynamic Language Switching | Backend | To Do | [KAN-27](https://voiceagentai.atlassian.net/browse/KAN-27) | [KAN-45](https://voiceagentai.atlassian.net/browse/KAN-45), [KAN-46](https://voiceagentai.atlassian.net/browse/KAN-46), [KAN-47](https://voiceagentai.atlassian.net/browse/KAN-47) |
| 6 | Implement Language Preference & Session State | Backend | To Do | [KAN-28](https://voiceagentai.atlassian.net/browse/KAN-28) | [KAN-48](https://voiceagentai.atlassian.net/browse/KAN-48), [KAN-49](https://voiceagentai.atlassian.net/browse/KAN-49), [KAN-50](https://voiceagentai.atlassian.net/browse/KAN-50) |
| 7 | Implement Multilingual Voice UI | Frontend | To Do | [KAN-29](https://voiceagentai.atlassian.net/browse/KAN-29) | [KAN-51](https://voiceagentai.atlassian.net/browse/KAN-51), [KAN-52](https://voiceagentai.atlassian.net/browse/KAN-52), [KAN-53](https://voiceagentai.atlassian.net/browse/KAN-53) |
| 8 | Implement Multilingual Error & Fallback Handling | Backend | To Do | [KAN-30](https://voiceagentai.atlassian.net/browse/KAN-30) | [KAN-54](https://voiceagentai.atlassian.net/browse/KAN-54), [KAN-55](https://voiceagentai.atlassian.net/browse/KAN-55), [KAN-56](https://voiceagentai.atlassian.net/browse/KAN-56) |
| 9 | Implement Multilingual End-to-End Flow | Full Stack | To Do | [KAN-31](https://voiceagentai.atlassian.net/browse/KAN-31) | [KAN-57](https://voiceagentai.atlassian.net/browse/KAN-57), [KAN-58](https://voiceagentai.atlassian.net/browse/KAN-58), [KAN-59](https://voiceagentai.atlassian.net/browse/KAN-59) |
| 10 | Create Multilingual Test Scenarios | QA/Full Stack | To Do | [KAN-32](https://voiceagentai.atlassian.net/browse/KAN-32) | [KAN-60](https://voiceagentai.atlassian.net/browse/KAN-60), [KAN-61](https://voiceagentai.atlassian.net/browse/KAN-61), [KAN-62](https://voiceagentai.atlassian.net/browse/KAN-62) |

**Suggested order:** **KAN-23 → KAN-28 → KAN-24 / KAN-25 / KAN-26 → KAN-27 → KAN-30 → KAN-29 → KAN-31 → KAN-32**.

Each story includes: **Purpose**, **Scope**, **High-Level Flow**, **Test Cases**, **Acceptance Criteria**, **Definition of Done** (per [`TICKET_STANDARDS.md`](TICKET_STANDARDS.md)).

---

## Later sprints (planned — do not start unless requested)

| Sprint | Theme | Ticket status |
| ------ | ----- | ------------- |
| 4 | Appointment System | Not created yet |
| 5 | Human-like Conversation Behavior | Not created yet |
| 6 | RAG + Tools | Not created yet |
| 7 | Adaptive Voice + Verification | Not created yet |
| 8 | 300 Test Scenarios + Final Demo | Not created yet |

When creating those tickets, follow [`TICKET_STANDARDS.md`](TICKET_STANDARDS.md) + [`../backend/SRD_BACKEND.md`](../backend/SRD_BACKEND.md) and register keys here.
