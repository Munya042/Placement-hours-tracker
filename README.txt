PLACEMENT HOURS TRACKER PRO

Features:
- Large Start and Stop buttons
- Date and live clock
- Manual previous-shift entry
- Edit and delete shifts
- Break deduction
- Total hours and total days
- CSV export
- JSON backup and restore
- Offline support
- Optional Firebase cloud sync with Google sign-in

DEPLOYMENT
Upload this entire folder to Netlify Drop or another static web host.

FIREBASE SYNC SETUP
1. Create a Firebase project at https://console.firebase.google.com
2. Add a Web app in Project settings > General.
3. Copy these four values into Settings & Sync in the tracker:
   apiKey, authDomain, projectId, appId
4. In Firebase Authentication, enable Google as a sign-in provider.
5. Create a Cloud Firestore database.
6. Replace Firestore rules with the contents of firestore.rules in this package.
7. Add your deployed website domain to Authentication > Settings > Authorised domains.
8. Open Settings & Sync in the tracker and select Save & sign in.

Keep regular JSON backups even when cloud sync is enabled.
