PLACEMENT HOURS TRACKER — VERSION 2.1

Included:
- Google sign-in
- Firebase/Firestore cloud sync
- Offline local storage
- Start/Stop timer
- Manual previous-shift entry
- Edit/delete shifts
- Break deductions
- Total, weekly, monthly, average and longest-day stats
- Placement target progress
- Search
- CSV export
- Print/PDF export
- JSON backup/restore
- Dark mode
- Installable PWA

FIREBASE
Project configuration is already built into index.html.
Authentication must have Google enabled.
Authorized domains must include: munya042.github.io
Firestore rules should match firestore.rules in this package.

GITHUB
Replace the existing repository files with the files in this package and commit to main.
GitHub Pages should remain configured to deploy from main / (root).

V2.1 FIX:
- Removed redirect fallback for Google sign-in on GitHub Pages.
- Uses popup sign-in only.
- Shows the exact Firebase error code if sign-in fails.
- Bumped service worker cache so the update loads immediately.
