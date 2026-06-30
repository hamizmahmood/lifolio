# Lifolio — Setup Guide (Supabase + Netlify)

## What you have now

Three files:
- `index.html` — your landing page (welcome, about, coming soon, profile preview)
- `hamiz.html` — your full profile page, lives at `lifolio.netlify.app/hamiz`
- `_redirects` — tells Netlify to map `/hamiz` → `hamiz.html`

Your Supabase project is already wired in (URL + anon key are in the code).

---

## How to upload these to GitHub (so Netlify can deploy from it)

### Step 1 — Create a repository
1. Go to **github.com** → log in
2. Click the **+** icon top-right → **New repository**
3. Name it `lifolio` (or anything)
4. Keep it **Public** or **Private**, doesn't matter
5. Don't check any boxes (no README, no .gitignore) → **Create repository**

### Step 2 — Upload your files
1. On the new repo page, click **"uploading an existing file"** (a blue link)
2. Drag in all 3 files: `index.html`, `hamiz.html`, `_redirects`
3. Scroll down → click **Commit changes**

That's it — no command line needed.

### Step 3 — Connect Netlify to this repo
1. Go to **app.netlify.com** → your `lifolio` site
2. Go to **Site configuration → Build & deploy → Link repository** (or "Link site to Git" if it's not linked yet)
3. Choose **GitHub** → authorize → select your `lifolio` repo
4. Branch: `main` → Build command: leave blank → Publish directory: leave blank (root)
5. Click **Deploy**

From now on, any time you upload a new file or edit one on GitHub, Netlify will **auto-redeploy** in ~30 seconds.

### Editing files later (no Git knowledge needed)
1. Go to your GitHub repo
2. Click the file you want to edit (e.g. `hamiz.html`)
3. Click the **pencil icon** (top-right of the file view)
4. Make your edit → scroll down → **Commit changes**
5. Netlify auto-deploys the update

---

## Your URLs

- **Landing page:** `https://lifolio.netlify.app`
- **Your profile:** `https://lifolio.netlify.app/hamiz`

## Admin login

On your profile page (`/hamiz`), click the small person icon bottom-right → log in with the email/password you created in Supabase → Authentication → Users.

You'll see an "Edit Mode" bar. From there you can:
- Click **Edit Profile** → change name, bio, links, year joined
- Click the ✎ on your avatar → change profile photo
- Click the **+** tile in the photo grid → upload photos (multiple at once)
- In edit mode, hover/tap any photo → **×** appears to delete it

---

## What's already done in Supabase

✅ `profile` table — stores name, username, bio, links, avatar_url, year, photos (as JSON)
✅ Row Level Security — public can read, only logged-in (you) can write
✅ `photos` storage bucket — public read, authenticated upload/delete
✅ Auth user — your login credentials

## Notes
- Supabase free tier: 500MB database + 1GB storage, **no expiry** (unlike Firebase's 90-day pause on inactive free projects)
- If your project ever shows as "paused" after a week of zero activity (Supabase free tier behavior), just log into the Supabase dashboard once to wake it up — your data is never deleted, only paused
- Everything (auth, database, storage) lives under one Supabase project — no other service needed
