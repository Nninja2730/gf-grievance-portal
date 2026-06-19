# Girlfriend Grievance Portal

> A fun and functional way to submit and track relationship grievances with emojis and apology tracking! 💔

## Features

✨ **Mood-Based Submissions** - Choose from 12+ emojis to express how you're feeling
🎯 **Priority Levels** - Mark grievances as low, medium, high, or urgent
📁 **Categories** - Organize by communication, respect, time, effort, or other
💌 **Expected Responses** - Suggest specific resolutions (apologies, gestures, quality time)
🙏 **Apology Tracking** - Boyfriend can submit apologies with emoji responses
👥 **Share Links** - Generate unique URLs to share grievances without needing an account
📊 **Dashboard** - View all submitted grievances and their status
🎪 **Resolution History** - Track when grievances were resolved

## Tech Stack

- **Frontend**: Next.js 15, React 19, Tailwind CSS 4
- **Backend**: Next.js API Routes
- **Database**: PostgreSQL with Prisma ORM
- **Auth**: NextAuth.js v4
- **Deployment**: Vercel

## Quick Start

### Prerequisites
- Node.js 18+
- PostgreSQL (local or cloud)
- npm or yarn

### Installation

1. Clone the repository:
```bash
git clone <repo-url>
cd gf-grievance-portal
npm install
```

2. Set up environment variables:
```bash
cp .env.example .env.local
```

3. Update `.env.local` with your database URL and generate a secret:
```bash
# Generate NEXTAUTH_SECRET
openssl rand -base64 32
```

4. Initialize database:
```bash
npx prisma migrate deploy
```

5. Run development server:
```bash
npm run dev
```

6. Open [http://localhost:3000](http://localhost:3000)

## Deployment to Vercel

### One-Click Deploy
[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=https%3A%2F%2Fgithub.com%2F[user]%2Fgf-grievance-portal)

### Manual Deployment

1. **Push to GitHub**
```bash
git add .
git commit -m "Initial commit"
git push origin main
```

2. **Create Vercel Project**
   - Go to [vercel.com](https://vercel.com)
   - Click "New Project"
   - Import your GitHub repository

3. **Add Environment Variables**
   - Go to Settings → Environment Variables
   - Add `DATABASE_URL` (from Vercel Postgres, Supabase, or your provider)
   - Add `NEXTAUTH_SECRET` (generate with `openssl rand -base64 32`)
   - Add `NEXTAUTH_URL` (your Vercel deployment URL)

4. **Database Setup** (Choose one)

   **Option A: Vercel Postgres (Easiest)**
   - In Vercel dashboard, go to Storage → Create Database → Postgres
   - Copy the connection string to `DATABASE_URL`

   **Option B: Supabase**
   - Sign up at [supabase.com](https://supabase.com)
   - Create a project and copy PostgreSQL connection string

   **Option C: Other Providers** (Railway, Render, AWS RDS, etc.)

5. **Deploy**
   - Vercel auto-deploys on git push
   - Or manually deploy: `vercel deploy`

## Database Setup

### Local Development

#### Using Docker (Recommended)
```bash
# Start PostgreSQL container
docker run --name gf-postgres \
  -e POSTGRES_PASSWORD=password \
  -p 5432:5432 \
  -d postgres

# Create database
docker exec gf-postgres createdb -U postgres gf_grievance_portal

# Update .env.local
DATABASE_URL="postgresql://postgres:password@localhost:5432/gf_grievance_portal"

# Run migrations
npx prisma migrate deploy
```

#### Native PostgreSQL
```bash
# Create database
createdb gf_grievance_portal

# Update .env.local with your connection string

# Run migrations
npx prisma migrate deploy
```

### Database Migrations

After schema changes:
```bash
npx prisma migrate dev --name descriptive_name
```

On Vercel, migrations run automatically during deployment (configured in `package.json` build script).

## Project Structure

```
├── src/
│   ├── app/
│   │   ├── api/              # API routes
│   │   ├── auth/             # Login/Register pages
│   │   ├── dashboard/        # User dashboard
│   │   ├── share/            # Public grievance submission
│   │   └── page.tsx          # Home page
│   ├── components/           # React components
│   ├── lib/                  # Utilities (auth, prisma)
│   └── types/                # TypeScript types
├── prisma/
│   ├── schema.prisma         # Database schema
│   └── migrations/           # Database migrations
└── public/
    └── emoticons/            # Emoji SVGs
```

## API Endpoints

### Grievances
- `POST /api/message` - Submit a grievance (public or authenticated)
- `PATCH /api/message?id=<id>` - Mark as resolved/submit apology
- `DELETE /api/message?id=<id>` - Delete grievance

### Users & Profiles
- `POST /api/auth/register` - Create account
- `POST /api/person` - Create profile link
- `GET /api/person` - Get all profile links
- `DELETE /api/person?id=<id>` - Delete profile

### Authentication
- `POST /api/auth/[...nextauth]` - NextAuth endpoints
- `POST /api/change-password` - Change password

## Usage

### For Her (Filing Grievances)
1. Go to the link your boyfriend shares (e.g., `yourapp.vercel.app/share/unique-slug`)
2. Write your grievance
3. Select your mood emoji
4. Optionally choose an expected response or type custom one
5. Submit

### For Him (Responding)
1. Sign up at the app
2. Create a profile (get unique share link)
3. Share the link with girlfriend
4. View dashboard to see all grievances
5. Submit apology with emoji response when ready
6. Grievance marked as resolved

## Troubleshooting

### Database Connection Error
- Verify `DATABASE_URL` format is correct
- Ensure database is running and accessible
- Check firewall/security group rules

### "Invalid datasource" Error
- Make sure `.env.local` has `DATABASE_URL` set
- Run `npx prisma generate` to regenerate client
- Restart dev server

### Migrations Failed
- Check Vercel build logs
- Try: `npx prisma db push` to sync schema
- Verify database is running

### NextAuth Issues
- Verify `NEXTAUTH_SECRET` is set
- Verify `NEXTAUTH_URL` matches your domain
- Check NextAuth session configuration in `src/lib/auth.ts`

## Development

```bash
npm run dev      # Start dev server
npm run build    # Build for production
npm start        # Start production server
npm run lint     # Run ESLint
```

## Environment Variables

See `.env.example` for all required variables.

## License

MIT - Feel free to customize for your own relationship! 💕

---

**Made with ❤️ for keeping relationships honest and fun**
