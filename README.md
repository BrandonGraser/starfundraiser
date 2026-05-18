# S.T.A.R. Golf Classic 2026

Registration page for the S.T.A.R. (Serving To Aid & Restore) Golf Classic fundraiser.

**Event:** Sunday, June 28, 2026  
**Venue:** Green Pond Country Club, 3604 Farmersville Rd, Bethlehem, PA 18020  
**Registration Deadline:** June 10, 2026

---

## File Structure

```
star-golf-classic/
├── index.html          # Main registration page
├── images/
│   ├── hero-bg.jpg     # Hero section background photo
│   └── STARLogo.svg    # S.T.A.R. organization logo
└── README.md
```

## Setup

1. **Supabase** — open `index.html` and replace the two placeholders near the bottom of the file:
   ```js
   const SUPABASE_URL = 'https://YOUR_PROJECT.supabase.co';
   const SUPABASE_KEY = 'YOUR_ANON_KEY';
   ```

2. **Supabase Table** — create a `golf_registrations` table. Suggested schema:
   ```sql
   create table golf_registrations (
     id uuid default gen_random_uuid() primary key,
     registration_type text,
     leader_name text,
     leader_email text,
     leader_phone text,
     teammates jsonb,
     dinner_guest_name text,
     dinner_guest_email text,
     dinner_guest_phone text,
     dinner_guest_count int,
     sponsor_tier text,
     sponsor_name text,
     sponsor_address text,
     sponsor_phone text,
     sponsor_email text,
     total_amount int,
     submitted_at timestamptz default now()
   );
   ```

3. **Deploy** — this is a single static HTML file. Drop the entire folder into any static host:
   - GitHub Pages
   - Netlify (drag & drop the folder)
   - Vercel
   - Any web server

## Features

- Individual golfer, team (foursome), sponsor-only, and dinner guest registration
- Sponsorship tiers: Gold ($950), Silver ($650), Bronze ($500), Hole ($100)
- Live order summary with running total
- All submissions saved to Supabase
- Fully responsive (mobile + desktop)
