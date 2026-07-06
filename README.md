# S.T.A.R. Designer Purse Bingo & Tricky Tray 2026

Pre-registration page for the S.T.A.R. (Serving To Aid & Restore) Designer Purse Bingo & Tricky Tray fundraiser.

**Event:** Sunday, September 20, 2026 — doors open 12:00 PM, games start 1:00 PM  
**Venue:** American Club of Coplay, 300 Cherry St, Coplay, PA 18037  
**Pricing:** $25 pre-registration · $30 at the door  
**Also featuring:** Tricky Tray, 50/50 Raffle, toiletries donation raffle, food for purchase. No advance seat reservations.

---

## File Structure

```
starfundraiser/
├── index.html          # Main pre-registration page
├── images/
│   ├── bingo-hero.jpg  # Hero section background photo
│   └── STARLogo.svg    # S.T.A.R. organization logo
└── README.md
```

## Setup

1. **Hero image** — save the bingo photo as `images/bingo-hero.jpg`. If the file is missing, the hero falls back to a solid navy background.

2. **Supabase** — open `index.html` and replace the two placeholders near the bottom of the file:
   ```js
   const SUPABASE_URL = 'https://YOUR_PROJECT.supabase.co';
   const SUPABASE_KEY = 'YOUR_ANON_KEY';
   ```

3. **Supabase Table** — create a `bingo_registrations` table. Suggested schema:
   ```sql
   create table bingo_registrations (
     id uuid default gen_random_uuid() primary key,
     name text,
     email text,
     phone text,
     ticket_count int,
     guest_names text,
     total_amount int,
     payment_status text,
     submitted_at timestamptz default now()
   );
   ```

4. **Donorbox** — the success screen embeds a Donorbox campaign at
   `https://donorbox.org/embed/star-purse-bingo-2026`. Update the iframe `src` in
   `index.html` to your actual Donorbox campaign URL for this event.

5. **Deploy** — this is a single static HTML file. Drop the entire folder into any static host:
   - GitHub Pages
   - Netlify (drag & drop the folder)
   - Vercel
   - Any web server

## Features

- $25/person pre-registration with attendee count (1–10) and live total
- Payment after registration via Donorbox (card) or Venmo (@starbethlehem)
- Event highlights: Designer Purse Bingo, Tricky Tray, 50/50 Raffle, toiletries donation raffle
- All submissions saved to Supabase with `payment_status: pending`
- Fully responsive (mobile + desktop)
