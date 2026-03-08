# Policy Management Overview

Policy management in EpochOS provides a built-in document authoring and distribution system designed for mortgage lending companies. It replaces shared drives, email attachments, and disconnected wikis with a single, searchable policy library that tracks every change and controls exactly who can see what.

---

## Why policy management matters in mortgage lending

Mortgage companies operate under a web of federal, state, and investor regulations. Maintaining up-to-date, accessible policies is not optional -- it is a compliance requirement. Common pain points that EpochOS addresses:

- **Regulatory audits** -- Examiners expect you to produce current policies on demand. EpochOS keeps every policy versioned and timestamped so you can demonstrate exactly what was in effect at any point in time.
- **Distributed teams** -- Loan officers, processors, and branch managers need access to the same procedures regardless of location. A centralized library ensures everyone works from the same playbook.
- **Stale documents** -- When policies live in shared drives, outdated versions linger. EpochOS status management (Draft, Published, Archived) makes it clear which version is authoritative.
- **Access control** -- Not every employee should see every policy. Compensation structures, disciplinary procedures, and executive-level documents can be restricted to specific people or roles.

---

## Key concepts

### Policies

A policy is a single document with a title, rich-text body, and metadata. Policies are the core unit of the system. Each policy has:

- A **title** and auto-generated **slug** used in the URL.
- **Content** authored in the built-in rich text editor or imported from an uploaded file.
- A **status** that controls visibility: Draft, Published, or Archived.
- Optional assignment to a **folder** for organization.
- **Tags** for additional categorization and search.
- A record of who **created** and **last edited** the policy, and when it was **published**.

### Folders

Folders provide hierarchical organization for your policy library. Folders can be nested inside other folders to create a tree structure -- for example, `Compliance > TRID > Disclosures`. Each folder has a name, an optional icon, and a sort order.

### Versions

Every time a policy is published, EpochOS automatically captures a version snapshot. Versions are sequentially numbered and include the content at that point in time, a change note describing what was modified, and a record of who created the version. You can view any previous version and restore it if needed.

### Permissions

Access to policies and folders is controlled through a permission system with three levels:

| Level | Capabilities |
|-------|-------------|
| **Viewer** | Can read the policy but cannot make changes |
| **Editor** | Can read and modify policy content |
| **Admin** | Full control including publishing, deleting, and managing permissions |

Permissions can be assigned to individual employees or to employee roles (such as all Loan Officers or all Branch Managers). They can be set at the individual policy level or at the folder level.

### Document upload

If you already have policies in PDF or Word format, you can upload them directly. EpochOS extracts the text content and converts it into the rich text editor format so you can continue editing in-browser. The original file is preserved and linked to the policy for reference.

### Export

Any policy can be exported back to PDF or DOCX format for distribution outside of EpochOS -- for example, when providing documents to regulators or printing physical copies for a branch office.

---

## Where to find policies

The policy library is accessible from the left-hand sidebar under **Policies**. The URL pattern is `/{company}/policies`.

> **Screenshot placeholder:** *Sidebar navigation with the Policies section highlighted.*

---

## Typical workflow

1. **Create a folder structure** that mirrors your compliance and operational categories (e.g., Compliance, Operations, HR, IT).
2. **Upload existing documents** or create new policies from scratch using the rich text editor.
3. **Set permissions** to control who can view or edit each folder or policy.
4. **Publish** policies to make them available to your team. They start in Draft status until you are ready.
5. **Update and re-publish** as regulations or internal processes change. Each publish creates a new version automatically.
6. **Archive** policies that are no longer active but need to be retained for audit purposes.
