# Admin Editing Reference

What each section in the visual admin (`/admin`) lets you edit. Open `/admin`, pick a section in the left sidebar, change the fields, click **Save** -> the live site updates in ~1-3 minutes (hard-refresh with Ctrl/Cmd+Shift+R if you don't see it).

The sidebar has these sections: **Pages** (click it, then pick one of the 6 pages on the right), **Publications**, **Auto-import (ORCID)**, **Site settings**, **Members**, **Projects**, **Lab Life**, and **Blog posts**.

---

## Page sections (text & images per panel)

### 1. Main page
The home page.
- **Home banner image** - optional; overrides the site-wide Top banner just for the home hero. Blank = use the site-wide one (Site settings).
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
- **Heading above featured papers** (default "Highlighted")
- **Featured papers** - a list; paste a paper title or DOI (must exist in your publications). Each shows as a large card.
- **Heading above the full publication list** (default "All")
- **Talks & videos** (shown right under Highlighted) - a list of YouTube links (paste a normal watch?v=... or youtu.be/... URL + a title). They embed side by side as players. Empty list hides the section.
  - **How many videos to show** (`videos_max`, default 6); if you have more, a **More videos** button appears linking to a full `/videos/` page.
  - **Video size** - Small / Medium / Large (or type any CSS width in the data file for a custom size).
- **The full publication list** shows only your **curated** papers - the ones you add in the **Publications** section (see below). It does **not** show auto-imported ORCID papers (those go on each member's own page instead), so the Research page stays clean even with a big lab.

> Not in the admin (page layout): the "Research" heading + icon and the nav tooltip live in `research/index.md`.

### 3. Projects page
- **Intro paragraph** (top of the page)
- The project cards are their own **Projects** section in the sidebar (add/remove anytime).

### 4. Team page
- **Intro paragraph** (top)
- **Mid-page band paragraph** (the text in the dark photo band)
- **Photo wall** - a list; add/remove as many as you like (same photos, edited here once). Shows as **one row** at the **top of the Team page** and on the **Main page**. Hover a photo to zoom/highlight it; click to open it large (lightbox).
  - **How many photos to show** (`photos_max`, default 6); if you have more, a **More photos** button appears linking to a full `/photos/` page.
- The people grid comes from the **Members** section (below).

### 5. Blog page
- **Intro paragraph** (top of the blog page)
- **"Lab Life" section heading** - the title of the activity gallery shown right below the search box (default "Lab Life").
- **How many Lab Life cards to show** (`life_max`, default 3) - if you have more items, a **More** button links to the full `/life/` page.
- **Lab Life intro** - optional text shown only at the top of the full `/life/` page.
- The Lab Life cards themselves (cover + title) come from the **Lab Life** section (below). The search box does **not** filter these - it only filters the blog posts.
- The list of posts comes from the **Blog posts** section (below).
- The tag keywords shown under the search box are generated automatically from the **tags you give each blog post** - add or rename a tag on a post and it shows up here. There is no separate list to edit.

### 6. Contact page
- **Intro paragraph** (top)
- **Email address**, **Phone (shown)**, **Phone (dial link)**
- **Address tooltip**, **Map / address link**
- **Extra buttons** - a list; add as many as you like next to email/phone/address. Pick an icon, set button text + link.
- **Photos** - a list (image + caption); add/remove as many as you like
- **Bottom column 1 / 2 / 3** (the three text columns at the bottom)

---

## Site-wide

### 7. Site settings (lab identity)
- **Lab name** - shown in the header and footer
- **Subtitle** - small text under the name
- **Description** - used by search engines and link previews
- **Top banner image** - the large image at the top of every page (the big hero on the home page). This is separate from the whole-page background below.
- **Footer background image**.
- **Whole-page background image** - one image behind the entire site; content sits on translucent panels so text stays readable. **Leave blank for the plain look.** (Different setting from the Top banner - they can be the same or different images.)
- **How much the background shows through** - Subtle / Medium / Strong.
- **Social / contact links** - Email, ORCID, Google Scholar, GitHub, Twitter/X, YouTube, LinkedIn (footer icons). Leave one blank to hide that icon.
- **Auto-imported papers per member page** (`member_publications_max`, default 5) - how many of each person's ORCID papers to list on their page before a "See all on ORCID" link.

> The background image and the lab logo are not in the admin: replace `images/background.jpg` (background) or add `images/logo.svg` / `logo.png` (logo) in the repo.

---

## Repeatable lists (add/remove as many as you want, anytime)

### 8. Members
One entry per person. Click **+ Member** to add, open an entry to edit or delete.
- **Name**, **Photo** (auto-cropped to a centered circle), **Role** (PI / Co-PI / Research Scientist / Postdoc / PhD / Masters / Undergrad / RA-Programmer / Lab Manager / Visiting Scholar / Rotation Student / Alumni), **Affiliation**
- The Team page shows people in **sections by role, in a fixed order with the PI/Leader first**; empty roles are skipped automatically. (To add/reorder roles, a maintainer edits three matched places: `_data/types.yaml`, the Role dropdown in `admin/config.yml`, and the `role_order` line in `team/index.md`.)
- **Name aliases** (helps auto-match paper authors)
- **Known links** - email, home page, ORCID, Scholar, GitHub, Twitter, LinkedIn. An icon shows **only if you fill that field** (blank = hidden). On the member's page each link shows its icon followed by the actual address/handle, left-aligned.
- **Other links (custom)** - a list of label + URL pairs for anything not in the known list (e.g. CIW, a database profile). Shows a globe icon + your label.
- **Bio**
- **Recent publications (automatic)** - if a member has an **ORCID** filled in their Known links **and** that same ORCID is added under **Auto-import (ORCID)** (below), their newest papers appear automatically at the bottom of their page (capped by the Site setting, rest link to ORCID). Nothing to type per paper.
- The Team page automatically groups people by role and **wraps to multiple rows** - 4 people or 40, no layout editing needed.

### Auto-import (ORCID)
The **Auto-import (ORCID)** section -> **ORCID profiles to import** -> the list. Click **+ ORCID iD** to add a profile.
- Paste an **ORCID iD** (e.g. `0000-0002-1825-0097`). On the next rebuild, **every paper on that profile is fetched and cited automatically**, and shown on the matching member's page (match = the same ORCID in that person's **Known links**).
- These do **not** appear on the Research page (that stays your curated list). Empty list = no auto-import.
- This is how you keep publications current without typing them: add a member + their ORCID once, and new papers show up by themselves.

### Publications
The **Publications** section in the sidebar -> open **Publication list** -> the **Publications** list. Click **+ Publication** to add, open one to edit, or use the trash icon to remove.
- **ID** - the only field you usually need: a DOI (`doi:10.1234/abc`), PubMed ID (`pmid:12345678`), arXiv id (`arxiv:2001.00001`), or a plain URL. The **title, authors, journal, and date are fetched automatically** when the site rebuilds.
- **Type** (icon), **Image/thumbnail**, **Description** (shows on Highlighted cards), **Tags**, **GitHub repo** (shows stars), **Buttons** (extra links under the card).
- Advanced (optional, all override the auto-fetched value): **Title / Authors / Journal / Date / Link**.
- **Hide this entry** - keeps the row but removes it from the site.
- To feature a paper as a large card at the top of Research, also add its **title or DOI** to **Pages -> Research page -> Featured papers**.

### Projects
One entry per project card. Click **+ Project** to add, open one to edit or delete.
- **Title**, **Subtitle**, **Section** (Featured = large top row / More = smaller below), **Image**, **Link**, **Description**, **GitHub repo** (optional, shows stars), **Tags**
- The Projects page fills its Featured and More rows automatically.

### Lab Life
Records of lab activities - team-building game rules, plant care, lab chores, anything. One entry per item. Click **+ Lab Life item** to add, open one to edit or delete.
- **Title**, **Cover image**, **Subtitle / category** (optional, e.g. "Team-building"), **Date**, **Write-up** (the full rules / instructions / notes, in the body).
- Each item shows as a **cover + title card** on the **Blog page** (below the search box) and opens its **own page** with the write-up. The newest 3 show on the Blog page (set by **Pages -> Blog page -> How many Lab Life cards to show**); the rest are on the full **/life/** page behind the **More** button.

### Blog posts
One entry per post. Click **+ Blog post** to add.
- **Title**, **Date**, **Author** (dropdown of Members), **Tags**, **Body**

---

## FAQ

**Can I add more items anytime?**
- **Members** and **Blog posts**: yes - unlimited. Use **+ Member** / **+ Blog post**. The team grid and blog list grow automatically.
- **Publications**: yes - unlimited. Use the **Publications** section -> **+ Publication**.
- **Projects**: yes - unlimited. Use **+ Project**.
- **Lab Life**: yes - unlimited. Use the **Lab Life** section -> **+ Lab Life item**.
- **Home page panels**: no - fixed at 3 by the layout. A 4th would require a layout change.

**Adding publications**: use the **Publications** section in the admin -> **+ Publication**, then paste a DOI (e.g. `doi:10.1234/your.doi.here`) into **ID**. The template auto-fetches the title, authors, journal, and thumbnail on the next rebuild, and they appear on the Research page.

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
