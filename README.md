# 🔥 AtoZ Service Hub — Firebase Setup Guide

## Files in This Project
- `community.html` → Community page (submit & view posts, admin panel)
- `community-posts-loader.js` → Loads approved posts on feature pages
- `latest-jobs.html` → Shows approved "jobs" community posts
- `govt-schemes.html` → Shows approved "schemes" community posts
- `free-courses.html` → Shows approved "courses" community posts
- `daily-updates.html` → Shows approved "updates" community posts
- `service-providers.html` → Shows approved "services" community posts

---

## Step 1: Create Firebase Project

1. Go to https://console.firebase.google.com
2. Click **Add project** → name it `atozservicehub` → Create
3. Left sidebar → **Firestore Database** → **Create database**
4. Choose **Start in test mode** → select region `asia-south1` → Enable

---

## Step 2: Paste Your Firebase Config

Open each of these **6 files** and search for `PASTE_YOUR_apiKey_HERE`, then replace the entire block with your real Firebase config:

1. `community.html`
2. `latest-jobs.html`
3. `govt-schemes.html`
4. `free-courses.html`
5. `daily-updates.html`
6. `service-providers.html`

**Your config to paste:**
```js
firebase.initializeApp({
  apiKey: "AIzaSyDl6q6vSnWIeaY843NOAL5Jpy0PpHjmG5o",
  authDomain: "atozservicehub-d49ab.firebaseapp.com",
  projectId: "atozservicehub-d49ab",
  storageBucket: "atozservicehub-d49ab.firebasestorage.app",
  messagingSenderId: "972035776073",
  appId: "1:972035776073:web:a38c75e2ba3e4c2e406998"
});
```

---

## Step 3: Set Firestore Security Rules

Firebase Console → Firestore → **Rules** tab → paste this → click **Publish**:

```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /community_posts/{postId} {
      allow read: if true;
      allow create: if true;
      allow update: if true;
      allow delete: if true;
    }
  }
}
```

---

## Step 4: Upload All Files to GitHub

1. Go to your GitHub repo
2. Click **Add file → Upload files**
3. Select ALL files from this folder (Ctrl+A)
4. Click **Commit changes**

---

## How It Works

| Action | What Happens |
|--------|-------------|
| User submits post | Saved in Firestore as `pending` |
| You open Admin panel | See all pending posts |
| You click Approve | Status → `approved` in Firestore |
| Feature pages | Automatically show approved posts |
| Permanently stored? | ✅ Yes — stored in Google's servers forever |

---

## Admin Panel

- Go to **Community** page on your website
- Scroll down → click **Admin Login**
- Password: `Krishika@24Achyut@04`
- To change password: open `community.html` → find `ADMIN_PASS` → change it

---

## Where Are Posts Stored?

Firebase Console → **atozservicehub-d49ab** → **Firestore Database** → collection: `community_posts`

---

## Free Tier Limits (More Than Enough)
- 1 GB storage
- 50,000 reads / day
- 20,000 writes / day
- 20,000 deletes / day
