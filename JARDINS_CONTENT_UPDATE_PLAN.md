# Jardins de Leiria — Content Update Plan (pre-Monday review)

**File:** `jardins-de-leiria/index.html`
**Scope:** content only — no CSS, no architecture, no other page. Nothing in this document has been applied to the code yet.
**Note on structure:** every text field exists twice — once in the `pt:{...}` block, once in the `en:{...}` block (both starting around line 232 and line 375). Any content change approved below needs to be made in **both** places to keep PT/EN parity; I've flagged this per item rather than repeating it forty times.

I audited the file against itself — cross-checking the Overview status grid against the Deliverables, Action Matrix, Document Register, Risk Register and Roles tabs — to find places where the dashboard currently contradicts itself or is too generic/empty to present Monday. I have **not** invented any new facts (survey results, financial figures, CLIU's role, etc.) — where the "proposed update" needs a real fact, I've marked it "needs your input" and specified exactly what I need from you.

---

## 1. Current project status (Overview tab / status grid)

| | |
|---|---|
| **Current entry** | `recText` narrative says "advanced structuring phase... awaiting developer input"; the status grid (`DS.statusData`) computes to **~69% investor readiness** shown as the big progress bar. |
| **Inconsistent because** | The 69% is pulled up almost entirely by categories BridgePoint authored itself (`structure`, `docs`, `finance`, `pmo` — 23 of 48 items, all green) while the categories that actually gate external readiness (`tech`: 0 green / 3 amber / 3 red, `legal`: 1 green / 4 amber, `finval`: external validation still red) are the ones dragging behind. A number that high next to a narrative that says "awaiting promoter input" and an Action Matrix that's mostly "waiting/blocked" risks reading as overstated to an investor who only looks at the top of the page. |
| **Proposed update** | Needs your input — either confirm 69% is still accurate today, or tell me which category items should move (see items 2–6 below) so the % recalculates honestly. |
| **Source confirmation needed** | You / Carlos Simões — current true completion state per category, not just the headline number. |
| **Data object to edit** | `DS.statusData` (line ~510–519) — this is the single source the % is computed from; do not edit `investorReadiness`/`phases` labels without also fixing the underlying grid. |

---

## 2. Topographic survey

| | |
|---|---|
| **Current entry** | Everywhere it appears it's marked **not delivered**: `categories.tech` → `Topografia` = red; `delivItems[2]` "Levantamento Topográfico" = red/no deadline; `docItems[7]` = pending, version "—"; `actionItems[1]` "Receber Levantamento Topográfico" = waiting; `riskItems[1]` "Topografia desatualizada" = open, mitigation "Solicitação enviada" (request sent). |
| **Inconsistent because** | Internally consistent with itself (all red/pending/waiting) — but "Solicitação enviada" as a risk mitigation is generic and undated, and if the survey has since been received or scheduled, five separate places need updating together. |
| **Proposed update** | Needs your input — has it arrived? If yes: flip `tech[1]`, `delivItems[2].st`, `docItems[7].st/ver/date`, `actionItems[1].st` together, and either close or update `riskItems[1]`. If no: at minimum give it a real deadline/date instead of the blank `deadline:''`. |
| **Source confirmation needed** | Carlos Simões / JTA — delivery status and date. |
| **Data object to edit** | `DS.statusData.tech[1]`, `delivItems[2]`, `docItems[7]`, `actionItems[1]`, `riskItems[1]` (all in `T.pt`, mirrored in `T.en`). |

---

## 3. Masterplan (Plano Diretor)

| | |
|---|---|
| **Current entry** | `categories.tech` → "Plano Diretor (Masterplan)" = amber; `delivItems[3]` = amber/no deadline; `docItems[6]` = pending, version "—"; `actionItems[2]` "Receber Masterplan Final" = waiting; `decItems[2]` "Masterplan a ser entregue em fase seguinte" (to be delivered in the next phase) — undated, no owner beyond "Carlos Simões". |
| **Inconsistent because** | "Amber / in preparation" everywhere, but the decision log entry that set that expectation has no date and no concrete next-phase milestone, so there's no way to tell from the dashboard alone whether it's overdue. |
| **Proposed update** | Needs your input — current draft status, and a real target date to replace the open-ended "next phase" language. |
| **Source confirmation needed** | Carlos Simões / JTA. |
| **Data object to edit** | `categories.tech[0]` status, `delivItems[3]`, `docItems[6]`, `actionItems[2]`, `decItems[2]`. |

---

## 4. Financial model — **highest-priority inconsistency found**

| | |
|---|---|
| **Current entry** | `categories.finance` (Preliminary Financial Work) shows **all 6 items green** — CAPEX model, revenue model, cash flow projections, ROI scenarios, sensitivity analysis, assumptions all "done." Meanwhile `delivItems[1]` "Modelo Financeiro" = **red/missing**, `docItems[1]` = pending, `actionItems[0]` "Receber Modelo Financeiro" = waiting, and it's the **#1 entry in the Risk Register** ("Modelo Financeiro atrasado", high/high/open). |
| **Inconsistent because** | The dashboard is presenting two different things under similar names without saying so: BridgePoint's own *preliminary* modeling work (marked 100% done) vs. the promoter's *official* financial model (marked missing and the top risk). An investor skimming the Overview tab sees "finance: all green" and could reasonably miss that the actual bankable model doesn't exist yet. This needs either a labeling fix (make clear "Preliminary Financial Work" ≠ "Financial Model deliverable") or a status fix if the real model has since arrived. |
| **Proposed update** | Needs your input — is the promoter's financial model still outstanding? If yes, I'd suggest relabeling `categories.finance`'s section title to make the "preliminary/BridgePoint-side" scope explicit, so it stops reading as if the real deliverable is done. If the model has since arrived, this cascades through `delivItems[1]`, `docItems[1]`, `actionItems[0]`, and `riskItems[0]` (likely closing that risk). |
| **Source confirmation needed** | You — confirm whether this is a labeling problem, a status problem, or both. |
| **Data object to edit** | `categories.finance` (title/items), `DS.statusData.finance`, `delivItems[1]`, `docItems[1]`, `actionItems[0]`, `riskItems[0]`. Same question applies to `categories.finval[0]` "Modelo financeiro (Preliminar)" = green — check whether that label is also being misread. |

---

## 5. Technical validation

| | |
|---|---|
| **Current entry** | `categories.tech` = 0 green / 3 amber / 3 red (Masterplan, Topografia, Arquitetura, Planeamento de infraestruturas, BoQ, Custos de construção vinculativos). Priority 1 in the PMO Tracker ("Bases Técnicas") lists the same 5 open tasks, all unchecked (`tasksData[0]` = all `false`). |
| **Inconsistent because** | Internally consistent, but zero of the six technical items are marked complete, which conflicts with the Overview narrative calling the project "advanced structuring phase" — technical validation reads as the least-advanced area on the whole dashboard. Worth confirming this is still accurate before Monday rather than presenting it unreviewed. |
| **Proposed update** | Needs your input — anything technical actually resolved since this was last touched (architecture progress, infrastructure planning)? |
| **Source confirmation needed** | Carlos Simões / JTA + Angola project team. |
| **Data object to edit** | `DS.statusData.tech`, `DS.tasksData[0]`, `priorities[0].tasks`. |

---

## 6. Legal documentation

| | |
|---|---|
| **Current entry** | `categories.legal` = Surface Rights green, the other four (proof of ownership, corporate structure, permits, contracts) all amber. But on the **Roles** tab, "Documentação Jurídica" (owner: Angola Project Team) is marked **`st:'open'`** (red pill "Em aberto") — a coarser, more negative status than the amber detail underneath it. |
| **Inconsistent because** | Two different granularities disagree: the detailed grid says "mostly in progress," the summary role card says "not started." One of them is wrong. |
| **Proposed update** | Needs your input — pick the accurate one; I'd default to trusting the detailed grid (amber = in progress) and updating `roles[5].st` from `'open'` to `'ongoing'`, unless legal work has genuinely stalled. |
| **Source confirmation needed** | Angola project team / legal counsel — actual current state of each of the 5 legal items. |
| **Data object to edit** | `roles[5]` (Documentação Jurídica), `DS.statusData.legal`, `priorities[1].tasks` (Priority 2 tracker). |

---

## 7. CLIU involvement — **not present anywhere in the current dashboard**

| | |
|---|---|
| **Current entry** | No mention of "CLIU" anywhere in the file — not in Roles, Deliverables, Action Matrix, Risk Register, Decision Log, or Meeting Log. |
| **Inconsistent because** | N/A — this isn't an inconsistency, it's a gap. If CLIU is now a stakeholder in this project, none of the dashboard's tabs currently reflect that. |
| **Proposed update** | Cannot propose without more information. |
| **Source confirmation needed** | **I need you to tell me:** (1) what CLIU is/stands for and their role in this project, (2) since when they've been involved, (3) which tab(s) should reference them — Roles (as a new row)? Action Matrix (new action items)? Decision Log (a decision involving them)? Risk Register (a dependency/risk)? |
| **Data object to edit** | TBD once scope is known — likely a new row in `roles[]` and/or `actionItems[]`, possibly `decItems[]`. |

---

## 8. Promoter deliverables (`delivItems`, 7 rows)

| Row | Current | Note |
|---|---|---|
| Business Plan Atualizado | amber, no deadline | needs your input: still in prep? real deadline? |
| Modelo Financeiro | red, no deadline | see item 4 above |
| Levantamento Topográfico | red, no deadline | see item 2 above |
| Plano Diretor (Masterplan) | amber, no deadline | see item 3 above |
| Medições (BoQ) | red, no deadline | needs your input |
| Alvará Atualizado | amber, no deadline | needs your input — building permit renewal status |
| Estimativas de Custos de Construção | red, no deadline | needs your input |

**Inconsistent because:** all 7 rows have an empty `deadline` field — the table has a "PRAZO" (deadline) column that's currently blank for every single item, which weakens the "waiting on the promoter" framing for Monday (no dates to point to).
**Source confirmation needed:** Carlos Simões — real target dates for each, even if approximate.
**Data object to edit:** `delivItems[]`, all 7 entries, `deadline` field specifically.

---

## 9. Action matrix (`actionItems`, 8 rows)

| Row | Current status |
|---|---|
| Receber Modelo Financeiro | waiting |
| Receber Levantamento Topográfico | waiting |
| Receber Masterplan Final | waiting |
| Atualizar Investment Memorandum | waiting |
| Validação Financeira Externa | blocked |
| Investor Outreach | blocked |
| Preparar Data Room | blocked |
| Processo NDA | blocked |

**Inconsistent because:** every single row is either "waiting" or "blocked" — there are zero "done" or "in progress" entries anywhere in the Action Matrix, which for a PMO tracker being shown to investors reads as fully stalled. Combined with the 69% readiness figure (item 1), this is the clearest internal contradiction in the whole file.
**Proposed update:** needs your input — has anything actually moved since this was written? Even partial progress on one item would materially change how Monday's presentation reads.
**Source confirmation needed:** you / Carlos Simões, item by item.
**Data object to edit:** `actionItems[]`, `due` fields (also all empty) and `st` fields.

---

## 10. Risk register (`riskItems`, 5 rows)

| Row | Current | Note |
|---|---|---|
| Modelo Financeiro atrasado | high/high/open, mitigation "Prazo acordado com Carlos" | see item 4 |
| Topografia desatualizada | medium/high/open, mitigation "Solicitação enviada" | see item 2 |
| Due Diligence de terreno pendente | low/high **... impact shown as "critical"**, open, "Dependência crítica" | see below |
| Atraso nas licenças | medium/high, open, **mitigation blank** | needs input |
| Custos de construção não vinculativos | high/high, open, **mitigation blank** | needs input |

**Inconsistent because:** two of five risks have no mitigation text at all (blank string), which is a gap for an investor-facing risk register, not a contradiction — but worth closing before Monday. Also worth double-checking "Due Diligence de terreno pendente" — probability is "low" while impact is "critical" and it's described as a "critical dependency," which reads oddly as *low probability*; confirm that's intentional (low chance of happening, but severe if it does) rather than a mismatch with what's actually meant.
**Proposed update:** needs your input for the two blank mitigations; confirm the probability/impact pairing on the land DD risk.
**Source confirmation needed:** you.
**Data object to edit:** `riskItems[2].prob` (confirm), `riskItems[3].mitigation`, `riskItems[4].mitigation`.

---

## 11. Roadmap (`roadmapSteps` / `DS.roadmapData`)

| Current | |
|---|---|
| 12 steps; step 3 ("Prontidão para Investidores") = `active`; steps 4–11 ("Entregas do Promotor" through "Investor Engagement") = `open`; steps 1–2 = `done`; step 12 ("Financiamento") = final goal, implicitly open. |

**Inconsistent because:** internally consistent with the rest of the file (matches the "waiting on promoter" narrative), so no contradiction — flagging only because if any of items 2–6 above get updated (survey received, masterplan delivered, etc.), the corresponding roadmap dot should move from `open` to `active`/`done` too, otherwise the roadmap will contradict the updated detail tabs.
**Proposed update:** dependent on outcomes of items 2–6.
**Source confirmation needed:** none additional — this one follows from the others.
**Data object to edit:** `DS.roadmapData` (array of `done`/`active`/`open`), `roadmapSteps[].note` text.

---

## 12. Decision log (`decItems`, 3 rows)

| Row | Current |
|---|---|
| BridgePoint assume função PMO no projeto | dated "Jul 2026" only (no day), by "BridgePoint / Carlos" |
| Modelo Financeiro será atualizado pelo promotor | "Jul 2026", by Carlos Simões |
| Masterplan a ser entregue em fase seguinte | "Jul 2026", by Carlos Simões |

**Inconsistent because:** all three entries share the same month-only date with no day, and there are only 3 entries total for what's described as an active, multi-week PMO engagement — if meetings/decisions have happened since (see item 13, meeting log), this list is almost certainly incomplete.
**Proposed update:** needs your input — any decisions since these three? Also worth adding exact dates where known.
**Source confirmation needed:** you / Carlos Simões.
**Data object to edit:** `decItems[]` — append new rows, backfill day-level dates on existing ones if available.

---

## 13. Meeting log — **important operational flag, not just a content gap**

| | |
|---|---|
| **Current entry** | `logInitial` — a single static line ("PMO Report v1.0 initiated... validation pending"), dated generically "Julho 2026." `DS.logData` (the array that holds any manually-added meeting notes) is **empty** (`logData:[]`). |
| **Why this matters right now** | Before the persistence hotfix (Phase 0A, shipped this week), the "Adicionar Entrada" meeting-log feature called a storage API that didn't exist in production — every note anyone typed in and clicked "save" on **was silently lost and never actually stored**, even though the dashboard showed a green "saved" confirmation at the time. If you or Carlos used this feature at any point before the fix, that history is gone from the file and needs to be re-entered manually now that saving actually works. |
| **Proposed update** | Needs your input — do you recall any meeting notes or decisions logged via the dashboard itself (as opposed to email/memory) before this week? If so, they need to be retyped. |
| **Source confirmation needed** | You — best recollection of what was logged and lost. |
| **Data object to edit** | `logInitial` (both languages) if you want a note about the fix itself; otherwise new entries would normally go through the live "Adicionar Entrada" UI rather than being hardcoded, since `logData` is meant to be user-entered, not seeded in source. |

---

## 14. Executive recommendation (`recText`)

| | |
|---|---|
| **Current entry** | "...encontra-se em fase avançada de estruturação... BridgePoint aguarda input do promotor para prosseguir." (advanced structuring phase, BridgePoint awaiting promoter input). |
| **Inconsistent because** | This is the single paragraph investors are most likely to actually read, and it needs to match whatever gets resolved in items 1–13 above — right now it's generically accurate but says nothing Monday-specific (no mention of CLIU, no specific asks, no timeline). |
| **Proposed update** | Should be rewritten last, after items 1–13 are resolved, so it accurately summarizes the final state rather than needing a second pass. |
| **Source confirmation needed** | You — final sign-off on tone/framing for an investor audience. |
| **Data object to edit** | `recText` (both languages) — do this last. |

---

## 15. Investor readiness percentage

Covered in item 1 — repeating here only to confirm it's on the list: this number is **derived**, not directly editable text. It will only change if the underlying `DS.statusData` grid changes as a result of items 2–6. Recalculating it is the last step, not a separate edit.

---

## What I need from you before I can turn this into actual content

In priority order for Monday:

1. **Financial model** (item 4) — real status, and whether "Preliminary Financial Work" vs. the actual deliverable needs relabeling. This is the clearest contradiction on the dashboard right now.
2. **Action matrix** (item 9) — is everything really still "waiting/blocked," or has something moved?
3. **CLIU** (item 7) — who/what they are and where they belong.
4. **Topographic survey, masterplan, BoQ, permit, construction-cost deliverables** (items 2, 3, 8) — current status + real deadlines.
5. **Legal status mismatch** (item 6) — amber-detail vs. red-summary.
6. **Meeting log** (item 13) — any notes lost to the pre-fix storage bug that need re-entering.
7. Everything else (risk mitigations, decision log entries, roadmap dots, executive summary) follows once 1–6 are answered.

No code has been changed. Waiting for your answers (or a go-ahead to proceed with whatever subset you can confirm now) before I touch `jardins-de-leiria/index.html`.
