# Client Questions → My Answers

Every question / concern the client raised in the chat, with the answer / clarification I gave (or should give).

---

## Q1 — "Are you able to do what you outlined in WordPress, with or through Oxygen Builder where possible?"
**Answer:** Yes. Everything in the prototype can be built in WordPress. I will use Oxygen Builder as the main builder. Where Oxygen cannot handle a custom gamified interaction (e.g. Star Pick logic, floating action bar popups, MyCred + WooCommerce hybrid checkout), I will add custom PHP/JS/CSS that runs *inside* Oxygen — no theme system needed.

---

## Q2 — "I have all required plugins installed, will provide WP access."
**Answer:** Perfect. I will use the existing plugin stack (MyCred, MarketKing, CheckoutWP, SliceWP, Sassy Social, WP Video Magic). I won't install duplicates. I'll only add custom code where the plugins can't talk to each other cleanly.

---

## Q3 — "I will send the doc with calculations for Treasury (e.g. Dz to €)."
**Action:** Still need this doc — the OneDrive link they shared (`1drv.ms/...`) requires login, so I couldn't open it. I'll ask them to either make it public, send a PDF, or paste the Dz/Tz/PR rules in chat.

Until then, I'm coding it data-driven: **Dz as the primary price**, **€ shown beside it** (the live site currently only shows €, e.g. *PS5 Pro €319–€349*). One config value flips this once the conversion table arrives.

---

## Q4 — "The fundamental aspect of Oxygen is it disables the WP theme system. Elementor relies on the theme system."
**Answer:** Understood. I will not use Elementor. I will keep Oxygen active and build everything inside Oxygen templates. Custom code will be added via Oxygen's Code Block / a small custom plugin — **not** via a theme's `functions.php`.

---

## Q5 — "You can use Gutenberg with Oxygen, for example."
**Answer:** Noted. I'll keep Gutenberg available for content editing where it makes sense (FAQ entries, info popups), and Oxygen for layout/templates.

---

## Q6 — "I think I need a long-time Oxygen user for this."
**Answer (concern to address):** I am comfortable building inside Oxygen. The custom parts (Star Pick, action bar, points logic) are **not Oxygen-specific** — they are PHP/JS that runs on any WordPress site. Oxygen just hosts the layout. I will deliver clean, Oxygen-compatible work and add a 100% refund guarantee if I cannot deliver what I promised.

---

## Q7 — "Will products be added as usual through WP/WooCommerce?"
**Answer:** Yes. All prizes are normal WooCommerce products. No custom post type. We just add custom fields (Dz price, Tz cost, "display only", "linked game", vendor rules) using WooCommerce's existing meta system. The client manages everything from the standard WooCommerce admin.

---

## Q8 — "The 3 shop pages will be a good start. We can use these elements for the rest of the site? E.g. button style, box sections, FAQ."
**Answer:** Yes — that's exactly the plan. Phase 1 deliverables include a **reusable design system** (buttons, cards, sections, FAQ, popups, action bar) so the same look extends to Mint, Account, and game pages later. Saved as Oxygen reusable components / classes.

---

## Q9 — "How long will this take? I may have someone else work on The Mint page in parallel."
**Answer:** ~15 days total. MVP of the 3 pages + action bar in 7–10 days, then 3–5 days for plugin integration testing and polish. The other developer can work on Mint in parallel — no conflict because Mint is a separate template.

---

## Q10 — "Some prizes are display-only (top prize category) and link to the games where they can be won, not for sale."
**Answer:** Handled with a simple product flag (custom field: `prize_type = display_only | redeemable`). 
- `display_only` → button says **"Play to win"** and links to the game page (no add-to-cart).
- `redeemable` → normal **"Redeem with Dz"** button → checkout flow.

---

## Q11 — "Can you ensure best practices for page speed? Site performance is poor."
**Answer:** During development I won't enable aggressive caching/optimization (it blocks live testing). I will follow speed best practices in code:
- Minimal custom CSS/JS (no heavy libraries).
- Defer non-critical scripts.
- Use WebP images (client already does this).
- No bloated page builders for custom sections.

After development, I'll do one optimization pass. The deeper issue is likely **Pressable hosting / plugin overhead** — that needs server-level review separately.

---

## Q12 — "I've been working with several developers. Some parts done, some pending. Everything links to MyCred and the customer account core. You'll do Star Pick; we'll have 3 other games."
**Answer:** Got it. I will only build the **Star Pick** mechanic inside the Treasury. After checking the live site, Star Pick is a **weekly user-selected favourite** ("Choose any item in the Treasury as your weekly Star Pick — and you could win it"), not a separate mini-game. So the work is:
- Action bar button: **set** the current product as Star Pick (on product page) / **view** my current Star Pick (anywhere else).
- One MyCred hook to register the weekly entry.
- Reset weekly via WP-Cron.

The other 3 games are out of scope. All my MyCred hooks will be namespaced `prizino_starpick_*` so other devs' code doesn't collide.

---

## Q13 — "Did you visit the Treasury page when reading the brief? Send order details."
**Answer:** Yes — see `docs/01-project-overview.md` for the scope summary, and `docs/03-todo-list.md` for the exact deliverables. Order will reflect $500, 2 milestones, 15-day delivery.

---

## Q14 — Concern: "That's a blank page, with just header/footer. The 3 icons are Games, Treasury, Account."
**Answer:** Understood — the current Treasury page is empty, which is exactly what we're filling with the 3 new templates. The header icon system stays as-is; the floating action bar I build is a **separate** Treasury-only sticky bar, not a replacement for the main site header.
