# AGENTS.md — ebin Website Architecture & Guidelines

Welcome to the **ebin** repository. This document defines the business domain, architecture, design system, coding rules, and backend boundary rules for all AI agents and developers working on this project.

---

## 1. Business Profile
- **Brand Name**: ebin
- **Domain**: Responsible e-waste recycling for households and businesses
- **Geographic Service Area**: **Bengaluru only** (Bruhat Bengaluru Mahanagara Palike - BBMP jurisdiction)
- **Primary Mission**: Divert toxic e-waste from landfills through seamless doorstep pickups and certified KSPCB/CPCB partner recycling facilities.
- **Target Audience**: Bengaluru residents, apartment associations (RWAs), tech workers, and small offices with retired gadgets.

---

## 2. Technical Stack & Commands
- **Framework**: Astro 4.x (Static Site Generation / Zero-JS by default)
- **Styling**: Tailwind CSS with custom `eco` (Fresh Green) and `charcoal` palettes
- **Hosting Target**: Netlify (Forms, Edge CDN, HTTPS)
- **Routing**: Strict trailing slashes enabled (`trailingSlash: 'always'`)

### Common Commands
- `npm run dev`: Starts local Astro development server on `http://localhost:4321`
- `npm run build`: Builds the production-ready static site into `dist/`
- `npm run preview`: Previews the generated static build locally

---

## 3. Strict Architectural Rules & Constraints

### A. Privacy & Contact Restrictions
1. **Never print the owner's email address (`samarth200810@gmail.com`) on any page or HTML source.**
2. All customer communications are received through Netlify forms (`/pickup/` and `/contact/`).
3. Form submissions are dispatched via Netlify Form Notifications configured in the Netlify Dashboard.

### B. Social Media Restrictions
1. **No social media icons or outbound links** anywhere on the website (none exist yet).

### C. URLs & Routing
1. All pages must use explicit directory structure with trailing slashes:
   - `/` (Home)
   - `/pickup/` (Pickup booking form) & `/pickup/success/`
   - `/how-it-works/` (4-stage workflow)
   - `/price-guide/` (Indicative rate list)
   - `/locations/` (Bengaluru drop-off centers with interactive map)
   - `/about/` (Mission, team, and environmental impact)
   - `/contact/` (Inquiry form) & `/contact/success/`
   - `/privacy/` (Privacy policy, linked in footer)

### D. Indicative Pricing Policy
1. All price listings on `/price-guide/` and across the site must be clearly labeled as **"Indicative"**.
2. Final payout depends on physical device inspection, battery health, and cosmetic/functional condition.
3. Pricing values must be confirmed by the business owner before commercial operations begin.

### E. Real Locations Verification
1. Bengaluru drop-off points provided in `/locations/` are researched real community and partner hubs.
2. The business owner must verify operating hours, active bin availability, and site permissions before publishing or advertising.

### F. Backend Boundaries (What Requires a Database or Secret)
1. **Do NOT build**: User login/registration, authentication state, or real-time GPS driver tracking.
2. Any requested feature involving persistent user sessions, driver geolocation streams, payment gateway escrow, or multi-tenant database queries requires an external backend (e.g., Supabase / Node.js API / PostgreSQL + secure API secrets).
3. Current static Astro + Netlify Forms architecture avoids backend maintenance, secrets, and server bills.

---

## 4. Design System & Visual Aesthetics
- **Style Inspiration**: Netflix and Shopify (Bold headlines, cinematic contrast, generous whitespace, strong high-converting CTAs).
- **Logo**: Modern minimalist SVG featuring an eco recycle loop merged with an 'e' glyph in Fresh Green (`#16a34a`) and Charcoal (`#12161f`).
- **Brand Palette**:
  - Fresh Green: `#16a34a` (Primary), `#15803d` (Hover), `#f0fdf4` (Tint)
  - Charcoal: `#12161f` (Primary Dark), `#181e29` (Card Surface), `#090d14` (Deep Background)
  - Neutral / Text: `#ffffff` (White), `#f8fafc` (Off-white), `#94a3b8` (Muted), `#334155` (Slate)
