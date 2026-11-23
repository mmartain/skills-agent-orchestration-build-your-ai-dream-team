# Project Pulse implementation plan

## Goal

Create a lightweight, polished static Project Pulse dashboard that helps
contributors quickly see project names, owners, statuses, recent activity,
and priorities.

The finished app should use:

- `app/index.html`
- `app/styles.css`
- `app/project-data.json`
- `.vscode/launch.json`

## Implementation phases

### Phase 1: Define dashboard content and structure

The Coder creates `app/project-data.json` and `app/index.html`.

- `app/project-data.json`
  - Define a top-level `projects` array.
  - Give each project `name`, `owner`, `status`, `recentActivity`, and
    `priority`.
- `app/index.html`
  - Define a clear Project Pulse page structure.
  - Link to `styles.css`.
  - Load `project-data.json` and render the project cards.
  - Include semantic headings, status information, and project summaries.

### Phase 2: Establish the visual design

The Designer owns the experience decisions for `app/styles.css`.

- Create a polished dashboard layout with `.dashboard` and `.project-card`
  selectors.
- Use visible project cards, status badges, clear priority treatment,
  readable spacing, border radius, and shadows.
- Provide an accessible information hierarchy and responsive behavior.
- Maintain strong contrast and a consistent visual style.

### Phase 3: Add the runnable preview

The Coder creates `.vscode/launch.json`.

- Name the launch configuration `Run Project Pulse Dashboard`.
- Serve from the `app` directory.
- Open `http://localhost:<port>/index.html` instead of a server directory.
- Use strict JSON with no comments.

## Agent responsibilities

### Designer

- Own `app/styles.css`.
- Define the dashboard hierarchy, responsive layout, accessibility, status
  and priority treatment, spacing, color, and visual affordances.
- Keep the markup and data structure compatible with the Coder's work.

### Coder

- Own `app/index.html`, `app/project-data.json`, and
  `.vscode/launch.json`.
- Implement the data model and static dashboard behavior.
- Render the project fields consistently and include deterministic CSS hooks.
- Create a valid launch configuration that opens the dashboard.

## Dependencies

1. `app/project-data.json` must use the documented field names before
   `app/index.html` can render project cards reliably.
2. `app/index.html` should establish the selectors and markup used by
   `app/styles.css`.
3. `app/styles.css` depends on the dashboard and project-card structure in
   `app/index.html`.
4. `.vscode/launch.json` depends on the completed `app/index.html` and
   `app/project-data.json`, and must serve from `app/`.
5. The final Orchestrator handoff depends on successful integration of all
   three app files and the launch configuration.

## Parallel work decisions

- Designer and Coder may work in parallel when the Coder first confirms the
  markup and CSS hooks in `app/index.html` and the Designer owns only
  `app/styles.css`.
- The Coder may build `app/project-data.json` independently from the initial
  visual styling.
- Designer work must pause or be adjusted if markup ownership changes.
- `.vscode/launch.json` should be completed after the app structure is stable
  so the launch target and port do not need to change.
- Final integration must be sequential: merge file changes, validate them,
  then create the final handoff.

## Validation expectations

- `app/index.html` contains the exact title `Project Pulse`.
- `app/index.html` references `styles.css` and `project-data.json`.
- The page contains visible `.project-card` elements and a `.dashboard`
  selector is defined in `app/styles.css`.
- `app/styles.css` includes polished responsive styling with
  `border-radius` and `box-shadow`.
- `app/project-data.json` parses as JSON and contains a top-level `projects`
  array.
- Each project includes `name`, `owner`, `status`, `recentActivity`, and
  `priority`.
- `.vscode/launch.json` parses as strict JSON and has a launch configuration
  named `Run Project Pulse Dashboard`.
- The launch configuration serves from `app/` and opens `index.html`, not a
  directory listing.
- The final dashboard presents project information clearly at desktop and
  mobile sizes.
