# Commission Plans v2 / v3 — In-repo Status Index

> **This file is a repo-local breadcrumb.** The master plan + locked mockups live outside this repo in the user's gstack project directory. If anything here conflicts with the canonical docs below, the canonical docs win.

## Canonical docs (source of truth)

All paths relative to `C:\Users\krist\.gstack\projects\Epoch-Financial-Group-keystone-app\`:

| Artifact | Path |
|---|---|
| **v3 plan (canonical)** | `ceo-plans/2026-04-15-commission-plans-v3-unified.md` |
| v2 plan (SUPERSEDED, lineage only) | `ceo-plans/2026-04-13-commission-plans-v2.md` |
| S1/S2/S3 locked mockups | `designs/commission-plans-v2-20260413/` |
| Loan commission surface mockups (Batch 1) | `designs/loan-commission-surface-20260415/` |
| New-roles ripple mockups (Batch 2) | `designs/new-roles-ripple-20260415/` |
| Form-alignment mockups (Batch 3) | `designs/form-alignment-20260415/` |

The canonical v3 doc includes `§15 Implementation checklist` — a hand-off-ready Phase 0–4 plan with concrete file pointers. Use it, don't reinvent the checklist here.

## Commit convention

Every commission-plan commit subject references the Item number: `feat(commission-v3): Item N — …`. Keeps this reconstruction easy if the plan docs are ever lost again.

---

## Status table

Fields: **item** · **name** · **status** · **evidence**. "Evidence" points at commits / releases / files that verify the status claim.

### Phase 0 — Vocabulary + Schema Foundation

| # | Item | Status | Evidence |
|---|---|---|---|
| — | "Rate edit" vocabulary swap (§0.1) | ✅ shipped | v0.1.0.1 (`be987b4`) |
| — | `Company.implementationAnchorDate` | ✅ shipped | v0.1.0.1 (`6b99bfc`) |
| — | `AuditLog.flaggedOverride` + `overrideReason` | ✅ shipped | v0.1.0.1 (`6b99bfc`) |

### Phase 1 — Foundation (v2 items + new-roles)

| # | Item | Status | Evidence |
|---|---|---|---|
| 0 | Plan-ownership helper | ✅ shipped | PR #46 (`f2d25f3`) |
| 1 | Mode picker (`/commission-plans/start`) | ✅ shipped | v0.1.0.6 (`3f2aa22`) |
| 2 | Compensation Roster (v1 3-column) | ✅ shipped | PR #47 (`ba30f61`). **Gap vs v3:** 5-tab layout (People default / Templates / Changes / Needs attention / History) not yet shipped — current is 3-column |
| 3 | Starter templates | ✅ shipped (12 of 15) | v0.1.0.6. **Gap vs v3:** 6 new-role starters (Item 17) not added |
| 4 | Kill `Contractor` from `EmployeeRole` | ⚠️ UI only; enum value retained | v0.1.0.6 (`ccc8906`) removed from UI pickers; `scripts/backfill-contractor-to-processor.ts` is ready to migrate remaining rows. Full drop is part of the v3 Item 17 schema-push PR (separate, coordinated) |
| 6 | Two-radio deduction disclosure | ✅ shipped | v0.1.0.5 (`4d169ff`) |
| 7 | Role-grouped individual plans tab | ✅ shipped | Part of Item 0 / Compensation Roster work |
| 17 | Five new `EmployeeRole` values + grouped pickers | ✅ shipped | **v0.2.2.0:** scaffolding (`PLAN_TYPE_OPTIONS_GROUPED`, `BACK_OFFICE_ROLES`, `ROLE_FAMILY`, `shouldShowTaxClassificationPicker`, `isBackOfficeCommissionOptIn`, `RoleFamilyChips`, 9-role `DEFAULT_PORTAL_PERMISSIONS` with Payroll restricted, full `ROLE_LABELS`). **v0.2.2.1:** 17·M1 Block 1 refresh — `commission-template-form.tsx` now uses grouped chips. **v0.3.1.0:** schema push — added 5 enum values to Prisma + Supabase via `npx prisma db push`, mirrored across all 5 Zod schemas + AI tool enum + `confirm-employees` mapCSVRole + `api/leads` ROLE_MAP, restored DisclosureDesk + LockDesk in `PLAN_ELIGIBLE_ROLES` and added `BACK_OFFICE_ELIGIBLE_ROLES` + `employeeHasBackOfficeRole` helper, dropped the 4 enum entries from `CHIP_DISABLED_ROLES` so admins can now select all 5 new roles. Replaced `crm-contact-people.tsx`'s narrow string-literal union with `EmployeeRole` from `@/generated/prisma`. **Follow-up:** Contractor backfill (5 employees identified, awaiting triage) + Contractor enum drop |
| 18 | `CommissionRule.targetRole` column (dual-read/write) | ✅ shipped | v0.1.0.7, PR #52 (`955ebb6`). Backfill script: `scripts/backfill-commission-rule-target-role.ts`. Boolean-flag drop queued in TODOS behind Item 17 |

### Phase 2 — Preview + Explainability

| # | Item | Status | Evidence |
|---|---|---|---|
| 8 | `CompStackPreview` (builder sticky rail) | ✅ shipped | v0.2.1.0 (`a3eb9fb`) |
| 19 | Ledger-first loan Commissions tab + scoped adjustment modal (12·A3 / 14·F2) | ✅ shipped | v0.2.1.0 (`e2ad5bd`) |
| 20 | `CommissionExplainInline` (no drawer) | ✅ shipped | v0.2.1.0 (`750fe5b`) |
| 21 | 5-source `PrecedenceChip` + calculator extension | ✅ shipped | v0.2.1.0 (`20aa67f`) |
| 27 | Admin approval queue (27·H) | ✅ shipped | New `CommissionChangeRequest` model + 4 server actions in `src/lib/actions/commission-change-requests.ts`. Page at `/{companySlug}/run-commissions/pending-approvals` with sidebar `pendingApprovals` count badge. Admins skip the queue (call direct-write actions); non-admins call `submitCommissionChangeRequest` from the Finalized Guard's Request-Change form. |
| 28 | Per-loan audit timeline (28·I) | ✅ shipped | `getLoanCommissionAudit` reads `AuditLog` rows scoped to a loan's modifiers, adjustments, revenue lines, and change requests. `<LoanCommissionAudit>` mounted at the bottom of the loan Commissions tab; `flaggedOverride` rows render amber + flag icon with a "Show flagged only" filter. `audit()` helper in `src/lib/audit.ts` extended to accept `flaggedOverride` + `overrideReason`; all 7 commission mutations now write audit rows that this timeline reads. |
| 29 | Finalized-period lock banner + admin override (29·J) | ✅ shipped | `useFinalizedPayPeriodGuard` rewritten as a dual-modal hook: non-admins see Request-Change form (routes to Item 27); admins see Override-Lock modal with required reason + acknowledgment. `assertLoanPayPeriodEditable` returns `{ flaggedOverride, overrideReason }` so callers stamp them on the audit row. The pay-period-level `unfinalizePayPeriod` admin operation stays — only the per-loan unlock path was removed. |

### Phase 3 — Ceremony + Safety

| # | Item | Status | Evidence |
|---|---|---|---|
| 9 | Effective-date ceremony dialog (10·P2) + `ScheduledPlanChange` model | 🔴 NOT SHIPPED | `Starting soon` bar on roster uses temp `Employee.startDate > now()` query until this lands |
| 16 | Individual producer override (recruiting) | 🔴 NOT SHIPPED | |
| 22 | Arive mapper new-role fields | 🔴 NOT SHIPPED | Blocked by Item 17 |
| 23 | CSV upload deltas (new roles) | 🔴 NOT SHIPPED | Blocked by Item 17 |
| 24 | Manual loan form role-assignee section | 🔴 NOT SHIPPED | Blocked by Item 17 |
| — | Individual plan form (07·N1) — S2-parity layout | ⚠️ shell + blocks + inspector + diff shipped; auto-save / draft store / effective-date ceremony deferred | This PR: 3-column shell (outline / stream / inspector), 4 collapsible blocks (Who it's for / Earnings / Deductions / Special cases), override pills on diverged blocks, sticky inspector with plain-English preview + diff-from-template rows, shared `RoleFamilyChips` component (Block 1 read-only, 9 roles grouped by family), reset-to-template affordances. Deferred: auto-save drafts (Item 10), Set effective date modal (Item 9·P2), Discard draft (Item 10) |
| — | Assign-to-employees dialog (09·O2) — two-pane picker | 🔴 NOT SHIPPED | |

### Phase 4 — AI Entry Points

| # | Item | Status | Evidence |
|---|---|---|---|
| 10 | Draft-store pattern (3 stores) | 🔴 NOT SHIPPED | |
| 11 | "Build with AI" button on Templates | 🔴 NOT SHIPPED | |
| 12 | "Describe plan" in Roster | 🔴 NOT SHIPPED | |
| 13 | AI individual plan tools | 🔴 NOT SHIPPED | |
| 14 | AI edit-template tool | 🔴 NOT SHIPPED | |
| 15 | System prompt expansion (nine-role strategy) | 🔴 NOT SHIPPED | Blocked by Item 17 |
| 25 | Onboarding wizard integration | 🔴 NOT SHIPPED | |
| 26 | AI loan adjustments + bulk onboarding tools | 🔴 NOT SHIPPED | |

### Other tracked work

| # | Item | Status | Notes |
|---|---|---|---|
| — | Drop `CommissionRule` boolean role flags | 🔴 NOT SHIPPED | Queued in `TODOS.md`; depends on Item 17 + prod backfill verification (Item 17 done as of v0.3.1.0) |
| — | Contractor data cleanup | ✅ shipped (v0.3.1.1) | Strip-only (not migrate-to-Processor) was the correct call for these 5 rows — they were external relationships, not contract processors. 5 employees + 5 mirrored CRM contact rows stripped. Empty-roles employees stay active; admins can flag externally in the UI. |
| — | Drop `Contractor` from `EmployeeRole` enum | ✅ shipped (v0.3.1.1) | `npx prisma db push --accept-data-loss` ran `ALTER TYPE "EmployeeRole" DROP VALUE 'Contractor'` on Supabase. Safe — strip ran first, zero rows referenced the value. |

---

## Next up

Phase 2 is closed out — Items 27, 28, 29 shipped together. Phase 1 (Item 17 in v0.3.1.0) and the legacy `Contractor` retirement (v0.3.1.1) are also done. Remaining v3 work, in dependency order:

1. **16·L1 roster People-tab filter chips** — the only Batch 2 lock not yet shipped. Grouped role-family dropdown with active filter chips on the Compensation Roster People tab. Fully unblocked.
2. **Phase 3 ceremony + safety** — Items 9 (effective-date ceremony dialog 10·P2), 16 (individual producer override for recruiting), 22 (Arive mapper new-role fields — now unblocked by Item 17), 23 (CSV upload deltas — now unblocked), 24 (manual loan form deltas — now unblocked), plus 09·O2 assign-to-employees dialog.
3. **Phase 3.5 — Run Commissions loan-level parity (§9.8)** — `EarningsTab` row-level "Edit rate for this loan" / "Add adjustment" reusing the loan-detail components and the new approval-queue + override-lock substrate.
4. **Drop `CommissionRule` boolean role flags** — `targetRole` column has been dual-read/dual-write since Item 18 shipped in v0.1.0.7. Now that Item 17 is fully done and the boolean flags are no longer needed for new roles, the dual-write scaffolding can come out. See `TODOS.md`.

Keep this file synced: update status cells in the same PR as the item ships.
