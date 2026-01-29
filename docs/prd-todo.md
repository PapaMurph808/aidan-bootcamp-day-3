# Product Requirements Document (PRD) - TODO App Upgrade

## 1. Overview

We are upgrading the basic TODO app to support due dates, simple priorities, and filters to help users quickly identify urgent work and organize tasks without adding backend complexity. This PRD consolidates requirements confirmed in the 09/16 requirements meeting and the 09/17 Slack follow-up.

Sources:
- 09/16 Requirements Meeting Transcript: [docs/artifacts/09162025-requirements-meeting.vtt](docs/artifacts/09162025-requirements-meeting.vtt)
- 09/17 Slack Conversation: [docs/artifacts/09172025-slack-conversation-export.txt](docs/artifacts/09172025-slack-conversation-export.txt)

---

## 2. MVP Scope

- Add `dueDate` to a task:
  - Optional; stored as ISO `YYYY-MM-DD`.
  - Invalid values are ignored (treated as absent).
- Add `priority` to a task:
  - Enum with values `"P1" | "P2" | "P3"`.
  - Default is `"P3"` when not specified.
- Filters:
  - All: shows all tasks (including completed).
  - Today: shows only incomplete tasks with `dueDate` equal to the current date.
  - Overdue: shows only incomplete tasks with `dueDate` earlier than the current date.
- Storage: local-only; no backend or external storage changes.
- Validation:
  - `title` is required.
  - `priority` must be one of `"P1" | "P2" | "P3"`; otherwise default to `"P3"`.
  - `dueDate` must be a valid ISO date; invalid values are ignored.

---

## 3. Post-MVP Scope

- Visual highlighting for overdue tasks (e.g., red highlight for overdue items).
- Sorting rules in list views:
  - Overdue first.
  - Then by priority (P1 → P2 → P3).
  - Then by due date ascending.
  - Tasks without a due date appear last.
- Priority display enhancements (e.g., color-coded badges: red for P1, orange for P2, gray for P3).

---

## 4. Out of Scope

- Notifications.
- Recurring tasks.
- Multi-user support.
- Keyboard navigation and advanced accessibility.
- External storage or backend changes (remain local-only).
