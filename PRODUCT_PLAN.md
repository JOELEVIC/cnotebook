# cnotebook — Product Plan

## 1. Product direction

cnotebook is an approachable workspace for creating notebooks that combine free-form notes with reusable structure. People can start with a ready-made template, adapt it to their workflow, or begin with a blank notebook. Creating a useful notebook should feel like arranging a few building blocks—not configuring software.

The first release demonstrates this idea with a **Membership & Payments** template. It organizes customer profiles, membership periods, payments, daily notes, and simple reports. It is one example of what notebooks can do, not the product's only supported workflow.

## 2. Product principles

1. **Useful before sign-up:** creating and editing a notebook should not require an account.
2. **No lost work:** save locally as the user types; make cloud-sync state visible and recoverable.
3. **Structure when helpful:** notes are always available, while forms, tables, and summaries are optional building blocks.
4. **Easy to make a copy:** creating a notebook from a template gives the user an independent copy.
5. **Plain language:** use everyday labels such as “Add a note,” “New table,” and “Sync now.”
6. **Trust through clarity:** explain where data is saved, what syncing does, and when an action could replace or merge data.

## 3. Audience and core jobs

### Initial audience

People who currently keep lightweight operational records in documents, spreadsheets, or paper notebooks and want a clearer, more reusable way to work.

### Core jobs

- Keep notes and structured records together.
- Find recent notebooks and add an entry quickly.
- Reuse a starting structure instead of building one from scratch.
- Adapt the structure as a workflow changes.
- Continue working without an account and sync later if desired.
- Export a copy of important information.

## 4. Information architecture

- **Home** — recent notebooks, create actions, and template gallery entry point.
- **Notebook** — pages/sections, notes, tables, and summaries belonging to one notebook.
- **Templates** — ready-made starting points and user-created templates.
- **Account & settings** — sign-in, sync status, exports, and privacy options.

### Content hierarchy

`User → Notebook → Pages/sections → Entries`

`Template → Notebook copy`

A template describes a starting structure. A notebook is the user's working copy. Editing a notebook must not silently change its source template or other notebooks created from that template.

## 5. Main user journeys

### A. Create a notebook without an account

1. Choose **Create notebook**.
2. Choose **Use a template** or **Start blank**.
3. Enter a notebook name; accept a suggested name if provided.
4. Open the notebook and see a clear **Saved on this device** indicator.
5. Add a note or structured item; changes save automatically.

### B. Make a notebook from a template

1. Browse template cards with a short description and preview of included sections.
2. Select **Use template**.
3. Review the sections that will be created and optionally rename the notebook.
4. Create an independent notebook copy.

### C. Add structure to a notebook

1. Choose **Add to notebook**.
2. Pick a building block: **Note**, **Form**, **Table**, or **Summary**.
3. Give it a simple name and configure only the essential fields.
4. Preview, save, and return to the notebook.

The first release should use guided, button-based setup rather than a drag-and-drop page builder.

### D. Sign in and sync existing work

1. Select **Sync across devices**.
2. Sign in or create an account.
3. Explain that this device's unsynced notebooks will be added to the account.
4. If the account already has notebooks, show a review step with clear choices before combining or replacing anything.
5. Show per-notebook sync progress and a final synced state.

Never imply that guest data is already available in the cloud. Do not delete the local copy until the cloud save has succeeded and been verified.

### E. Recover from a sync problem

1. Keep the local copy usable.
2. Display **Not synced** with a concise reason where known and a **Retry** action.
3. Avoid overwriting a newer cloud version silently.
4. If both local and cloud versions changed, offer a review/duplicate option before resolving the conflict.

## 6. Low-fidelity screen plan

### Home

```text
┌──────────────────────────────────────────────────────────┐
│ cnotebook                              Account / Sync     │
│                                                          │
│ Good morning                                             │
│ [ + Create notebook ]     [ Browse templates ]           │
│                                                          │
│ Recent notebooks                                         │
│ ┌─────────────────────┐ ┌─────────────────────┐         │
│ │ Membership &         │ │ Team field notes    │         │
│ │ Payments             │ │ Updated yesterday   │         │
│ │ Updated just now     │ │ [ Open ]            │         │
│ │ [ Open ]             │ └─────────────────────┘         │
│ └─────────────────────┘                                  │
│                                                          │
│ Start with a template                                    │
│ [ Membership & Payments ] [ Blank notebook ] [ See all ] │
└──────────────────────────────────────────────────────────┘
```

Prioritize the create action and recent work. Show local/sync status on notebook cards without making it the dominant visual element.

### Template gallery

```text
┌──────────────────────────────────────────────────────────┐
│ Templates                              [ Back to home ]  │
│ Find a starting point for your notebook.                 │
│ [ Search templates... ]                                  │
│                                                          │
│ ┌──────────────────────────┐ ┌────────────────────────┐ │
│ │ Membership & Payments    │ │ Blank notebook         │ │
│ │ People, periods, payments│ │ Start with a clean page│ │
│ │, notes, and reports.     │ │                        │ │
│ │ [ Preview ] [ Use ]      │ │ [ Create ]             │ │
│ └──────────────────────────┘ └────────────────────────┘ │
└──────────────────────────────────────────────────────────┘
```

Each card should say who it helps and what it contains. Preview before creation; don't require users to understand implementation terms like schemas or modules.

### Notebook

```text
┌──────────────────────────────────────────────────────────┐
│ Home / Membership & Payments       Saved on this device  │
│                                                          │
│ Membership & Payments       [ Share/export ] [ ••• ]     │
│ Keep member records and payment activity together.       │
│ [ + Add ]                                                 │
│                                                          │
│ Overview | Members | Memberships | Payments | Notes       │
│                                                          │
│ Overview                                                  │
│ ┌─────────────────┐ ┌─────────────────┐                  │
│ │ Received        │ │ Active members  │                  │
│ └─────────────────┘ └─────────────────┘                  │
│ Recent activity                            [ View all ]  │
│ ...                                                      │
└──────────────────────────────────────────────────────────┘
```

For the first template, preserve the distinction between money received and amounts expected. Use simple lists and forms before introducing dense dashboards. On small screens, move navigation into a compact menu and keep **+ Add** easy to reach.

### Add menu and simple builder

```text
Add to this notebook
  [ Note ]      Capture free-form information
  [ Form ]      Collect a consistent set of details
  [ Table ]     Track records in rows and columns
  [ Summary ]   Show totals and activity
```

Keep the first builder step to choosing a block and naming it. Add optional field configuration only when relevant to the selected block. Make preview and undo/edit options easy to find.

## 7. First template content

The **Membership & Payments** template should include:

- **Overview:** collected payments, active memberships, outstanding balances, recent activity, and quick actions.
- **Members:** one profile per person, searchable by name and contact details.
- **Memberships:** dated periods with expected amount and a lifecycle status.
- **Payments:** separate transactions linked to a membership; allow partial payments.
- **Daily notes:** free-form operational context.
- **Reports:** date-based summaries with editable notes and saved snapshots.

Important behavior:

- A renewal creates a new dated membership period; it does not overwrite history.
- Payment status is derived from transactions, not manually entered independently.
- Expected amounts and received amounts remain distinct.
- Editing template prices later must not rewrite amounts on existing records.
- Financial corrections must preserve a visible history rather than silently erasing transactions.

## 8. Visual and interaction direction

- Calm, light interface with a neutral background, readable dark text, and one clear blue primary action.
- Strong page titles, generous spacing, subtle dividers, and restrained card styling.
- Use status text and icons as well as color; never depend on color alone.
- Forms should be grouped into short steps with clear labels, helpful examples, and one primary save action.
- Provide keyboard focus states and usable touch targets.
- Responsive from desktop to phone; the main task should remain obvious at every width.
- Autosave feedback should be brief and persistent enough to build trust: **Saving…**, **Saved on this device**, **Syncing…**, **Synced**, or **Not synced**.

## 9. Save, sync, and data expectations

### Guest mode

- Save drafts and notebook data locally, automatically.
- Clearly identify the current device as the only copy.
- Provide export/backup before or alongside account creation.
- Do not present browser storage as encrypted or as a substitute for an account.

### Account mode

- Supabase Auth manages account sign-in.
- Supabase Postgres stores synced notebooks and their content.
- Each user's records must be isolated by database policies.
- Keep local changes until remote persistence succeeds.
- Indicate sync state and handle retry/conflicts explicitly.

### Initial data concepts

- `profiles`
- `notebooks`
- `notebook_members` (defer collaboration unless required; ownership can be represented simply for v1)
- `template_definitions`
- `pages` or `sections`
- `entries`
- `entry_fields` or structured JSON content where appropriate
- `sync_metadata` / revision timestamps

Treat this as a conceptual model only. Settle the precise schema after the user journeys and building-block behavior are validated. Avoid storing an entire shared workspace as one replaceable JSON document; concurrent edits need record-level ownership and update semantics.

## 10. MVP scope

### Include

- Home and recent notebooks.
- Create from the initial template or a blank notebook.
- Rename, open, and export a notebook.
- Add and edit notes and the initial template's structured records.
- Automatic local saving for guests.
- Optional account creation and cloud sync through Supabase.
- Clear save/sync status and safe retry behavior.
- Responsive layouts and basic keyboard accessibility.

### Defer

- Real-time collaboration and shared editing.
- Public template marketplace.
- Custom automation, formulas, and arbitrary permissions.
- Drag-and-drop canvas and fully programmable templates.
- Native mobile apps and offline multi-device conflict merging.
- Payment collection or gateway integrations.
- Complex accounting, tax, or audit workflows.

## 11. Product risks and mitigations

| Risk | Mitigation |
|---|---|
| Guest work is mistaken for cloud-backed data | Show device-only status and explain it at sign-in/export points. |
| Sign-in overwrites existing work | Review the local and cloud inventories before combining; retain recoverable copies. |
| A failed sync loses edits | Keep local data until remote confirmation; make retry explicit. |
| The initial template makes the product feel single-purpose | Lead with notebook/template language and make the blank path visible. |
| The builder becomes too complex | Limit v1 to guided building blocks and validate them with real users. |
| Sensitive operational details are exposed | Use authenticated access and database isolation for cloud data; make exports user-initiated. |

## 12. Success measures

Instrument only what is needed and disclose analytics appropriately. Initial product measures:

- Time from first visit to first notebook created.
- Percentage of new users who add their first note or record.
- Completion rate for template-based notebook creation.
- Guest-to-account conversion and successful first sync rate.
- Sync failures, retries, and unresolved conflict rate.
- Week-one return rate and notebooks with repeated use.

Do not treat sign-up alone as success if people cannot create and keep useful work.

## 13. Design and build sequence

1. Review and refine the Home, Template Gallery, and Notebook wireframes.
2. Prototype guest creation, autosave feedback, and the sign-in/sync transition.
3. Validate that users understand notebook vs. template and local vs. synced.
4. Define the first template's fields, calculations, and report boundaries.
5. Finalize Supabase authentication, ownership, and row-level access model.
6. Build the local-first notebook experience, then add sync and recovery behavior.
7. Test responsive layouts, keyboard use, export/restore, and interrupted sync.

## 14. Decisions to validate before implementation

- Should a signed-in user be able to create and edit while offline in the first release, or is local-first limited to guests?
- Should notebook creation from a template include an optional setup step for renaming sections and choosing which ones to include?
- What should be exportable in v1: one notebook at a time, or all notebooks together?
- Are reports only saved snapshots, or should users also be able to recalculate an old report from current records?
- Should the first release allow multiple people to access one notebook, or remain single-owner?
