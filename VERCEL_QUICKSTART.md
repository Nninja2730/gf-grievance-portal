# Vercel Deployment Quick Start

## 🚀 Get Your App Running on Vercel in 5 Minutes

### Step 1: Choose Your Database

Pick one:
- **Vercel Postgres** (easiest) - Just create it in your Vercel dashboard
- **Supabase** (free tier available) - Go to supabase.com
- **Railway, Render, AWS RDS** - Use any PostgreSQL provider

### Step 2: Prepare Your Connection String

Once you have a PostgreSQL database, get your connection string:
```
postgresql://user:password@host:port/database
```

### Step 3: Generate Your Secret

```bash
openssl rand -base64 32
```
Copy this value.

### Step 4: Connect to Vercel

1. Go to [vercel.com](https://vercel.com)
2. Click **New Project**
3. Import your GitHub repository
4. Go to **Settings** → **Environment Variables**
5. Add these variables:

| Variable | Value |
|----------|-------|
| `DATABASE_URL` | Your PostgreSQL connection string |
| `NEXTAUTH_SECRET` | The secret from Step 3 |
| `NEXTAUTH_URL` | `https://your-project.vercel.app` |

### Step 5: Deploy!

Click **Deploy** and wait about 1-2 minutes.

### Step 6: Test It

Once deployed:
1. Visit your app URL
2. Register as the boyfriend
3. Create a profile → Get your share link
4. Share the link with your girlfriend
5. Submit a test grievance!

---

## 📱 Using Your App

**Girlfriend side:**
- Open the share link
- Write a grievance
- Pick a mood emoji
- Submit (no login needed!)

**Boyfriend side:**
- Sign up at the main site
- View all grievances in dashboard
- Click on grievances to respond with apologies
- Emojis let you express remorse 😅

---

## 🆘 Troubleshooting

### "Build failed"
Check Vercel logs for the error. Usually:
- Missing environment variable
- Database connection issue
- Invalid secret format

### "Can't connect to database"
- Verify `DATABASE_URL` is correct
- Check your database is running
- Allow connections from Vercel (whitelist 0.0.0.0/0 if needed)

### "Page won't load after deploy"
- Wait 30 seconds (first load can be slow)
- Check browser console for errors
- Verify all 3 environment variables are set

---

## ✨ Features Working Out of the Box

✅ Share grievance links (no registration needed)
✅ Multiple mood emojis
✅ Priority levels & categories
✅ Dashboard to view all grievances
✅ Apology submission with emoji
✅ Resolution tracking

---

**Questions?** Check SETUP.md or DEPLOYMENT.md for detailed guides.
