# Wanderly — Your World, Your Adventure

An interactive, responsive travel application crafted with clean semantic **HTML5**, modern **CSS3**, and modular **Vanilla JavaScript (ES6+)**.

---

## 🌟 Key Features

### 1. Interactive Tour Packages Explorer & Live Search
- **Instant Keyword Search**: Live debounced search across tour titles, subheadings, destinations, and highlighted landmarks (e.g. *"Ring Road"*, *"Aurora"*, *"Ice Cave"*, *"Flåm"*).
- **Multi-Faceted Filtering**:
  - **By Destination**: Iceland, Norway, Scotland, Ireland, The Alps, Lapland, Scandinavia, and Italy.
  - **By Travel Style**: Self-Drive, Guided Small Groups, Scenic Trains & Cruises, and Privately Guided.
  - **By Season**: Winter & Northern Lights vs. Summer & Midnight Sun.
  - **By Duration**: Getaways (1–6 days), 1 Week (7–9 days), and Grand Tours (10+ days).
- **Smart Sorting**: Recommended, Price (Low to High / High to Low), Duration, and Highest Traveler Rating.

### 2. Real-Time Dynamic Currency Switcher
- Switch seamlessly between **INR (₹)**, **EUR (€)**, and **GBP (£)**.
- Automatically re-calculates all tour prices, excursion add-ons, sub-totals, discounts, and final checkout vouchers across the entire site in real-time.
- Persists user currency preferences via `localStorage`.

### 3. Interactive Itinerary Details Modal
- **Day-by-Day Timeline**: Detailed collapsible itinerary cards outlining daily routes, included meals, and handpicked hotels.
- **Inclusions & Exclusions Checklist**: Transparent breakdown of what's included (transport, boutique stays, certified guides, insurances) vs. what's optional.
- **On-the-Fly Booking Customizer**:
  - Departure date selector.
  - Traveler count adjuster (Solo, Standard 2-person, Family 4+).
  - Room category tier selector (*Standard*, *Comfort*, *Superior*).
  - Optional excursion checkboxes (e.g. *Blue Lagoon Comfort Pass*, *Glacier Snowmobile Safari*, *Husky Sledding*).
  - Instant live total price calculation.

### 4. Slide-Over Booking Cart Drawer & Local Storage Persistence
- Right-hand slide-over drawer accessible from any section.
- Itemized display of reserved tours, selected departure dates, traveler counts, and customized excursion add-ons.
- Traveler count increment/decrement with reactive total adjustments.
- **Promo Code Engine**: Test with `EARLYBIRD` (10% discount) or `NORDIC2027` (€200 advance booking credit).
- All cart items and wishlist state automatically persist across page refreshes via `localStorage`.

### 5. Multi-Step Checkout & Printable Booking Voucher
- **Step 1 — Traveler Information**: Full contact form with validation, emergency contact, and special dietary/mobility requests.
- **Step 2 — Secure Payment Simulation**: Encrypted payment form with card validation preview.
- **Step 3 — Official Booking Confirmation Voucher**: Generates a verified booking reference ID (e.g., `NV-2027-XXXXXX`), summary of reservations, and includes a **one-click printable voucher** layout.

### 6. Interactive Wishlist Engine
- Save favorite journeys using the heart button on any tour card.
- Dedicated wishlist badge in the top navigation with quick filtering to saved trips.

### 7. Responsive Nordic Design System
- Authentic color scheme: Arctic Teal (`#2cc9d0`), Deep Ocean Navy (`#102a36`), and Warm Amber (`#e69500`).
- Typography pairing: Classical editorial headings (*Playfair Display*) with modern digital interface typography (*Inter*).
- 100% responsive across desktop, tablet, and mobile viewport sizes.

---

## 📁 File Structure

```
├── index.html          # Main application page with semantic markup
├── styles.css          # Custom responsive CSS design system
├── data.js             # Tour datasets, destinations, itineraries, and currencies
├── app.js              # Controller handling search, filters, modals, cart, and checkout
└── README.md           # Project documentation and submission notes
```

---

## 🚀 How to Run the Application

This project is completely standalone with zero external build tools required.

### Method 1: Direct File Open
Double-click `index.html` in your file explorer or open it in any modern browser (Chrome, Safari, Firefox, Edge). Account registration and the AI assistant require the local server and will not work from a `file://` URL.

### Method 2: Local HTTP Server (Recommended)
From this project directory, run:
```bash
export SUPABASE_URL="https://your-project.supabase.co"
export SUPABASE_ANON_KEY="your-supabase-anon-key"
# Optional: set this only if you use the travel assistant
export OPENAI_API_KEY="your-api-key"
python3 server.py
```
Then navigate to `http://127.0.0.1:8000` in your browser. The server exposes the Supabase project URL and **anon/public key** to the browser; this key is intended for client use. Never put a Supabase `service_role` key in the browser or expose it through the config endpoint.

Optionally set `OPENAI_MODEL` before starting the server to use a different model. Keep server secrets such as `OPENAI_API_KEY` out of browser code and Git.

### User Accounts
Email, Google, and Apple registrations all use Supabase Auth. View registered users in the Supabase project dashboard under **Authentication → Users**.

#### Configure OAuth providers
1. In Supabase, open **Authentication → URL Configuration**. Set the site URL to `http://127.0.0.1:8000` for local testing and add it to the redirect URL allowlist. Add your production HTTPS URL before deploying.
2. In **Authentication → Providers**, enable Google and Apple.
3. Create OAuth credentials with each provider and copy them into the matching Supabase provider settings. Use the callback URL shown by Supabase (usually `https://<project-ref>.supabase.co/auth/v1/callback`) as the provider's authorized redirect/callback URL.
4. Set `SUPABASE_URL` and `SUPABASE_ANON_KEY` in the terminal before starting this server. Restart the server after changing them.

Apple sign-in requires an Apple Developer account and a configured Service ID, Team ID, Key ID, and private key in Supabase. Provider credentials are configured in Supabase and must never be added to the website source. For deployment, use HTTPS and a production-ready server; this built-in Python server listens on this computer only.
