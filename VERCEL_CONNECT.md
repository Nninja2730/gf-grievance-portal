# 🚀 Connect GitHub to Vercel (5 minutes)

Your code is on GitHub. Now let's connect it to Vercel!

## Step 1: Go to Vercel

1. Open https://vercel.com
2. Click **Sign Up** (or login if you have an account)
3. Choose **GitHub** to sign up with your GitHub account
4. Authorize Vercel to access your GitHub repos

## Step 2: Import Your Repository

1. After login, click **New Project**
2. You should see your repos listed, including **gf-grievance-portal**
3. Click **Import** next to gf-grievance-portal
4. Click **Import** again on the next screen

## Step 3: Configure Project (Optional at this stage)

You'll see a config screen:
- **Project Name**: gf-grievance-portal ✓
- **Framework Preset**: Next.js ✓ (auto-detected)
- **Environment Variables**: You can skip this for now OR add them here

Leave everything else default and click **Deploy**

## Step 4: Wait for Deployment

- Vercel will deploy (takes 1-2 minutes)
- It will FAIL with DATABASE_URL error (this is expected!) ❌
- Don't worry, this is normal

## Step 5: Create Vercel Postgres Database

Once deployment shows as failed:
1. Click on your **gf-grievance-portal** project
2. Click **Storage** tab
3. Click **Create Database** → **Postgres**
4. Name: `gf_grievance_portal`
5. Click **Create**
6. ⏳ Wait for database creation (1-2 minutes)

## Step 6: Add Environment Variables

Once database is ready:
1. Click on the `.env.local` tab in the database panel
2. Copy the entire connection string for `POSTGRES_PRISMA_URL`
3. Go to project **Settings** → **Environment Variables**
4. Add these three variables:

| Name | Value |
|------|-------|
| `DATABASE_URL` | Paste the connection string you copied |
| `NEXTAUTH_SECRET` | `cUaNquNp2i62SkwO057iPs+wDJju9iULPY0BTanH+dY=` |
| `NEXTAUTH_URL` | `https://gf-grievance-portal.vercel.app` |

5. Click **Add** for each one
6. Select **All** for environments (Production, Preview, Development)

## Step 7: Redeploy

1. Go to **Deployments** tab
2. Find your latest deployment (the failed one)
3. Click the **...** (three dots) → **Redeploy**
4. Watch for the green checkmark ✅

## Step 8: Your App is Live! 🎉

Once it's green:
- Your app is at: https://gf-grievance-portal.vercel.app
- Try signing up
- Create a profile
- Share the link with your girlfriend
- Start filing grievances!

---

## 📋 TL;DR Timeline

1. ✅ Push to GitHub (done)
2. ⬜ Go to Vercel.com → New Project → Import GitHub repo
3. ⬜ Deployment fails (expected, no DATABASE_URL yet)
4. ⬜ Click Storage → Create Postgres database
5. ⬜ Add 3 environment variables to project
6. ⬜ Redeploy
7. ⬜ Your app is LIVE! 🚀

**Start at Vercel.com now!**
