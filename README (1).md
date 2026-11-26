# Cortex Vault

Private cloud storage with Google sign-in. Each account sees only its own files. Max 15 uploads per day per account (enforced by the security rules, not just the page).

## Setup (about 10 minutes)

1. Go to https://console.firebase.google.com and create a project.
2. **Build > Authentication > Get started > Sign-in method > Google > Enable.**
3. **Build > Firestore Database > Create database** (production mode).
4. **Build > Storage > Get started.** Storage needs the Blaze (pay-as-you-go) plan; you pay for what you store, so "unlimited" costs money as it grows.
5. **Project settings > Your apps > Web (</>)**: register an app, copy the config, and paste it into the `cfg` block at the bottom of `index.html`.
6. Rules: in the console, paste `firestore.rules` into Firestore > Rules and `storage.rules` into Storage > Rules, then Publish.
   (Or with the CLI: `npm i -g firebase-tools && firebase login && firebase use <project-id> && firebase deploy`.)
7. Host it: `firebase deploy --only hosting` (or any static host), then **Authentication > Settings > Authorized domains** and add your site’s domain.

Keep `wallpaper.jpg` next to `index.html`.

## Notes
- Google search opens in a new tab (Google can’t be embedded in a page). "Save from a link" only works when the other site allows it; otherwise download the file and upload it.
- Download links contain a private token. Anyone who has the link can open that one file, so don't post them publicly.
- Deleting moves a file to Trash. Restore it any time, or it is removed for good after 30 days (the cleanup runs when you open the site). Deleting does not give back today’s upload count.
- The daily limit resets at midnight UTC.
