# Vercel Deployment Checklist

## Pre-Deployment ✅

- [ ] Database chosen (Vercel Postgres, Supabase, or other)
- [ ] Database connection string ready
- [ ] NEXTAUTH_SECRET generated (`openssl rand -base64 32`)
- [ ] Code pushed to GitHub

## Vercel Setup ✅

- [ ] Project created on Vercel
- [ ] GitHub repository connected
- [ ] Environment variables added:
  - [ ] `DATABASE_URL` 
  - [ ] `NEXTAUTH_SECRET`
  - [ ] `NEXTAUTH_URL` (automatic, but verify)

## First Deployment ✅

- [ ] Initial build succeeds (check build logs)
- [ ] Prisma migrations run automatically
- [ ] Test your deployment:
  - [ ] Home page loads
  - [ ] Can register an account
  - [ ] Can create a profile link
  - [ ] Can submit grievance via share link
  - [ ] Dashboard shows grievances

## Ongoing ✅

- [ ] Database backups enabled (if applicable to your provider)
- [ ] Monitor Vercel analytics
- [ ] Keep dependencies updated

## Debugging Deployment Issues

### Build Fails
1. Check Vercel build logs for specific errors
2. Run locally: `npm run build`
3. Verify all environment variables are set
4. Check database connection

### App Crashes on Production
1. Check Vercel function logs
2. Verify database is running
3. Check NEXTAUTH_URL matches your domain
4. Verify NEXTAUTH_SECRET is set

### Database Queries Fail
1. Verify DATABASE_URL is accessible from Vercel
2. Check Prisma can connect: `npx prisma db execute --stdin < query.sql`
3. Try: `npx prisma db push`

## Support Links
- [Vercel Docs](https://vercel.com/docs)
- [Next.js Deployment](https://nextjs.org/docs/deployment)
- [Prisma Deployment](https://www.prisma.io/docs/orm/prisma-client/deployment)
- [NextAuth.js Deployment](https://next-auth.js.org/deployment)
