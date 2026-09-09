PLACEMENT HOURS — VERSION 5.0

A single-page web app (PWA) for students tracking placement, practicum,
internship or professional-experience hours. No build step, no dependencies:
index.html contains the whole app.

FILES
  index.html      the entire app (markup, styles, logic)
  about.html      what the app does
  privacy.html    privacy policy
  manifest.json   PWA install metadata
  sw.js           service worker (offline app shell)
  firestore.rules Firestore security rules
  icon-192.png    app icon
  icon-512.png    app icon

--------------------------------------------------------------------
WHAT'S NEW IN V5.0
--------------------------------------------------------------------

Built for more than one person
  - Every signed-in account now gets its own separate store on the device,
    plus a separate store for use before anyone signs in.
    In v4 all local data shared one set of keys. On a shared laptop that
    meant person A's records could be uploaded into person B's Firestore
    document the first time B signed in. That can no longer happen.
  - Signing out returns the app to the device store, so the next person
    does not see your hours.
  - Signing in for the first time on a device that already has records asks
    whether to add them to your account or leave them where they are. It
    never moves data on its own. The merge is by record id, so nothing is
    duplicated or lost.
  - First-run setup asks for your name, programme, organisation, required
    hours and dates, with one-tap presets from 100 to 1000 hours. Nothing
    is hard-coded to one programme any more.
  - Your name and student ID appear on the professional report.
  - Settings has a "Delete everything" control.

Interface rebuild
  - Four tabs (Today, Shifts, Supervision, Progress) instead of one long
    scroll. Segmented tabs on desktop, a bottom bar on phones.
  - New progress ring, refined type, spacing, colour and shadows.
  - Toasts and in-app dialogs replace browser alert() and confirm().
  - Proper empty states, paginated shift list, month-by-month calendar.
  - Live "net hours" preview while entering a shift.
  - Dark mode now follows the system by default; Light / Dark / System in
    Settings.
  - Fixed: the shift list rendered .shift-card markup that had no CSS at
    all in v4.1, so recent shifts were completely unstyled.

Under the hood
  - Timer state, milestone history and settings all sync with the cloud
    record, so a shift started on your phone can be finished on a laptop.
  - The service worker no longer caches cross-origin responses (it was
    caching Firebase's SDK), and falls back to the app shell for offline
    navigations.
  - Heavy sections only re-render when their markup actually changes,
    rather than once a second while a timer runs.
  - Settings are normalised to a fixed schema before being stored.

--------------------------------------------------------------------
DATA SAFETY
--------------------------------------------------------------------
v5.0 migrates v3 and v4 local data into the new device store on first
load. The old localStorage keys are left in place untouched as a safety
net. Cloud data stays in the same Firestore user document and the old
document shape is still read correctly.

--------------------------------------------------------------------
RUNNING IT
--------------------------------------------------------------------
Any static host works. To try it locally:

    python3 -m http.server 8000

then open http://localhost:8000

Service workers and Google Sign-In need http://localhost or HTTPS; opening
index.html directly with file:// will not work.

--------------------------------------------------------------------
DEPLOYMENT
--------------------------------------------------------------------
Push to the GitHub Pages branch. Bump the CACHE constant at the top of
sw.js whenever you change the app shell, otherwise returning visitors may
keep the previous version until their cache clears.

For Google Sign-In, the domain must be listed under
Firebase Console -> Authentication -> Settings -> Authorised domains.

--------------------------------------------------------------------
EARLIER VERSIONS
--------------------------------------------------------------------
V4.1  dismissible 8-hour reminder; timer never stops on its own
V4.0  custom icon, insights, 8-week chart, milestone celebration,
      professional report
V3.1  goal/progress presentation, completion forecast, weekly pace
V3.0  redesigned dashboard, milestones, calendar, Google Sign-In,
      Firestore sync, offline storage, CSV, PDF, backup, dark mode
