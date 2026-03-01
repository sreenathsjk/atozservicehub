# 🔥 Firebase Setup Guide — AtoZ Service Hub

## Files Changed
- `community.html` → now reads/writes Firestore
- `latest-jobs.html` → shows approved "jobs" community posts
- `govt-schemes.html` → shows approved "schemes" community posts
- `free-courses.html` → shows approved "courses" community posts
- `daily-updates.html` → shows approved "updates" community posts
- `service-providers.html` → shows approved "services" community posts
- `community-posts-loader.js` → shared Firestore loader (NEW FILE)

---

## Step 1: Create Firebase Project

1. Go to https://console.firebase.google.com
2. Click **Add project** → name it `atozservicehub` → Create
3. Left sidebar → **Firestore Database** → **Create database**
4. Choose **Start in test mode** → select region `asia-south1` → Enable

---

## Step 2: Get Your Config

1. Gear icon ⚙️ → **Project Settings** → scroll to **Your apps**
2. Click **</>** (Web) → register app → copy the `firebaseConfig` object

---

## Step 3: Paste Config in 2 Files

Open these files and find `PASTE_YOUR_apiKey_HERE` etc.:

### File 1: `community.html`
Search for this block (around line 400):
```js
const firebaseConfig = {
  apiKey:            "PASTE_YOUR_apiKey_HERE",
  ...
};
```
Replace with your real values.

### File 2: `community-posts-loader.js`
Same config block at the top — paste your values there too.

---

## Step 4: Set Firestore Security Rules

Firebase Console → Firestore → **Rules** tab → paste:

```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /community_posts/{postId} {
      allow read: if resource.data.status == "approved";
      allow create: if request.resource.data.keys().hasAll(['name','cat','title','body','status','date'])
                    && request.resource.data.status == "pending";
      allow update: if true;   // tighten later with Firebase Auth
      allow delete: if true;   // tighten later with Firebase Auth
    }
  }
}
```

Click **Publish**.

---

## Step 5: Enable CORS for GitHub Pages

Firebase Console → Firestore → **Rules** already handles this.
For the CDN JS modules — no extra config needed, they're served by Google.

---

## Step 6: Upload to GitHub

Replace your existing files on GitHub with all files from this zip.
Make sure `community-posts-loader.js` is in the **root** of your repo
(same folder as index.html).

---

## How It Works Now

| Action | What Happens |
|--------|-------------|
| User submits post | Saved to Firestore with `status: "pending"` |
| Admin opens panel | Sees all pending posts |
| Admin clicks Approve | `status` → `"approved"` in Firestore |
| Feature pages | Show only approved posts for their category |
| Data loss? | Never — Firestore stores permanently for free |

---

## Admin Password
Current password: `Krishika@24Achyut@04`
To change it, edit line in `community.html`:
```js
const ADMIN_PASS = 'your-new-password';
```

---

## Free Tier Limits (more than enough)
- 1 GB storage
- 50,000 reads/day
- 20,000 writes/day
- 20,000 deletes/day
