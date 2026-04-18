# Prizino Treasury — Project Overview

## What is Prizino?
Prizino is a **gamified prize shop** (multi-vendor) where users:
- Play games using **Tokenz (Tz)** to win prizes.
- Redeem prizes using **Dimenz (Dz)** — the shop currency.
- Earn **Prizino Reward points (PR)** for "meta actions" (referrals, social shares, etc.) → used for bonuses later.

Tagline from the client:
> "Play games with Tokenz/Tz, Get prizes with Dimenz/Dz" — earn Prizino Reward points (PR) for all meta actions.

## What I Am Building (this contract = Phase 1 only)
Just **3 pages** of the Treasury (the shop side):
1. **Shop Home** — landing page of the Treasury.
2. **Explore** — browse all prizes.
3. **Single Product Page** — one prize detail page.

Plus a **Floating Action Bar** (sticky, used across all 3 pages) with:
- **Menu, Star Pick, Play, Info, Bag, Countdown timer**
- Plus the live currency counters that already exist in the site header: **TZ, DZ, PR** (matches `/Treasury` header today).
- Each opens a clean popup.

> **Star Pick clarification (from live site):** Star Pick is **not a game**. It is a weekly mechanic — *"Choose any item in the Treasury as your weekly Star Pick — and you could win it."* The action bar button = set / view the user's current Star Pick.

## What I Am NOT Doing in This Phase
(Client will handle these or hire others later)
- The Mint page (`/Mint` — buy Tz/Dz with BuyCred).
- Customer Account / Prizelist page (`/Account`).
- The 3 other main games (one game — **Win-O Wisps** — is already live at `/WOW`; the others are out of scope).
- Site-wide speed optimization (likely a Pressable hosting issue — separate engagement).
- Any plugin setup (client confirmed all required plugins are already installed).

## Budget & Timeline (agreed)
- **$500 USD**, split into **2 milestones**.
- Delivery: ~15 days (MVP 7–10 days + 3–5 days integration/polish).
- Client provides all WordPress / plugin / hosting access.

## Tech Stack the Client Uses
| Layer | Tool |
|---|---|
| CMS | WordPress |
| Builder | **Oxygen Builder** (client preference — disables WP theme system, dev-friendly) |
| Shop | WooCommerce |
| Points | MyCred (handles Tz, Dz, PR) |
| Multi-vendor | MarketKing |
| Checkout | CheckoutWP |
| Affiliates | SliceWP |
| Social share | Sassy Social Share |
| Video hosting | WP Video Magic + AWS |
| Emails | Amazon SES |
| Hosting | Pressable |

## Build Approach
- Use **Oxygen Builder** as primary (client's hard requirement).
- Add **custom PHP / JS / CSS** only where Oxygen can't cover the gamified logic.
- Use the existing plugin stack first — never replace what's already installed.
- Build reusable components (buttons, cards, FAQ, popups) so the same design system can extend to Mint, Account, and game pages later.
