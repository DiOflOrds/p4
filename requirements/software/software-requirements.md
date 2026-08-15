# Software Requirements — P4 "Mission Control 3.1" (extension of platform baseline)

*Extends SWR-001–047; numbering continues. Components: BCK/FRT (backend/frontend), OPS (Betrieb/Runbook). Language: English (D011). Status `reviewed` = feasibility + verifiability per DoD checklist. Verification is UI/device acceptance checklist plus tests; test coverage lands with Sprint 1. v0.1 Sprint 0, T-0003 — G1 pending (Inbox-DR T-0005).*

## LAN access with PIN protection (P4-E1)

| ID | Requirement | Trace | Verification | Prio | Status |
|---|---|---|---|---|---|
| SWR-048 | The server shall reject write requests (decisions, mailbox messages) from non-localhost clients unless they carry the PIN configured via a local environment variable (never stored in Git); read endpoints remain available without PIN; localhost keeps working without PIN (backward compatible). | STK-016 | API tests (localhost ok, remote simulated without/with wrong/with correct PIN) + device checklist | high | reviewed |
| SWR-049 | The frontend shall offer a PIN entry kept for the browser session and send it with every write request; a missing or wrong PIN yields a clear German message instead of a technical error. | STK-016 | UI acceptance checklist (wrong-PIN attempt) + API tests (error text path) | medium | reviewed |

## Team mailbox (P4-E3)

| ID | Requirement | Trace | Verification | Prio | Status |
|---|---|---|---|---|---|
| SWR-050 | The backend shall accept mailbox messages per project and store each as a versioned markdown file with metadata (author, time, status open/answered) under the project's management area, committed immediately (inbox pattern); the conversation (messages and team replies) shall be served via API in chronological order. | STK-016 | API tests (post → file+commit, list order, reply visible) + E2E acceptance checklist (K4) | high | reviewed |
| SWR-051 | The frontend shall provide a team-chat tab showing the conversation and a message form usable on desktop and mobile; projects with unanswered messages shall be visible in the cockpit. | STK-016 | UI acceptance checklist (browser + phone) + API test (cockpit flag) | high | reviewed |

## Mobile usability (P4-E2)

| ID | Requirement | Trace | Verification | Prio | Status |
|---|---|---|---|---|---|
| SWR-052 | All views shall be usable on an Android/Chrome phone: touch-sized controls, primary layouts without horizontal overflow, PWA installable from the LAN address. | STK-016 | Device acceptance checklist (real phone, incl. one button decision) | high | reviewed |

## Traceability

STK-016 ← SWR-048–052 (complete; no orphans). DoD checklist applied per SWR (2026-08-15 RM). Security guardrail (kein Internet-Expose, PIN ≠ Passwortersatz im offenen Netz) dokumentiert in ADR-006 + Runbook. G1 pending (T-0005); Schreibschutz-Modell und Briefkasten-Ablage in G2 (T-0006).
