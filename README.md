Preview Link: https://apptesting-h59jucfi.myshopify.com/products/the-multi-managed-snowboard
<br>**STORE PASSWORD = 1234**

This covers two custom sections located in `/sections/`:

1. Product Hgihlights
2. Custom Carousel / Verified Reviews



Both sections pull data from **product metafields**, so they only render fully once those metafields are created and populated in Shopify Admin. Below is what to set up for each.


## 1. Product Highlights

### What it does
Renders a two-column "dossier" style block: a numbered ledger of feature highlights (theme editor blocks) plus an expandable "Materials & Care" certificate panel that reads from a product metafield.

### Required metafield

Metafield Name: Highlights<br>
Type: [One] Multi-line Text 

If this metafield is empty or missing, the whole "Materials & Care" panel is skipped automatically (`show_materials and materials_metafield != blank`) — no error, it just won't render.

### Section settings (theme editor)
- Eyebrow text, heading, heading/eyebrow size
- Layout style: **Two column** (ledger + certificate) or **Stacked**
- Accent / ink / background colors
- Toggle: **Show Materials & Care panel**
- Materials panel label text
- Title/description font sizes
- Top/bottom padding

### Blocks
- **Features / Highlight** block — repeatable, add one per feature. Each has:
  - `Title`
  - `Description`

No metaobjects are used in this section — only the one product metafield above plus native section blocks.


## 2. Custom Carousel (Verified Reviews)

### What it does
Renders an infinite-loop testimonial carousel with star ratings, verified-customer badge, image, name, heading, and quote — all sourced from a **list of metaobjects** attached to the product via metafield.

### Intruction: Metaobject definition

Create a metaobject definition (this becomes the "testimonial" content type), then a list metafield on Product that references it.

**Step 1 — Create the metaobject definition**

Metaobject Name: Testimonial Data<br>
Fields:<br>
  - Image - Image File<br>
  - Rating - Integer<br>
  - Name - Single Line Text<br>
  - Heading - Single Line Text<br>
  - Testimonial - Multi-line Text<br>

**Step 2 — Create entries**

**Step 3 — Create the product metafield that lists these entries**

Metafield Name: Testimonials<br>
Type: [List] Metaobject   - then select the Metaobject "Testimonial Data"

Then, on each product page, go to the Metafields section and select which Testimonial entries to attach/reorder for that product.

### Section settings (theme editor)
- Section title / subtitle (text, color, size)
- Section background color
- Card background / active-card background color
- Active card zoom toggle
- Star, name, badge, heading, and content colors + sizes
- Navigation button color

No blocks are used in this section — all content comes from the `custom.testimonials` metafield list, so the carousel automatically shows/hides nav controls (hidden if 3 or fewer testimonials).

