# ICI dependency board

Interactive dependency atlas for ICI Local 2.0.

Open https://eniloan4002.github.io/ici-dependency-board/

See [collaboration instructions](documentation/ici-board/README.md) and [dependency register](DEPENDENCIES.md).

To save completion changes, use Enable shared editing with a fine-grained GitHub token scoped to this repository with Contents read/write. Tokens remain in tab memory. Shared progress is read every 30 seconds and saved in Git history. This does not update Jira.

## Sprint planning and task details

Choose Sprint board to create named, dated sprints. Open a card to assign its sprint, change its status, or edit its description, user story and acceptance criteria. Drag cards between To Do, In Progress, Review and Done. Search/module and sprint filters narrow the board. Status/sprint selectors also work without dragging. Done stays aligned with the dependency map; unfinished prerequisites are warnings, not hard movement restrictions.

All 37 tasks include draft stories and acceptance criteria derived from the supplied implementation plan or the additional planning tasks. These are reviewable drafts, not school-approved rules. Metadata, sprint definitions and assignments use the same local queue and optional GitHub sharing as completion. Enable shared editing to publish local changes to the team; without it they remain in this browser. This does not synchronize with Jira. Sprint date/name creation and assignment are supported; automatic sprint start/closure is not implemented.

## Assignees

Open any task in either view and use Assigned to: Linus, Anton, Pauline, Elijah, or Unassigned. The assignee appears on map and sprint cards. Assignment changes use the existing local persistence and optional GitHub shared-editing queue, preserving status, sprint and task details. Anyone using the page can change their local assignment; publishing it for everyone still requires shared editing access.
