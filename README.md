# Diet Factory

**Where health meets wellness.**

This is the website for Diet Factory, a healthy food and juice spot in BTM 1st Stage, Bengaluru. It sells fresh juices, shakes and smoothies, toasts, bowls, salads and hot teas, made with zero added sugar, olive oil only, no palm oil and air frying only.

The site is one static page. It has no build step, no framework and no backend. Visitors can browse the full menu, build an order with + and − buttons, and send that order to Diet Factory on WhatsApp as a ready-made message.

**Live site:** https://dietfactory.in/ (main address). The same site is also published on GitHub Pages at https://dietfactorydotin.github.io/DietFactory/.

## Files

| Path | What it is |
| --- | --- |
| `index.html` | The whole site: markup, menu, styles (inline `<style>`) and scripts (inline `<script>`) |
| `404.html` | Branded "page not found" page that GitHub Pages shows for any unknown address |
| `.nojekyll` | Empty file that tells GitHub Pages to serve the files as they are, without Jekyll |
| `assets/logo-green.webp` | Full green logo with tagline, for white backgrounds (also used by `404.html`) |
| `assets/logo-green-wordmark.webp` | Green logo without tagline, used in the header |
| `assets/logo-cream.webp` | Full cream logo, for the green `#033623` background only (footer) |
| `assets/logo-cream-wordmark.webp` | Cream logo without tagline, for small sizes on green |
| `assets/icon-cup.webp`, `assets/icon-bowl.webp` | The juice cup and salad bowl from the logo. Use them on green backgrounds only |
| `assets/favicon.png`, `assets/apple-touch-icon.png`, `assets/icon-512.png` | Browser and home-screen icons |
| `assets/og-image.jpg` | 1200×630 preview image for WhatsApp, Instagram and other link previews |
| `assets/brand/` | Original logo files for print and social media |

All paths in the site are relative (`assets/...`), so it works at `/DietFactory/` on GitHub Pages and on any other host.

## Brand colours

Green and white lead. The other logo colours are only small accents.

| Name | Hex | Used for |
| --- | --- | --- |
| Diet Factory green | `#033623` | The logo green. Header lines, hero, menu panels, buttons, text |
| White | `#ffffff` | Page background, white menu panels, text on green |
| Green tint (dark) | `#0b4a32` | Cards on green sections |
| Green tint (light) | `#e9f1ec`, `#f4f8f5` | Soft backgrounds, contact tiles, form fields |
| Lemon | `#efe837` | Small accents only: the hero underline, "from ₹" stickers, item count badge |
| Orange, Leaf, Tomato | `#f7a225`, `#108e2c`, `#d21429` | Small accents inside the flat illustrations only |

Fonts (Google Fonts): **Fredoka** for headings and **DM Sans** for body text.

## How to edit the menu

The menu is plain HTML inside `index.html`, so it also shows when JavaScript is off. Search the file for `<div class="stack">`. Each category is an anchor plus a panel:

```html
<span class="anc" id="juices"></span>
<section class="pn pw" aria-labelledby="h-ju"><div class="wrap">
<header class="ph"><p class="pnum">01 / 06 · 11 juices</p><h3 id="h-ju">Juices</h3>
<div class="ill" aria-hidden="true">…illustration…<span class="from">from<b>₹59</b></span></div></header>
<div class="bd two">
<div><h4>Fresh juices</h4><ul>
<li><span>Papaya</span><b>₹59</b></li>
…
</ul></div>
…
```

- **One item** is one line: `<li><span>Item name</span><b>₹price</b></li>`.
- **Change a price:** edit the number inside `<b>`. The order builder reads the price from there, so there is nothing else to update.
- **Item with no price yet:** use `<li><span>Grilled Chicken Toast</span><b class="ask">Ask us</b></li>`. It can still be added to an order, and the WhatsApp message says "price to confirm".
- **Diet Factory signature badge:** put the small logo inside the name, after the text: `<li><span>Skin Glow<img class="sig" src="assets/logo-green-wordmark.webp" width="520" height="276" alt="Diet Factory signature" loading="lazy"></span><b>₹119</b></li>`. On green panels (`pg`) use `assets/logo-cream-wordmark.webp` (height `275`) instead. The name must stay the first text in the `<span>`.
- **Optimum Nutrition tag:** add `<small class="onb">Optimum Nutrition</small>` after the badge, as on Signature Protein Shake.
- **Add or remove an item:** copy or delete an `<li>` line. Every item name must be unique, because the saved basket stores items by name.
- **Then update the counts and "from" prices** that are typed in by hand:
  - the category count in the sticky bar, for example `Juices<span aria-hidden="true">11</span>` inside `<nav aria-label="Menu sections">`
  - the panel label, for example `<p class="pnum">01 / 06 · 11 juices</p>`
  - the lowest price sticker, for example `<span class="from">from<b>₹59</b></span>`
  - the line `35 items · 6 categories · prices in ₹` above the menu
- **Juices** has two groups (`Fresh juices`, `Blends`), each a `<div><h4>…</h4><ul>…</ul></div>`. Other categories use one `<div class="bd"><ul>…</ul></div>`.
- **New category:** copy an `anc` + `section` pair, give it a new `id`, and add a matching link to the sticky bar (`<li><a href="#new-id">Name<span aria-hidden="true">N</span></a></li>`). Panels alternate white (`pw`) and green (`pg`).

## Contact details

| What | Value | Where it appears in `index.html` |
| --- | --- | --- |
| Phone | +91 63622 48157 | `tel:+916362248157` links (header, hero, how to order, visit, footer) |
| WhatsApp | same number | `https://wa.me/916362248157` links and the `WA` constant in the script |
| Email | info@dietfactory.in | `mailto:` links in visit and footer |
| Address | Diet Factory, 12th Cross, Maruthi Nagar, BTM 1st Stage, Madiwala, Bengaluru 560068 | Visit section, footer, JSON-LD block in `<head>` |
| Instagram | https://www.instagram.com/dietfactory.in/ | Visit, footer, JSON-LD `sameAs` |

If the number changes, search and replace both `916362248157` and `63622 48157`, in `index.html` and `404.html`.

Opening hours are deliberately not shown anywhere on the site.

## How ordering works

1. Every menu item has a **+** button. After the first tap it turns into **− quantity +**.
2. The basket button in the header shows the item count once something is added (and the running total on larger screens). On phones, a bar with the total, item count and "Review order" also slides up from the bottom.
3. "Review order" opens a panel with quantities, line totals, the total, an optional name and an optional "Pickup or delivery address/notes" field, plus a "Clear order" link.
4. **Send order on WhatsApp** opens `https://wa.me/916362248157?text=…` with the order written out:

   ```
   Hi Diet Factory! I'd like to order:
   • 2 × ABC — ₹178
   • 1 × Grilled Chicken Toast — ₹199
   Total: ₹377
   Name: ...
   Notes: ...
   ```

5. The visitor presses send in WhatsApp, and Diet Factory confirms the order on chat.

The basket is saved in the visitor's own browser (`localStorage`, key `df-order-v1`), so it survives a page reload. Nothing is sent to any server. The menu search, the "How to order" chat preview (which switches to the visitor's real order) and the sticky category bar all run in the same inline script.

## Publishing

Every push to the `main` branch publishes the site in two places automatically:

- **Vercel** (the `diet-factory` project) builds every push to `main` as the production site. Connect `dietfactory.in` to that project under **Vercel > Project > Settings > Domains**.
- **GitHub Pages** builds every push to `main` (Settings > Pages > Source: **Deploy from a branch**, Branch: **main**, folder **/ (root)**) and serves it at https://dietfactorydotin.github.io/DietFactory/.

Connect `dietfactory.in` to only one of the two. If it should be GitHub Pages instead of Vercel, add the domain under **Settings > Pages > Custom domain** and point the domain's DNS at GitHub Pages.

The canonical URL, Open Graph and Twitter preview tags and the Restaurant JSON-LD in `index.html` all point at `https://dietfactory.in/`. Search engines and link previews treat that as the main address, even when the page is opened from the GitHub Pages or Vercel address. If the main address ever changes, search and replace `https://dietfactory.in/` in `index.html` and `404.html`.

All asset paths are relative, so the same files work at `/` (Vercel, dietfactory.in) and at `/DietFactory/` (GitHub Pages). `404.html` works out which of the two it is on by itself.
