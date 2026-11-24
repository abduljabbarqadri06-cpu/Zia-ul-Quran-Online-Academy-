# Zia-ul-Quran Online Academy — development package

Includes the academy logo, responsive emerald/gold website, admission inquiry form connected to Supabase, email/password login, student portal, admin overview, and SQL database schema with row-level security policies.

## Important
This is a backend-ready development starter, **not a live deployed service**. It cannot store or process real student records until a Supabase project is configured and the SQL schema is applied. Domain, hosting, verified WhatsApp/email, Zoom credentials, and app-store publishing are not included. Never put Supabase service-role keys or Zoom secrets in browser code.

## Setup
1. Install Node.js 20+.
2. Create a Supabase project.
3. In Supabase SQL Editor, run `supabase/schema.sql`.
4. Copy `.env.example` to `.env.local` and fill in the Supabase Project URL and anon/public key from Project Settings → API.
5. In Supabase Authentication URL settings, allow `http://localhost:3000` and your future domain.
6. Run `npm install`, then `npm run dev`; open `http://localhost:3000`.

## First administrator
Create a user through Supabase Authentication → Users. Copy its UUID, then run this SQL in the Supabase SQL Editor:
`update public.profiles set role='admin' where id='PASTE_AUTH_USER_UUID';`
Sign in at `/login`; admins are redirected to `/admin`. Public self-registration is intentionally not enabled in this starter.

## Included routes
- `/` public homepage and inquiry form
- `/login` account login
- `/dashboard` student courses and upcoming Zoom sessions
- `/admin` admin counts and recent inquiries

## Zoom and production
The `class_sessions.zoom_url` field stores private Zoom meeting links for enrolled participants. Automatic Zoom meeting creation requires a Zoom app and server-side OAuth integration; credentials are not included. Before production, add CAPTCHA/rate limiting, test all RLS policies, configure email verification and password recovery, backups, privacy policy, HTTPS, custom domain, and guardian consent procedures for minors.

## Remaining development work
Complete translation of all form and portal content; full CRUD pages for students, teachers, courses, schedules, attendance, reports and fee records; teacher and parent dashboards; Zoom API integration; payment integration if desired; mobile apps; automated tests and production deployment.
