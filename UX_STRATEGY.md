# Calitoy Muse — UX & Design Strategy

## Brand Architecture

**Calitoy Muse** is the luxury umbrella brand for evening wear.
**Kurced Wares** is the lingerie line under the Calitoy Muse umbrella.

Both share one Stripe account with brand-level transaction tagging (`brand=calitoymuse` vs `brand=kurced`). Separate reporting, shared infrastructure.

## Sitemap

```
calitoymuse.com/
├── index.html          Homepage
├── shop.html           Collection (filterable: All, Lingerie, Evening Wear, Robes, Accessories)
├── product.html        Product detail template
├── lookbook.html       Editorial gallery (Season One)
├── about.html          Brand story + values
├── contact.html        Contact form + info
├── styles.css          Shared design system
├── sitemap.xml         SEO
└── robots.txt          SEO
```

## Color Palette & Psychology

| Token | Value | Purpose | Psychology |
|---|---|---|---|
| bg-base | #0a0908 | Page background | Near-black warmth, not clinical. Feels intimate, like a dimly lit dressing room |
| accent | #8b1a3a | Primary accent (wine) | Wine red evokes sensuality, luxury, and confidence without being aggressive |
| gold | #c9a96e | Secondary accent | Muted gold signals premium quality, heritage, and craft without ostentation |
| text-primary | #f5f0eb | Body text | Warm off-white, softer than pure white. Reduces eye strain, feels editorial |
| text-muted | #8a7e6f | Captions, meta | Warm gray blends into background for hierarchy without harsh contrast |

**Why dark?** Luxury fashion brands (Saint Laurent, Tom Ford, Bottega Veneta) use dark backgrounds to create intimacy and let product imagery pop. Dark backgrounds reduce visual noise and force focus onto the garments.

## Typography System

| Role | Font | Usage | Psychology |
|---|---|---|---|
| Display | Cormorant Garamond | H1, H2, product names | High-contrast serif with elegant proportions. Signals heritage, craftsmanship, and editorial sensibility |
| Body | Inter | Paragraphs, buttons, forms | Clean, highly legible sans-serif. Modern, neutral, lets the serif do the talking |
| Mono | JetBrains Mono | Prices, tags, SKUs | Technical, precise. Makes prices feel authoritative, not negotiable |

**Hierarchy:** Display serif for emotion, body sans for clarity, mono for data. Three-tier system creates rhythm and prevents typographic monotony.

## UX Psychology by Section

### Hero
- Full-screen height (100vh) creates immersion, no distractions
- Centered text with generous whitespace feels confident, not rushed
- Two CTAs: primary "Shop Collection" (conversion) + secondary "Lookbook" (inspiration). Gives users a choice between buying and browsing
- Gradient overlay from top to bottom guides eye downward, creating natural scroll momentum
- Fade-in animation (1.2s) builds anticipation, feels like a curtain rising

### Product Cards
- 3:4 aspect ratio matches fashion editorial photography proportions
- Hover overlay appears from bottom, creating a "reveal" moment. Mimics the experience of lifting a garment off a rack
- Image scale on hover (1.05x) creates tactile, physical sensation
- Price in gold + JetBrains Mono makes it feel fixed, premium, non-negotiable
- Badge system (New, Sale, Limited) creates urgency without being aggressive

### Brand Story Split
- Left-right split creates a reading rhythm: absorb text, then visual
- Image on right mirrors magazine editorial layout
- "Crafted for those who dress for themselves" positions the brand as empowering, not objectifying

### Lookbook
- Asymmetric grid (tall, wide, square cells) breaks visual monotony
- Hover reveals caption, keeping the clean grid uncluttered
- No prices on lookbook, only inspiration. Separates "dream" from "buy" stages

### Newsletter
- Centered, full-width, bordered section feels like a moment of pause
- Single email field + button, no friction. No name, no preferences
- "Get the next collection first" implies exclusivity and limited access

### Footer
- 4-column grid: brand (wide) + 3 link columns
- Social links as circles with borders, not filled buttons. Feels restrained, not promotional
- Bottom bar with copyright and legal links, standard expectation

### Header
- Fixed, transparent on load, becomes blurred dark on scroll. Maintains brand immersion while providing navigation
- Underline animation on nav hover. Subtle, not flashy
- Cart button with count badge. Always visible, reduces friction to checkout
- Mobile hamburger animates to X. Standard but polished

## Conversion Strategy

1. **Hero CTA** leads to Shop (primary path)
2. **Product card hover** reveals "View" button (one click to product)
3. **Product page** has Add to Cart + Buy Now (two paths: browse more or checkout now)
4. **Related products** on product page (cross-sell)
5. **Newsletter** on every page (capture even if not ready to buy)
6. **Lookbook** creates desire, links back to shop
7. **About page** builds trust, links to shop
8. **Contact** for high-touch / custom orders

## Accessibility

- All interactive elements have focus states (inherited from form/input focus styles)
- `aria-label` on nav, menu toggle, cart button
- Semantic HTML5: header, nav, main, section, article, footer
- Alt text on all images (even gradient placeholders have descriptive alt)
- Color contrast meets WCAG AA (text-primary on bg-base = 12:1)
- `prefers-reduced-motion` respected
- Mobile menu keyboard accessible

## Performance

- No external images (CSS gradients for all placeholders)
- Google Fonts with preconnect + display=swap
- Single shared CSS file (cached across all pages)
- Minimal JS (vanilla, no frameworks)
- No render-blocking scripts

## Stripe Integration Plan

Both brands share one Stripe account:
- `brand=calitoymuse` metadata on all Calitoy Muse transactions
- `brand=kurced` metadata on all Kurced Wares transactions
- Product naming: `CalitoyMuse | Product Name` and `KURCED | Product Name`
- Lookup keys: `calitoymuse_sku` and `kurced_sku`
- Separate reporting by brand metadata field
- Same Stripe credentials in both repos, separate env configs and webhooks
