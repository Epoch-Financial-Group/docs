# Notes

Notes let you capture conversations, decisions, and context directly on a loan record. Every note is timestamped and attributed to the team member who wrote it, creating an auditable history of communication about each deal.

## Where notes appear

Notes are accessible from two places on the loan detail page:

1. **Notes slide-out sheet** -- Click the **Notes** button in the loan detail page header. A side panel slides out from the right, showing the full note history and the add-note form. This lets you view and add notes without leaving the current tab.

2. **Loan detail data** -- Notes are loaded as part of the loan detail and are available to all tabs.

> **Screenshot placeholder:** *Notes button in the loan detail page header.*

---

## Viewing note history

Notes are displayed in reverse chronological order (newest first). Each note shows:

- **Message** -- The note text
- **Author** -- The name of the team member who wrote the note
- **Timestamp** -- When the note was created, formatted as a full date and time

If no notes have been added yet, a "No notes yet." message is displayed.

> **Screenshot placeholder:** *Notes list showing multiple notes with author names and timestamps.*

---

## Adding a note

### From the slide-out sheet

1. Click the **Notes** button in the loan detail page header.
2. The notes panel slides out from the right.
3. Type your note in the text area at the bottom.
4. Click **Add Note**.
5. The note appears immediately at the top of the list.

### From the notes section

1. Scroll to the notes section (if displayed inline on a tab).
2. Type your note in the text area.
3. Click **Add Note**.

The note is attributed to the currently logged-in user. The text area requires at least one non-whitespace character.

> **Screenshot placeholder:** *Add note form with text area and Add Note button.*

---

## Deleting a note

To delete a note, click the **X** button on the right side of the note card. The deletion takes effect immediately and cannot be undone.

> **Screenshot placeholder:** *Note card with the delete button highlighted.*

---

## How notes are organized

Notes in Keystone use a polymorphic model, meaning the same `Note` table is used across different parts of the system. For loans, each note is linked to a specific loan via the `loanId` field.

Key characteristics:

- **Company-scoped:** Notes are scoped to your company. Only team members within your company can view loan notes.
- **Author tracking:** Each note records which employee wrote it via the `authorId` field. The author's first and last name are displayed alongside the note.
- **Chronological ordering:** Notes are always sorted by creation date, newest first.
- **No editing:** Notes are immutable once created. If you need to correct information, add a new note with the correction.

## Best practices

- Use notes to record borrower communications, underwriter conversations, and internal decisions.
- Add a note when changing a loan's status to explain why the status changed.
- Note any exceptions or unusual circumstances on the loan for future reference.
- Notes serve as an audit trail -- they are especially useful when multiple team members are working on the same loan.
