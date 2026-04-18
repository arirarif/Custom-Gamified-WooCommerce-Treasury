# Work To-Do List — Minimum, Clean, No Over-Engineering

**Goal:** Deliver exactly what the client paid for ($500, 15 days). Nothing extra. Clean, reusable, easy to extend later.

---

## Milestone 1 — Design System + Shop Home + Explore
**Pay trigger:** ~50% on approval of these.

### 1. Design System (reusable inside Oxygen)
- [ ] Color tokens, typography scale, spacing scale (matches prototype).
- [ ] Reusable Oxygen components: Button, Card, Section, FAQ, Popup/Modal.
- [ ] One small custom plugin scaffold: `prizino-treasury` (holds all custom PHP/JS — no theme edits).

### 2. Floating Action Bar (sticky, all pages)
- [ ] Sticky positioning, mobile-first, respects safe-area on iOS.
- [ ] Items: **Menu, Star Pick, Play, Info, Bag, Countdown Timer**.
- [ ] Live currency chips: **TZ, DZ, PR** (mirrors the existing site header — pulled from MyCred balances).
- [ ] Each opens a clean popup (no page reload).
- [ ] Bag = WooCommerce mini-cart (Dz balance + items).
- [ ] Countdown = configurable end-time from admin (single option, ties to "Leaving soon").

### 3. Shop Home Template (`/Treasury`)
- [ ] Build as Oxygen template, assigned to the Treasury page.
- [ ] Sections (matching what's already on the live page so nothing is lost):
  1. **Prize Categories** grid — use the real 6: Tech & Toys, In & Outdoors, Style & Flex, Mind & Body, Pop & Culture, Collectionz.
  2. **Prizino All-Access** promo block.
  3. **Star Picks** showcase (current week's featured picks).
  4. **Leaving soon** strip (products with an `expiry_date` meta in the next 7 days).
  5. **Get on the Prizelist!** email signup (style only — keep existing form integration).
- [ ] All product data pulled live from WooCommerce.

### 4. Explore Template (product archive)
- [ ] Oxygen template for the WooCommerce product archive (URL stays `/Treasure/...` for singles).
- [ ] Filters: **category** (the 6 real ones), **price range (Dz)**, **prize type** (display-only / redeemable), **vendor** (MarketKing).
- [ ] Card variants: **Redeem with Dz** card vs **Play to Win** card.

---

## Milestone 2 — Single Product + Gamification + Integration
**Pay trigger:** remaining 50% on final approval.

### 5. Single Product Template (`/Treasure/{slug}`)
- [ ] Oxygen single-product template.
- [ ] Show: gallery, **Dz price + € equivalent**, Tz info (if game-linked), vendor name, stock/limit, description, FAQ block, expiry date ("Leaving soon" badge if < 7 days).
- [ ] Two button states based on `prize_type` meta:
  - `redeemable` → **Redeem with Dz** (adds to cart, goes through CheckoutWP).
  - `display_only` → **Play to Win** (links to the game page from `linked_game` meta).
- [ ] **Set as Star Pick** button (calls the action-bar mechanic).
- [ ] Buy-limit enforcement (per-user max, set per product).
- [ ] Free delivery flag display.

### 6. Star Pick Mechanic (weekly favourite, not a game)
- [ ] Custom user meta: `prizino_starpick_product_id` + `prizino_starpick_week`.
- [ ] Action bar popup: shows current week's Star Pick + "change pick" button.
- [ ] **Set as Star Pick** action on product page (one click, AJAX, no reload).
- [ ] WP-Cron weekly reset + winner-eligibility log entry via MyCred.
- [ ] All hooks namespaced `prizino_starpick_*` so other devs' code doesn't collide.

### 7. Plugin Integration & Vendor Rules
- [ ] MyCred: Dz as primary price on cart/checkout, € shown beside, points-only checkout via MyCred Pay-with-Points.
- [ ] MarketKing: vendor-level rules — display vendor on product, enforce per-vendor limits, free-delivery flag.
- [ ] CheckoutWP: ensure custom Dz price flows through correctly.
- [ ] Sassy Social Share: enable on product page.
- [ ] WP Video Magic: support video block in product description (AWS-hosted).
- [ ] SliceWP: leave hooks ready (don't build affiliate UI in this phase).

### 8. QA + Handover
- [ ] Test on: desktop (1440), tablet (768), mobile (375).
- [ ] Test points flow: earn → spend → balance updates everywhere.
- [ ] Test display-only vs redeemable products.
- [ ] One speed pass: defer non-critical JS, confirm WebP usage, no bloat.
- [ ] Short README in `/wp-content/plugins/prizino-treasury/README.md` explaining hooks, options, where to edit.

---

## Out of Scope (do NOT build in this phase)
- The Mint page (BuyCred top-up).
- Customer Account page.
- The 3 other games (only Star Pick).
- SliceWP affiliate dashboards.
- Site-wide performance audit (mention as separate engagement).
- Any redesign of the existing site header/footer.

---

## Before I Start — Need from Client
1. **Dz ↔ € conversion doc** — the OneDrive link needs login. Please re-share as a public link / PDF / pasted in chat.
2. **WordPress admin access** (admin user + URL).
3. **Confirmation** that all listed plugins are installed and licensed.
4. **Confirm** the 6 prize categories (Tech & Toys, In & Outdoors, Style & Flex, Mind & Body, Pop & Culture, Collectionz) are final.
5. **Confirm** Star Pick = weekly favourite mechanic (per the live `/Treasury` page wording), not a separate game.
6. **Approval** of this todo list.
