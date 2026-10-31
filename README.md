# Diet Factory

**Where health meets wellness.** Website for Diet Factory, a healthy food spot in BTM Layout, Bengaluru: protein salads, juices, shakes and bowls with zero added sugar, olive oil only and no palm oil.

It is a single static page with no build step and no backend. Open `index.html` in a browser, or upload the folder to any static host.

## Files

| Path | What it is |
| --- | --- |
| `index.html` | The whole site: markup, styles, menu data and scripts |
| `assets/logo-cream.webp` | Full logo with tagline, cream, for the deep green background (hero, loader) |
| `assets/logo-cream-wordmark.webp` | Logo without tagline, for small sizes (nav, footer) |
| `assets/favicon.png`, `assets/apple-touch-icon.png`, `assets/icon-512.png` | Salad bowl icon from the logo |
| `assets/og-image.jpg` | 1200×630 preview image for WhatsApp, Instagram and other link previews |
| `assets/brand/` | Original logo files and full-size transparent PNGs (cream and green) for print and social |

## Brand colours

Taken from the logo.

| Name | Hex | Used for |
| --- | --- | --- |
| Forest | `#033623` | Logo background, hero, nav, dark bands |
| Cream | `#FCF4E8` | Logo letters, page background |
| Lemon | `#EFE837` | Juice in the cup, buttons, marquee |
| Orange | `#F7A225` | Salad bowl, WhatsApp buttons, highlights |
| Leaf | `#108E2C` | Salad leaves, small accents |
| Tomato | `#D21429` | Cherry tomatoes, small accents |

Fonts: Fredoka for headings and Nunito for text, both from Google Fonts.

## Editing

- **Menu:** edit the `M` object near the bottom of `index.html`. Each item is `[emoji, name, description, price]`.
- **Contact details:** search `index.html` for `910000000000` (WhatsApp) and `+91 00000 00000` (phone).
- **Reviews:** the three quotes in the `#reviews` section are samples.

## Before launch

1. Replace the placeholder WhatsApp number and phone number.
2. Replace the sample reviews with real customer reviews and remove the "Sample reviews" note.
3. Check the opening hours and address.
4. The link preview image points to `https://dietfactory.in/assets/og-image.jpg`. If the site lives on another domain, update the `og:image` tag.
