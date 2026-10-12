# Jacob’s University Hub — cloud version

## Deployment
1. In `config.js`, replace `PASTE_YOUR_SB_PUBLISHABLE_KEY_HERE` with the **publishable** key (`sb_publishable_...`) from Supabase. Never use the secret key.
2. Upload `index.html` and `config.js` to the **root** of the existing GitHub repository, replacing the old `index.html`.
3. Vercel redeploys automatically from GitHub. Open the Vercel URL and sign in with the Supabase users you created.
4. Confirm the sidebar says `Saved to cloud ✓` after making a change. Sign in on another device to verify the same data appears.

## Existing data
Before uploading, open the OLD live site, go to Data & backup and download the JSON backup. After updating, sign in and use Data & backup → Import JSON backup to upload that saved file. This replaces the cloud state. **Only import once**, on one device.

## Security and limitations
- This uses the existing `workspaces`, `workspace_members`, `records` tables and RLS policies.
- Only users already granted workspace membership can read/write records.
- Public HTML and `config.js` are visible to visitors; the publishable key is intended to be public. **Never include a secret/service-role key**.
- Current cloud storage is a single shared JSON document. Avoid editing simultaneously on multiple devices (last writer wins). Export backups regularly.
- Cloud synchronisation needs a network connection; watch the save status.
- The Vercel `NEXT_PUBLIC_...` environment variables alone do not configure this static HTML app. `config.js` is required.
