# 🔧 Fix: Set DATABASE_URL on Vercel

Your deployment failed because `DATABASE_URL` environment variable is missing.

## ✅ Here's What You Need to Do:

### Step 1: Create Vercel Postgres Database

1. Go to: https://vercel.com/dashboard
2. Click on **gf-grievance-portal** project
3. Click the **Storage** tab (top navigation)
4. Click **Create Database** → Select **Postgres**
5. Fill in:
   - **Database Name**: `gf_grievance_portal`
   - **Region**: Select closest to you
6. Click **Create**
7. ⏳ Wait for it to finish (1-2 minutes)

### Step 2: Copy Connection String

Once database is created:
1. You'll see a card showing your database
2. Click the `.env.local` tab
3. Copy the entire `POSTGRES_PRISMA_URL` line
4. It looks like: `postgresql://user:password@host/db?sslmode=require`

### Step 3: Add Environment Variables

1. Go to **Settings** tab (in your Vercel project)
2. Click **Environment Variables** in left sidebar
3. Add these variables one by one:

#### Variable 1: DATABASE_URL
- **Name**: `DATABASE_URL`
- **Value**: Paste the connection string from Step 2
- **Environments**: Select all (Production, Preview, Development)
- Click **Add**

#### Variable 2: NEXTAUTH_SECRET
- **Name**: `NEXTAUTH_SECRET`
- **Value**: `cUaNquNp2i62SkwO057iPs+wDJju9iULPY0BTanH+dY=`
- **Environments**: Select all
- Click **Add**

#### Variable 3: NEXTAUTH_URL
- **Name**: `NEXTAUTH_URL`
- **Value**: `https://gf-grievance-portal.vercel.app`
- **Environments**: Select all
- Click **Add**

### Step 4: Deploy Again

1. Go to **Deployments** tab
2. Find your latest deployment (from the GitHub push)
3. Click the three dots **...** → **Redeploy**
4. Or wait for Vercel to auto-redeploy when it detects the new env vars
5. ✅ Watch for green checkmark = SUCCESS!

### Step 5: Test Your App

1. Once deployment succeeds, click the deployment link
2. App should load at: https://gf-grievance-portal.vercel.app
3. Try signing up to test
4. If it works, you're live! 🎉

---

## 🆘 Still Getting Errors?

### Error: "Invalid request: `env.DATABASE_URL` should be string"
→ DATABASE_URL not set. Follow Step 3 above.

### Error: "Cannot find module '@prisma/client'"
→ App is starting. Wait 30 seconds and refresh.

### Error: "Connection timeout"
→ Database not running. Make sure Vercel Postgres is created and connection string is correct.

### Build still failing?
1. Check **Deployments** → click failed deployment → see error logs
2. Go to **Settings** → **Environment Variables** → verify all 3 variables exist
3. Try redeploying with **Redeploy** button

---

## 📝 Quick Reference

Your connection string should look like:
```
postgresql://user:password@host.vercel.app:5432/verceldb?sslmode=require
```

Not:
```
postgresql://localhost:5432/gf_grievance_portal
```

The `localhost` one is only for local development!

---

**Need Help?** Check the Vercel docs: https://vercel.com/docs/storage/vercel-postgres

Go create that database now! 🚀
