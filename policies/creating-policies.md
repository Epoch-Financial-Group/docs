# Creating Policies

This page walks through creating a new policy, using the rich text editor to format content, and managing policy status through its lifecycle.

---

## Creating a new policy

1. Navigate to **Policies** in the sidebar.
2. Click the **New Policy** button in the top-right corner of the policy library.
3. Fill in the policy metadata:
   - **Title** (required) -- The name of the policy. A URL-friendly slug is generated automatically from the title.
   - **Folder** -- Optionally assign the policy to an existing folder. You can also move it to a folder later.
   - **Tags** -- Add one or more tags for categorization and search.
4. Write or paste your policy content into the rich text editor.
5. Click **Save** to save the policy as a Draft.

> **Screenshot placeholder:** *New policy form showing the title field, folder selector, and the rich text editor area.*

---

## The rich text editor

EpochOS includes a full-featured rich text editor powered by TipTap. The editor toolbar appears at the top of the content area and provides formatting controls organized into logical groups.

> **Screenshot placeholder:** *Rich text editor toolbar showing all formatting buttons.*

### Text formatting

| Button | Action | Keyboard shortcut |
|--------|--------|--------------------|
| **Bold** | Apply bold weight | Ctrl/Cmd + B |
| **Italic** | Apply italic style | Ctrl/Cmd + I |
| **Underline** | Apply underline | Ctrl/Cmd + U |
| **Strikethrough** | Apply strikethrough | Ctrl/Cmd + Shift + X |
| **Highlight** | Apply yellow highlight background | -- |
| **Code** | Apply inline code formatting | Ctrl/Cmd + E |

### Headings

Three heading levels are available:

- **Heading 1** -- Top-level section heading (largest)
- **Heading 2** -- Subsection heading
- **Heading 3** -- Sub-subsection heading

Click the corresponding heading button in the toolbar, or use the keyboard shortcuts Ctrl/Cmd + Alt + 1, 2, or 3.

### Lists and block elements

| Button | Action |
|--------|--------|
| **Bullet List** | Insert or toggle an unordered (bulleted) list |
| **Ordered List** | Insert or toggle a numbered list |
| **Blockquote** | Insert a blockquote for callouts or citations |
| **Horizontal Rule** | Insert a horizontal divider line |

### Text alignment

Three alignment options are available for headings and paragraphs:

- **Align Left** -- Default alignment
- **Align Center** -- Center the text
- **Align Right** -- Right-align the text

### Links

1. Select the text you want to turn into a link.
2. Click the **Link** button in the toolbar.
3. Enter the URL in the prompt dialog.
4. Click OK. The selected text becomes a clickable link.

To remove a link, place your cursor in the linked text and click the Link button again, then clear the URL and confirm.

### Images

1. Place your cursor where you want the image to appear.
2. Click the **Image** button in the toolbar.
3. Enter the image URL in the prompt dialog.
4. The image is inserted at the cursor position.

> **Note:** Images are referenced by URL. Upload your images to your company's file storage or an image hosting service and paste the URL.

### Tables

1. Place your cursor where you want the table.
2. Click the **Table** button in the toolbar.
3. A 3x3 table with a header row is inserted.
4. Click into any cell to type content.
5. Tables are resizable -- drag column borders to adjust widths.

To add or remove rows and columns, right-click inside the table to access the context menu.

> **Screenshot placeholder:** *A policy document in the editor showing a table, formatted headings, a bulleted list, and highlighted text.*

### Undo and redo

The toolbar includes **Undo** and **Redo** buttons. You can also use Ctrl/Cmd + Z and Ctrl/Cmd + Shift + Z.

---

## Policy status

Every policy has a status that controls its visibility and lifecycle stage:

| Status | Meaning |
|--------|---------|
| **Draft** | The policy is being written or revised. It is visible to users with Editor or Admin permissions but is not yet published. |
| **Published** | The policy is live and visible to all users who have at least Viewer permission. Publishing a policy automatically creates a new version snapshot. |
| **Archived** | The policy is no longer active. Archived policies are hidden from the default library view but can still be accessed by searching or filtering for archived content. They are preserved for audit and compliance purposes. |

### Changing status

- **Draft to Published** -- When your policy is ready, click the **Publish** button. You will be prompted to enter an optional change note describing what was added or modified. A new version is created automatically.
- **Published to Draft** -- If you need to make changes to a published policy, editing it will return it to Draft status until you publish again.
- **Published or Draft to Archived** -- To retire a policy, change its status to Archived. This removes it from the default view without deleting it.

> **Screenshot placeholder:** *Policy detail page showing the status badge and the Publish button.*

---

## Editing an existing policy

1. Navigate to the policy in the library or use search to find it.
2. Click the policy to open the detail view.
3. Click the **Edit** button to open the editor.
4. Make your changes in the rich text editor.
5. Click **Save** to save your changes.
6. When ready to make the changes live, click **Publish**.

---

## Tips for writing policies

- **Use headings** to break policies into scannable sections. This helps employees find the relevant part quickly.
- **Use tables** for structured data like fee schedules, approval thresholds, or role responsibilities.
- **Use highlighting** to call attention to critical compliance requirements or recent changes.
- **Add tags** so policies can be found through multiple categorization paths.
- **Write a descriptive change note** each time you publish so the version history is meaningful during audits.
