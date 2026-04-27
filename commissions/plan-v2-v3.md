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
| 27 | Admin approval queue (27·H) | 🔴 NOT SHIPPED | |
| 28 | Per-loan audit timeline (28·I) | 🔴 NOT SHIPPED | Item 19 wrote `createdByName` + `reason` + `reasonNotes` specifically for this to read. View layer still needed. |
| 29 | Finalized-period lock banner + admin override (29·J) | ⚠️ partial | `assertLoanPayPeriodEditable()` + `useFinalizedPayPeriodGuard` shipped in v0.2.0.0; 29·J mockup UI not yet built |

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
| — | Drop `CommissionRule` boolean role flags | 🔴 NOT SHIPPED | Queued in `TODOS.md`; depends on Item 17 + prod backfill verification |
| — | Contractor → Processor data backfill | 🔴 NOT SHIPPED | Script ready at `scripts/backfill-contractor-to-processor.ts`. Dry-run as of v0.3.1.0 identifies 5 production employees (one looks like a vendor — needs triage). Prereq for dropping `Contractor` from the enum. |
| — | Drop `Contractor` from `EmployeeRole` enum | 🔴 NOT SHIPPED | Blocked by backfill above. Postgres `ALTER TYPE ... DROP VALUE` errors if any row still references the value. |

---

## Next up

Item 17 is now fully shipped — the v3 9-role model is live in production. Remaining v3 work, in dependency order:

1. **Contractor cleanup follow-up** — triage the 5 production employees still on `Contractor`, run `scripts/backfill-contractor-to-processor.ts --apply`, then ship a tiny migration that drops `Contractor` from the Prisma enum. Small but highest-priority because it closes out the legacy role.
2. **16·L1 roster People-tab filter chips** — the only Batch 2 lock not yet shipped. Grouped role-family dropdown with active filter chips on the Compensation Roster People tab. Independent of any further schema changes — fully unblocked.
3. **Phase 2 admin/audit surfaces** — Items 27 (admin approval queue), 28 (per-loan audit timeline), 29 (finalized-period lock banner UI). Items 19/20/21 already wrote the data plumbing (createdByName, reason, reasonNotes, AdjustmentReason); these three items are the view layer.
4. **Phase 3 ceremony + safety** — Items 9 (effective-date ceremony dialog 10·P2), 16 (individual producer override for recruiting), 22 (Arive mapper new-role fields — now unblocked by Item 17), 23 (CSV upload deltas — now unblocked), 24 (manual loan form deltas — now unblocked), plus 09·O2 assign-to-employees dialog.
5. **Polish (low-priority)** — add the 5 new role labels to the loose `Record<string, string>` maps in `lenders/send-survey-dialog.tsx`, `lenders/review-list.tsx`, `lenders/lender-ratings-section.tsx`, `nav/profile-menu.tsx`, `commission-templates/[id]/page.tsx`, `resources/resource-permission-manager.tsx`. Build-safe today, but renders raw enum names ("DisclosureDesk") instead of friendly labels ("Disclosure Desk") in those surfaces.

Keep this file synced: update status cells in the same PR as the item ships.
