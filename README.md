# coconutbaby.com

A static site. No build step, no dependencies, no framework. Edit the HTML, push, and it is live in about a minute.

```
index.html                   home — magazine front page, lead story + article grid
coconut-oil-baby-skin.html   skin oil
balms-and-lotions.html       balms, lotions, diaper creams
bath-and-washing.html        bath time
baby-massage.html            baby massage
coir-nursery.html            coconut fiber (coir) nursery goods
diapering.html               diapering
teething.html                teething
feeding-and-weaning.html     coconut in feeding
baby-clothes.html            baby clothes
style.css                    all styling (palette is set at the top)
mascot.svg  favicon.svg      the mascot and browser icon
*.jpg                        five article photos, 1200px wide
CNAME                        tells GitHub which domain to serve
README.md                    this file
```

Flat structure, no subfolders — every file uploads from an iPad in one drag.

---

## Put it online (about 20 minutes, once)

### 1. Make the repository

On GitHub, create a new **public** repository named `coconutbaby.com`.

Upload every file in this folder: **Add file → Upload files**, then drag them all in at once.

### 2. Turn on Pages

**Settings → Pages**. Source: `Deploy from a branch`. Branch: `main`, folder `/ (root)`. Save.

Wait a minute, then check the `github.io` URL it gives you. The site should be there.

### 3. Point the domain at it

In your registrar's DNS panel, delete any existing `A` records for `@` and any `CNAME` for `www`. Then add:

| Type | Name | Value | TTL |
|---|---|---|---|
| A | @ | 185.199.108.153 | 1 hour |
| A | @ | 185.199.109.153 | 1 hour |
| A | @ | 185.199.110.153 | 1 hour |
| A | @ | 185.199.111.153 | 1 hour |
| CNAME | www | <your-github-username>.github.io | 1 hour |

Those four IPs are GitHub's. If the site does not come up, check GitHub's current list in their Pages documentation.

### 4. Tell GitHub about the domain

**Settings → Pages → Custom domain** → enter `coconutbaby.com` → save. The `CNAME` file already contains it. Wait for the DNS check to pass, then tick **Enforce HTTPS**. Do not skip that.

---

## The Amazon Associates side

Everything on this site is monetised through the Associates account and nothing else. There are no other affiliate networks, no direct cart, no sponsored placements.

**1. Add the domain to your Associates account before the site goes live.** In Associates Central: **Account Settings → Manage Your Websites**. Amazon requires every site you place links on to be listed there. Links on an unlisted domain are a compliance problem, not a technicality.

**2. Every outbound product link already carries `tag=peteragro-20`.** Verify after any edit:

```bash
grep -o 'amazon\.com[^"]*' *.html | grep -v 'tag=peteragro-20'
```

That should return nothing. If it returns a line, that link is unmonetised.

**3. The links are category searches, not fixed products, on purpose.** A hardcoded pick goes stale within a season — formulas change, sellers go out of stock, prices move. If you later want a specific product, swap the search URL for a product URL and keep the tag:

```html
<!-- from -->
<a href="https://www.amazon.com/s?k=organic+virgin+coconut+oil&tag=peteragro-20">
<!-- to -->
<a href="https://www.amazon.com/dp/YOURASIN?tag=peteragro-20">
```

**4. The 180-day clock.** A new Associates application needs three qualifying sales within 180 days of approval or it lapses and has to be reapplied for. If this domain is a fresh application rather than an addition to your existing account, do not let the site sit unpromoted through that window.

**5. Disclosure is on every page, above the fold, and in the footer.** Required by the FTC and by the Associates operating agreement. Do not remove it from a page when editing.

---

## Three things to change before you launch

**1. The email address.** Every page uses `hello@coconutbaby.com`, which does not exist yet. Set up forwarding (ImprovMX works the same way it does for peteragro.com) or search-and-replace it with an address you already have.

**2. The links, once you have picks.** See point 3 above.

**3. The palette, if you want to.** Every color is a variable at the top of `style.css`. Change a hex value once and it changes everywhere. Nothing else needs editing.

---

## What this site deliberately does not have

No numbered top-ten lists, because a top-ten list is a format that has to be filled whether or not ten things deserve the slot. No newsletter wall. No hardcoded product picks that rot. Each guide explains what a good one looks like on the label, and points at a search so the reader compares current prices themselves.

Every guide carries a "who should skip it" section. That is the thing that makes the site worth linking to, and it is the first thing that will be tempting to cut. Do not cut it.

---

## The mascot

`mascot.svg` — a baby sitting in a coconut half. Vector, so it stays sharp at any size and weighs 2.5KB. It appears in the masthead (36px) and the footer (60px). `favicon.svg` is a simplified version for the browser tab.

Skin tone is `#F0C9A8`, appearing twice in `mascot.svg` and once in `favicon.svg`. Search and replace to change it.

The mascot is deliberately kept away from the safe-sleep panel in the nursery guide and the feeding warning. Cartoon next to a safety warning undercuts the warning.

## Photography

Each guide has a commented-out photo slot ready to go. To switch one on: drop the JPEG in the folder, then delete the two comment lines around the `<figure>`. Styling is automatic.

| File to add | Page | Shot |
|---|---|---|
| `coconut-oil-jar.jpg` | Skin oil | Open jar of virgin coconut oil, solid and white, side light |
| `unlabeled-bottle.jpg` | Balms | Plain white unlabeled bottle and glass jar, pale background |
| `coir-fiber.jpg` | Nursery | Loose coir fiber, coarse texture, raking light |
| `coconut-halves.jpg` | Feeding | A coconut split in half, cream background |
| `folded-bodysuits.jpg` | Clothes | Stack of folded cotton bodysuits in soft colors |

1200px wide, under 200KB each, shot on a plain pale background so they sit inside the pastel palette.

**Two rules that are not style preferences:**

1. **Never save or hotlink an Amazon product image.** Under the Associates operating agreement product images must come through SiteStripe or the Product Advertising API. Scraping listing photos is a common way affiliate accounts get closed.
2. **No photographs of real babies** unless you hold a commercial license and a model release. Subject photography — coconuts, fiber, folded clothes — carries neither risk and suits the brand better.
