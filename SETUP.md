# Girlfriend Grievance Portal - Setup Guide

## Local Development Setup

### Prerequisites
- Node.js 18+ installed
- npm or yarn

### Step 1: Install Dependencies
```bash
npm install
```

### Step 2: Database Setup (Choose One)

#### Option A: PostgreSQL Local (Recommended for local dev)
1. Install PostgreSQL locally or use Docker:
```bash
docker run --name gf-postgres -e POSTGRES_PASSWORD=password -p 5432:5432 -d postgres
```

2. Create database:
```bash
createdb gf_grievance_portal
```

3. Update `.env.local`:
```
DATABASE_URL="postgresql://postgres:password@localhost:5432/gf_grievance_portal"
NEXTAUTH_SECRET="your-random-secret-key-min-32-chars"
NEXTAUTH_URL="http://localhost:3000"
```

4. Run migrations:
```bash
npx prisma migrate deploy
```

#### Option B: SQLite (Simplest for local testing)
Change `prisma/schema.prisma`:
```prisma
datasource db {
  provider = "sqlite"
  url      = env("DATABASE_URL")
}
```

Update `.env.local`:
```
DATABASE_URL="file:./prisma/dev.db"
NEXTAUTH_SECRET="your-random-secret-key-min-32-chars"
NEXTAUTH_URL="http://localhost:3000"
```

Run migrations:
```bash
npx prisma migrate deploy
```

### Step 3: Run Development Server
```bash
npm run dev
```

Open [http://localhost:3000](http://localhost:3000) in your browser.

---

## Vercel Deployment

### Step 1: Set Up PostgreSQL Database

Choose one option:

#### Option A: Vercel Postgres (Easiest)
1. Go to [Vercel Dashboard](https://vercel.com/dashboard)
2. Create/select your project
3. Go to **Storage** tab → **Create Database** → **Postgres**
4. Copy the connection string

#### Option B: Supabase
1. Go to [Supabase](https://supabase.com)
2. Create a new project
3. Go to **Settings** → **Database** → copy connection string

#### Option C: Other PostgreSQL Providers
- Railway
- Render
- AWS RDS
- PlanetScale (MySQL - may require schema updates)

### Step 2: Configure Environment Variables on Vercel

1. Go to your Vercel project settings
2. **Settings** → **Environment Variables**
3. Add these variables:

```
DATABASE_URL = [Your PostgreSQL connection string]
NEXTAUTH_SECRET = [Generate with: openssl rand -base64 32]
NEXTAUTH_URL = https://your-vercel-deployment-url.vercel.app
```

### Step 3: Deploy

```bash
# Push to GitHub/GitLab
git push origin main

# Vercel will auto-deploy on git push
# Or manually deploy:
npm install -g vercel
vercel
```

### Step 4: Run Database Migrations on Vercel

After first deployment:
```bash
npx prisma migrate deploy
# Or if migrations aren't in prod yet:
npx prisma db push
```

You can also add a **Build Script** to auto-migrate:

Update `package.json` build script:
```json
{
  "scripts": {
    "build": "prisma migrate deploy && next build",
    "dev": "next dev"
  }
}
```

---

## Generate NEXTAUTH_SECRET

Run this in your terminal:
```bash
openssl rand -base64 32
```

Or use Node.js:
```bash
node -e "console.log(require('crypto').randomBytes(32).toString('hex'))"
```

---

## Development Workflow

1. **Create features** → Test locally
2. **Database schema changes** → Run `npx prisma migrate dev --name feature_name`
3. **Commit migrations** to git
4. **Push to main** → Vercel auto-deploys
5. **Migrations run automatically** on production

---

## Troubleshooting

### Connection Error
- Check `DATABASE_URL` format
- Verify database is running
- Check firewall/security group rules

### Build fails on Vercel
- Check build logs in Vercel dashboard
- Run `npm run build` locally to test
- Ensure all environment variables are set

### Database migration issues
- Run locally first: `npx prisma migrate dev`
- Check migration files are committed
- Use `npx prisma db push` if migrations are stuck

---

## Features

✅ Grievance submission with mood emojis
✅ Priority levels (low, medium, high, urgent)
✅ Categories (communication, respect, time, effort, other)
✅ Expected response prompts
✅ Apology tracking with emoji responses
✅ Dashboard for viewing all grievances
✅ Mark grievances as resolved
✅ Share unique links with partner

---

## Tech Stack

- **Frontend**: Next.js 15, React 19, Tailwind CSS
- **Backend**: Next.js API Routes
- **Database**: PostgreSQL (Prisma ORM)
- **Auth**: NextAuth.js
- **Deployment**: Vercel
