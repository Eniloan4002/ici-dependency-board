# Shared ICI dependency board

Open `/ici-board/` on this repository’s GitHub Pages site. The existing Pages workflow deploys it after main receives a site change.

## Collaboration

The diagram lives in `site/ici-board/index.html`; the dependency register and graph JSON are beside it. Shared completion states live in `documentation/ici-board/progress.json` on main. This file is fetched directly from GitHub every 30 seconds. Reloading does not lose saved changes. Jira is not updated.

To edit, collaborators need repository write permission and a fine-grained GitHub personal access token scoped to this repository with Contents read/write permission. Select Enable shared editing and provide it. The token is kept only in page memory, never in local storage or repository files. Refreshing requires re-entering it. Disable shared editing clears it. Use only the trusted HTTPS Pages deployment. A private repository also requires authenticated reads; do not publish private task data unintentionally.

Each change commits the latest JSON using GitHub’s SHA concurrency check. Conflicts retry up to three times, preserving changes to other tasks; the last accepted update wins for the same task. Errors are displayed and not treated as saved. Branch protections may prevent direct saves; this design requires permission to update this state file on main. Every saved edit is recorded in Git history. Contributors with Contents write access can edit repository content, not just this board; do not grant that permission to untrusted viewers.

Graph/title/dependency edits remain normal repository edits and are published through Pages. The board currently offers shared completion toggles, not an in-page graph editor.
