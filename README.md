# ICI team tracker

Live page: https://eniloan4002.github.io/ici-dependency-board/

## Shared editing

Anyone with the link can edit assignments, status, task details and sprints without logging in. Changes automatically PATCH the Firebase Realtime Database at `/tracker` using field-level paths, so editing an assignee does not replace someone else’s status change. The most recently accepted update wins for the same field. Views refresh every 15 seconds while visible. Offline edits queue in localStorage and retry on reconnect or Sync now. Browser storage must be available for offline edits to survive closing the page.

## One-time Firebase setup

Project: ici-tracker. Database: https://ici-tracker-default-rtdb.asia-southeast1.firebasedatabase.app

In Realtime Database → Rules, replace the rules with `firebase.rules.json` and Publish. This intentionally allows anyone to read/change the tracker subtree, without sign-in, while leaving other paths locked. Do not store student records, private data or credentials here. Database URLs are public configuration, not secrets. There is no backend server or Firebase SDK dependency. Only the Spark plan is needed; do not link billing or upgrade to Blaze. Free quotas still apply and availability is subject to Firebase service limits. Sites is not used for the live tracker.

Existing browser-local pending edits sync when the updated page opens. The earlier GitHub state file is retained as a legacy snapshot; it is no longer the live store. Its checked snapshot was empty at migration. Refresh/reopen older tabs to stop using the previous GitHub adapter.

## Archive and retire

1. Ask teammates to open the live page and Sync now to upload their local pending changes.
2. Download archive. It includes the latest fetched shared state plus pending edits on the exporting device. Resolve sync errors before treating it as the final team record.
3. Keep the downloaded HTML and a Firebase Data → Export JSON backup in the project documentation. The HTML is self-contained, read-only and works offline, including map, board, task details and sprint filters.
4. Set Firebase rules back to `{ "rules": { ".read": false, ".write": false } }`, then delete the Firebase project when backups are confirmed.
5. Disable GitHub Pages in repository Settings → Pages. Keep the source and final snapshot in GitHub and archive the repository when no further edits are needed.

No active service is needed to view the downloaded HTML. Keep it in more than one location before retiring the services.
