# Versioning

Every time a policy is published in EpochOS, a version snapshot is automatically created. This provides a complete history of changes over the life of the policy -- essential for regulatory compliance, internal audits, and accountability.

---

## How versioning works

### Automatic version creation

Versions are created automatically when you **publish** a policy. You do not need to manually create versions. The workflow is:

1. Edit a policy (it moves to Draft status if it was previously Published).
2. Click **Publish** when you are satisfied with the changes.
3. EpochOS prompts you for an optional **change note** describing what was modified.
4. A new version is created containing:
   - A sequential **version number** (1, 2, 3, ...).
   - The **title** of the policy at that point in time.
   - A snapshot of the full **content** as it existed when published.
   - The **change note** you entered.
   - The **employee** who published the version.
   - A **timestamp** of when the version was created.
5. The policy status changes to Published.

### Version numbering

Versions are numbered sequentially starting at 1. Each time you publish, the version number increments by one. Version numbers never reset and are unique within a policy.

### What is captured

A version captures the **complete content** of the policy at the time of publishing. This means you can view any version and see exactly what the policy said at that point -- not just a diff of what changed.

---

## Viewing version history

1. Open the policy whose history you want to review.
2. In the policy detail view, find the **Version History** panel (typically in the sidebar or a dedicated tab).
3. The version list shows all published versions in reverse chronological order (newest first).

Each version entry displays:

- **Version number** -- e.g., "Version 3"
- **Date** -- When the version was created
- **Change note** -- The description entered at publish time (if provided)
- **Author** -- The employee who published the version

> **Screenshot placeholder:** *Version history panel showing three versions with version numbers, dates, change notes, and author names.*

---

## Viewing a specific version

1. In the version history list, click **View** next to the version you want to inspect.
2. A read-only view of the policy content as it existed in that version is displayed.
3. The version view shows the title and full content from that point in time.

This is useful when:

- An auditor asks what your policy said on a specific date.
- You want to compare the current content against a previous version.
- You need to reference the exact language that was in effect during a particular period.

---

## Restoring a previous version

If a recent change needs to be rolled back, you can restore a previous version:

1. Open the version history for the policy.
2. Find the version you want to restore.
3. Click the **Restore** button (the rotate icon) next to that version.
4. Confirm the restoration when prompted.

When you restore a version:

- The policy's content is replaced with the content from the selected version.
- The policy status is set to **Draft** so you can review it before re-publishing.
- A **new version is not created** until you publish again. This means restoring is non-destructive -- you can review the restored content and make further edits before publishing.
- The version history is preserved. The restored version and all subsequent versions remain in the history.

> **Important:** Restoring a version does not delete any existing versions. It only changes the current working content of the policy.

---

## Change notes

Change notes are optional but strongly recommended. They serve as a human-readable record of why a version was created. Good change notes make version history useful during audits and compliance reviews.

### Examples of effective change notes

- "Updated TRID disclosure timeline to reflect new 3-day rule per CFPB guidance"
- "Added section on electronic signature requirements"
- "Revised compensation disclosure language per legal review"
- "Annual review -- no substantive changes, reformatted tables"

### Examples of less helpful change notes

- "Updated"
- "Changes"
- "Fix"

---

## Version history and compliance

For mortgage companies subject to regulatory examination, version history provides:

- **Proof of policy existence** -- Demonstrate that a policy was in place before a compliance issue arose.
- **Timeline of changes** -- Show when and why policies were updated in response to regulatory changes.
- **Accountability** -- Each version records who made the change and when.
- **Audit trail** -- An immutable record that versions were not retroactively modified.

---

## Limitations

- Versions are created only on **publish**, not on every save. Saving a draft does not create a version.
- Version content is a **point-in-time snapshot**. There is no line-by-line diff view between versions -- you compare them by viewing each version side by side.
- Version history cannot be deleted. This is intentional to maintain audit integrity.
