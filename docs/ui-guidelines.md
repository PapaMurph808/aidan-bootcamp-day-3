# UI Guidelines for TODO App

## Component Library

- Use Material UI (MUI) components for all form elements, buttons, dialogs, and lists.

## Color Palette

- Primary color: #1976d2 (blue)
- Secondary color: #ff9800 (orange)
- Background: #f5f5f5 (light gray)
- Text: #212121 (dark gray/black)
- Completed tasks: #9e9e9e (gray, with strikethrough)

### Priority Colors (from design image)

- P1: var(--priority-p1)
- P2: var(--priority-p2)
- P3: var(--priority-p3)

### Priority Selection States

- Selected priority item: `#07F2E6` (use `var(--priority-selected)`).
- Unselected priority item: `#7A7A7A` (use `var(--priority-unselected)`).

Implementation notes:
- Define CSS variables in packages/frontend/src/index.css under `:root` for `--priority-p1`, `--priority-p2`, `--priority-p3`.
- UI components must reference these variables (e.g., `backgroundColor: var(--priority-p1)`) so updates require no code changes.
- Define `--priority-selected` and `--priority-unselected` in `packages/frontend/src/index.css` and apply via `.priority-option` class on priority menu items.

## Button Styles

- Use contained buttons for primary actions (e.g., Add Task, Save)
- Use outlined buttons for secondary actions (e.g., Cancel, Edit)
- Buttons should have a minimum touch target of 48x48px

## Layout

- Responsive design: app must work on mobile, tablet, and desktop
- Use consistent spacing (8px grid)
- Tasks list should be easy to scan and interact with

## Accessibility

- All interactive elements must be keyboard accessible
- Use semantic HTML and ARIA attributes where appropriate
- Ensure sufficient color contrast (WCAG AA compliance)
- Provide visible focus indicators for all focusable elements

## Typography

- Use system font stack or Roboto (if using MUI)
- Headings: bold, clear hierarchy
- Task titles: medium weight, 16-18px
- Descriptions: regular weight, 14-16px

## Animations

- Use subtle transitions for adding, editing, and completing tasks
- Avoid excessive or distracting animations

## Icons

- Use Material Icons for actions (edit, delete, complete, etc.)
