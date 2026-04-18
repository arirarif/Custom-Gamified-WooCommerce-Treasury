# Live Site Research — prizino.com

Pulled from the live site on 2026-04-18. Use this as the source of truth for what already exists vs. what I need to build.

## Site Map (confirmed live)
| URL | Purpose |
|---|---|
| `/` | Homepage (currently mostly empty per client) |
| `/Games` | Games hub — currently lists **Win-O Wisps** |
| `/Treasury` | The shop landing page — **this is what I'm rebuilding** |
| `/Treasure/{slug}` | Single product URL pattern (note: singular "Treasure", not "Treasury") |
| `/Mint` | Buy Tz/Dz with BuyCred (next phase, not mine) |
| `/Account` | Customer account "Prizelist" (next phase, not mine) |
| `/Winners` | Past winners |
| `/PR` | Prizino Rewards info |
| `/About`, `/Partners`, `/Care`, `/Legal` | Static pages |
| `/DreamPortal`, `/DM` | "Dream Machine" weekly content |

## Header Currency Display (already on site)
The site header shows 4 live counters:
- **Bag** (cart) → links to `/Games` (odd, but that's current behavior)
- **TZ 0 Tokenz** → links to `/Mint`
- **DZ 0 Dimenz** → links to `/Mint`
- **PR 0** → links to `/PR`

**My floating action bar must match this currency model** (Bag, TZ, DZ, PR all visible).

## Prize Categories (real, use these — not placeholder names)
1. **Tech & Toys** — "Plug in excitement / From consoles to cameras"
2. **In & Outdoors** — "Home, garden, sports / Upgrade your surroundings"
3. **Style & Flex** — "Finer things in life / Win it to bling it"
4. **Mind & Body** — "Brain massage / Cool stuff for wellness"
5. **Pop & Culture** — "Win the moment / Trending and in the spotlight"
6. **Collectionz** — "Trios of Treasures / Collect Prizes... for more surprises"

## Existing Treasury Sections (already on the live page — I'm restyling these, not inventing)
1. **Prize Categories** grid (the 6 above)
2. **Prizino All-Access** — promo block ("For every which way to win...")
3. **Get on the Prizelist!** — email signup form
4. **Star Picks** — *"Choose any item in the Treasury as your weekly Star Pick — and you could win it!"* Currently shows 2 example picks: "Launch Party Nice Photos" (camera accessories), "Enjoy Game High Tech" (game accessories)
5. **Leaving soon** — *"Prizes don't stick around for long... redeem your favourites before they're gone!"* (refresh schedule)

## What "Star Pick" Actually Is (clarified from live site)
> "Choose any item in the Treasury as your weekly Star Pick — and you could win it!"

It is **NOT** a separate game. It's a weekly mechanic on the Treasury:
- User picks 1 item from the Treasury per week as their **Star Pick**.
- That item becomes their weekly entry — they could win it.
- Lives in the Treasury, not on `/Games`.

This changes my action bar plan: the **Star Pick** button on the action bar = "set this item as my Star Pick" (on product page) or "view my current Star Pick" (anywhere else).

## Currency / Pricing Examples Found
- "Sony PlayStation 5 Pro (Variant Product) — Price range: € 319.00 through € 349.00" → prices currently shown in **€** on product cards.
- "Placeholder 1 DM Entry — € 2.99" → also in €.
- Header shows TZ / DZ / PR balances.
- **Conclusion:** the conversion (Dz ↔ €) doc the client mentioned is critical. Until I have it, I'll show **Dz as primary** + **€ as secondary** on product templates (data-driven, easy to flip).

## Existing Game (already built)
- **Win-O Wisps** at `/WOW` — confirms the games pattern. My Star Pick lives in the Treasury, not here.

## Brand / Footer Facts
- Company: **MMD 4 Island Ltd**, Ireland.
- Tagline: **"Play games, win prizes."**
- Compliance: **18+ to play. Play responsibly.**
- Social: Facebook (michaelsvariety), YouTube, Instagram, X, Kick, Tumblr, Twitch, TikTok — all `@Prizino` or `Prizino_`.
- Recurring content: **"Dream Machine"** weekly episodes.

## What Was NOT Accessible
- The OneDrive scope doc (`1drv.ms/...`) — requires login. **Action:** ask client to share as a PDF, public link, or paste the Dz/Tz/PR calculations directly in chat.
- `/About` returned no content (likely empty page like `/`).

## Implications for My Build (changes from the original plan)
1. **Use real category names** in the Explore filters and Shop Home cards.
2. **Star Pick** = a weekly user-selected favourite, not a mini-game. Action bar button reflects that.
3. **Currency display** = Dz primary, € secondary (until conversion doc arrives).
4. **Product URL slug** = `/Treasure/{slug}` (already set in WooCommerce — don't change).
5. **Floating action bar** must mirror the header currency model: **Bag, TZ, DZ, PR + Star Pick + Play + Info + Menu + Countdown**.
6. **"Leaving soon"** section needs a real expiry-date field on products (custom meta + cron-driven refresh display).
7. **"Prizelist" email signup** likely already integrated with their email system — I'll just style the block, not rebuild it.
