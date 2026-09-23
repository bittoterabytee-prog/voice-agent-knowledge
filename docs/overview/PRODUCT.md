# Product overview (frontend + backend)

Browser-based AI Voice Appointment Agent POC — **no telephony**.

```
┌────────────────────────────┐         HTTP + CORS          ┌────────────────────────────┐
│ voice-agent-frontend       │ ───────────────────────────► │ voice-agent (Express)      │
│ React + Vite (:5174)       │                              │ API (:3000)                │
│ /calls Voice Agent UI      │                              │ /health                    │
│ mic → base64 clip          │                              │ /api/sessions              │
│ play TTS audio             │                              │ /api/voice/turn            │
└────────────────────────────┘                              │ STT → LLM → TTS            │
                                                            │ PostgreSQL + session state │
                                                            └────────────────────────────┘
```

## Sprint 2 happy path

1. Backend: `npm run deps:up && npm run db:migrate && npm run dev` → `:3000`
2. Frontend: Vite → **`http://localhost:5174/calls`** (not `5173`)
3. `GET /health` → System Status Healthy (CORS)
4. Start → `POST /api/sessions` → `callId`
5. Speak → `POST /api/voice/turn` with `audioBase64` + `callId`
6. Show transcript / reply; play audio (or soft-fail on `ttsError`)
7. Multi-turn with same `callId` → Stop → `POST /api/sessions/:callId/complete`

Runbooks:

- Backend-oriented: [`../testing/E2E_BROWSER_VOICE.md`](../testing/E2E_BROWSER_VOICE.md)
- Frontend-oriented: [`../testing/E2E_SPRINT2_KAN17.md`](../testing/E2E_SPRINT2_KAN17.md)

## Repos

| Concern | Where |
| ------- | ----- |
| API, DB, STT/LLM/TTS, sessions | `voice-agent` |
| Dashboard UI, mic, voice turn client | `voice-agent-frontend` |
| MCP + shared agent knowledge | **this repo** |

## Rules (cross-cutting)

- Backend is source of truth for appointment availability
- Never invent bookings; never leak API keys
- Browser mic POC only (no Twilio required for Sprint 2)
- See backend [`PROJECT_RULES.md`](../backend/PROJECT_RULES.md) and frontend [`PROJECT_RULES.md`](../frontend/PROJECT_RULES.md)
