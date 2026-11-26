# Cortex Vault (free version, Supabase)

Free, no card. 1 GB storage, 50 MB per file, 15 uploads per day per account (enforced by the database). Each account sees only its own files.

## Setup (do on a computer if you can; on a phone, switch the browser to "Desktop site")

1. Go to **supabase.com** > Start your project > sign in with GitHub.
2. **New project**: any name, make a database password (save it), pick a region near you, Free plan. Wait ~2 minutes.
3. Left menu **SQL Editor** > New query. Open `setup.sql`, copy ALL of it, paste, tap **Run**. It should say "Success".
4. Left menu **Project Settings** (gear) > **API** (or "API Keys"). Copy:
   - **Project URL** (looks like https://abcd1234.supabase.co)
   - **anon / public key** (long text starting with eyJ...)
5. Open `index.html`, find the block that says `PASTE YOUR SUPABASE DETAILS HERE`, replace `PASTE_SUPABASE_URL` and `PASTE_ANON_KEY` with those two (keep the quotes).
6. In Supabase: **Authentication > URL Configuration**:
   - Site URL: your GitHub Pages link, e.g. https://win883485-ops.github.io/YOUR-REPO/
   - Redirect URLs: add the same link with `**` at the end, e.g. https://win883485-ops.github.io/YOUR-REPO/**
7. Upload the edited `index.html` to GitHub (replace the old one). Wait a minute, open your site.

Sign in with the **email link** (works right away). Free Supabase sends only a few emails per hour, which is fine for you.

## Optional: Google sign-in later
Needs a Google Cloud OAuth client (free, but fiddly): Supabase > Authentication > Providers > Google shows the exact steps and the callback URL to paste into Google Cloud. After it works, set `google:true` in `index.html`.

## Notes
- Deleting moves a file to Trash for 30 days (cleanup runs when you open the site). Deleting does not give back today’s upload count.
- Google search opens in a new tab. "Save from a link" only works when the other site allows it.
- Free projects pause after 1 week with no activity; open the Supabase dashboard and tap Restore if that happens.
