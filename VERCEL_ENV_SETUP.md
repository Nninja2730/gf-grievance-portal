# 🚀 Vercel Environment Setup

## Your Generated Secret
```
NEXTAUTH_SECRET = cUaNquNp2i62SkwO057iPs+wDJju9iULPY0BTanH+dY=
```
**Save this!** You'll need it in the next step.

---

## Step 1️⃣: Go to Vercel Dashboard

1. Open https://vercel.com/dashboard
2. Find your **gf-grievance-portal** project
3. Click on it to open project settings

---

## Step 2️⃣: Create Vercel Postgres Database

1. Click **Storage** tab at the top
2. Click **Create Database** → **Postgres**
3. Name it: `gf_grievance_portal`
4. Select a region close to you
5. Click **Create**
6. **Copy the connection string** (you'll use this in Step 4)

---

## Step 3️⃣: Add Environment Variables

1. Go to **Settings** tab
2. Click **Environment Variables** (left sidebar)
3. Add these three variables:

### Variable 1: DATABASE_URL
- **Name**: `DATABASE_URL`
- **Value**: Paste the connection string from Step 2
- Click **Add**

### Variable 2: NEXTAUTH_SECRET
- **Name**: `NEXTAUTH_SECRET`
- **Value**: `cUaNquNp2i62SkwO057iPs+wDJju9iULPY0BTanH+dY=`
- Click **Add**

### Variable 3: NEXTAUTH_URL
- **Name**: `NEXTAUTH_URL`
- **Value**: `https://gf-grievance-portal.vercel.app`
- Click **Add**

---

## Step 4️⃣: Deploy!

1. Go to **Deployments** tab
2. You'll see your latest deployment (from GitHub push)
3. It should be deploying now... wait for it to finish (green checkmark)
4. Click the deployment to view your live app! 🎉

---

## ✅ What to Check After Deploy

1. **App loads**: https://gf-grievance-portal.vercel.app
2. **Can register**: Click "Sign Up"
3. **Can create profile**: After registering, create a profile
4. **Get share link**: Copy your share link
5. **Test submission**: Open share link in private/incognito window, submit test grievance

---

## 🔗 Important URLs

- **Your App**: https://gf-grievance-portal.vercel.app
- **Dashboard** (after login): https://gf-grievance-portal.vercel.app/dashboard
- **Share Link** (for girlfriend): https://gf-grievance-portal.vercel.app/share/{your-unique-slug}

---

## ❓ Need Help?

If deployment fails:
1. Check **Deployments** tab → see error logs
2. Verify all 3 environment variables are added
3. Make sure DATABASE_URL connection string is correct
4. Contact Vercel support if database creation fails

If everything is green but app shows error:
1. Wait 30 seconds (cold start)
2. Refresh the page
3. Check browser console (F12) for errors
4. Check Vercel function logs

---

**You're almost there!** 🚀 Go set up those environment variables and watch your app go live!
