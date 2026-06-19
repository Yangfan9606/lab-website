# Admin Editing Reference

What each section in the visual admin (`/admin`) lets you edit. Open `/admin`, pick a section in the left sidebar, change the fields, click **Save** -> the live site updates in ~1-3 minutes (hard-refresh with Ctrl/Cmd+Shift+R if you don't see it).

The sidebar has **4 sections**: **Pages** (click it, then pick one of the 6 pages on the right), **Site settings**, **Members**, and **Blog posts**.

---

## Page sections (text & images per panel)

### 1. Main page
The home page.
- **Big title** - the large heading at the top
- **Intro paragraph** - the sentence under the title
- **Panel 1 / 2 / 3** (the three "Highlights" cards), each has:
  - **title** (e.g. "Our Research")
  - **text** (the paragraph)
  - **button label** (e.g. "See our publications")
  - **image** (the card photo)
- Fixed: there are exactly **3 panels** (it's a 3-up layout). The buttons always link to Research / Projects / Team.

### 2. Research page
- **Intro paragraph** (top of the page)
- The publication list below it is **not** here - see "Adding publications" at the bottom.

### 3. Projects page
- **Intro paragraph** (top of the page)
- The project cards are their own **Projects** section in the sidebar (add/remove anytime).

### 4. Team page
- **Intro paragraph** (top)
- **Mid-page band paragraph** (the text in the dark photo band)
- **Bottom photos** - a list; add/remove as many as you like, they wrap into a grid automatically
- The people grid comes from the **Members** section (below).

### 5. Blog page
- **Intro paragraph** (top of the blog page)
- The list of posts comes from the **Blog posts** section (below).

### 6. Contact page
- **Intro paragraph** (top)
- **Email address**, **Phone (shown)**, **Phone (dial link)**
- **Address tooltip**, **Map / address link**
- **Photos** - a list (image + caption); add/remove as many as you like
- **Bottom column 1 / 2 / 3** (the three text columns at the bottom)

---

## Site-wide

### 7. Site settings (lab identity)
- **Lab name** - shown in the header and footer
- **Subtitle** - small text under the name
- **Description** - used by search engines and link previews
- **Social / contact links** - Email, ORCID, Google Scholar, GitHub, Twitter/X, YouTube (footer icons). Leave one blank to hide that icon.

> The background image and the lab logo are not in the admin: replace `images/background.jpg` (background) or add `images/logo.svg` / `logo.png` (logo) in the repo.

---

## Repeatable lists (add/remove as many as you want, anytime)

### 8. Members
One entry per person. Click **+ Member** to add, open an entry to edit or delete.
- **Name**, **Photo** (auto-cropped to a centered circle), **Role** (PI / Postdoc / PhD / Masters / Undergrad / RA-Programmer / Alumni), **Affiliation**
- **Name aliases** (helps auto-match paper authors)
- **Known links** - email, home page, ORCID, Scholar, GitHub, Twitter, LinkedIn. An icon shows **only if you fill that field** (blank = hidden). On the member's page each link shows its icon followed by the actual address/handle, left-aligned.
- **Other links (custom)** - a list of label + URL pairs for anything not in the known list (e.g. CIW, a database profile). Shows a globe icon + your label.
- **Bio**
- The Team page automatically groups people by role and **wraps to multiple rows** - 4 people or 40, no layout editing needed.

### Projects
One entry per project card. Click **+ Project** to add, open one to edit or delete.
- **Title**, **Subtitle**, **Section** (Featured = large top row / More = smaller below), **Image**, **Link**, **Description**, **GitHub repo** (optional, shows stars), **Tags**
- The Projects page fills its Featured and More rows automatically.

### Blog posts
One entry per post. Click **+ Blog post** to add.
- **Title**, **Date**, **Author** (dropdown of Members), **Tags**, **Body**

---

## FAQ

**Can I add more items anytime?**
- **Members** and **Blog posts**: yes - unlimited. Use **+ Member** / **+ Blog post**. The team grid and blog list grow automatically.
- **Publications**: yes - unlimited (see below).
- **Projects**: yes - unlimited. Use **+ Project**.
- **Home page panels**: no - fixed at 3 by the layout. A 4th would require a layout change.

**Adding publications** (admin, one line): edit `_data/sources.yaml`, add a line at the top:
```yaml
- id: doi:10.1234/your.doi.here
```
The template auto-fetches the title, authors, journal, and thumbnail. They appear on the Research page.

**Adding projects**: use the **Projects** section in the admin -> **+ Project**. Set **Section = Featured** for the large top row, or **More** for the smaller grid below.

**Can I change the font size?**
Yes, but it's a style setting, not content - edit `_styles/-theme.scss`:
- For everything at once, add a base size to the `:root { ... }` block, e.g. `font-size: 18px;` (default is the browser's 16px). Most sizes use `rem`, so this scales the whole site proportionally.
- For just the larger text, tweak these variables in the same block:
  ```scss
  --large: 1.2rem;
  --xl: 1.4rem;
  --xxl: 1.6rem;
  ```
- Fonts and colors live in the same file (`--body`, `--heading`, `--primary`, etc.).

**Where layout / one-time settings live** (not in the admin, on purpose):

| Thing | File |
|---|---|
| Background image | replace `images/background.jpg` |
| Logo | add `images/logo.svg` (or `.png` / `.jpg`) |
| Font size / fonts / colors | `_styles/-theme.scss` |
| Nav order & tooltips | each page's frontmatter `nav:` |
| Jekyll / plugin settings | `_config.yaml` |
