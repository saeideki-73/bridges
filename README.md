# Bridges to the Future — website source

Static, framework-free site (plain HTML/CSS). No build step — ready to push to GitHub as-is.

## Folder structure

```
index.html          Home
about.html           About the lab
news.html            News & events (collapsible entries)
projects.html        Research projects (links to individual project pages below)
projects/
  p01-heavy-axle-load-capacity.html       Individual project pages, one per
  p02-corrosion-smooth-reinforcement.html project, with aims, main body of
  p03-railway-earthwork-stability.html    work, and a photo gallery at the
  p04-rc-slabs-fibre-optic.html           end (album/bar/pair layout
  p05-composite-segmental-bridges.html    depending on the project)
  p06-next-gen-bridge-design.html
  p07-corroded-bridge-columns.html
  p08-crossrail-elizabeth-line.html
people.html          Team (links to individual profile pages below)
people/
  mehdi-kashani.html        Individual profile pages, one per
  ziliang-zhang.html        team member with photo, bio,
  masoud-mohandes.html      qualifications, publications and
  hossein-agha-beigi.html   contact/ORCID/Scholar/ResearchGate
  saba-ghassemi.html        links
  saeid-ekraminia.html
  hailong-cao.html
  karl-minta.html
publications.html    Publications (collapsible by category)
contact.html         Contact
home/index.html      Redirect only — keeps old Google Sites URL (/home) alive, e.g. for your QR code
assets/
  css/style.css      All styling
  images/
    logo.png                     ← drop your logo here
    people/<name>.jpg            ← one photo per team member (see filenames below)
    projects/<id>-<slug>.jpg     ← one photo per project
    events/<id>-<slug>.jpg       ← one photo per news/event item
```

Amirreza Zarei doesn't have a dedicated profile page yet — send over his
bio/qualifications/publications in the same format as the others and I'll
add `people/amirreza-zarei.html`.

**Karl Minta's page** is missing contact links (email/Scholar/ORCID/
ResearchGate) — the details you sent for him matched Saba Ghassemi's, so
they were left out rather than publish the wrong contact info under his
name. Send the correct ones and I'll add them.

## Keeping old links and QR codes working

Google Sites serves your homepage at `/home` (e.g. `bridges2f.com/home`). This
new site's homepage is just `/`, so `home/index.html` is included purely to
redirect anyone hitting the old `/home` URL — including any QR codes, printed
materials, or bookmarks using that link — straight to the new homepage.
No action needed; just keep that folder when you push to GitHub. If you ever
add other old Google Sites URLs you want preserved (e.g. `/contacts` instead
of `/contact.html`), copy this same pattern: a folder named after the old
path, containing an `index.html` with `url=../` in the `<meta http-equiv="refresh">`
tag adjusted to point at the right new page.

## Adding your images

Every photo slot already works without an image (it shows a steel/rust
placeholder with initials or a short label), so the site is safe to publish
as-is. To swap in a real photo, save it with **exactly** this filename —
no code changes needed:

**Logo**
- `assets/images/logo.png`

**People** (`assets/images/people/`)
- `mehdi-kashani.jpg`
- `ziliang-zhang.jpg`
- `masoud-mohandes.jpg`
- `hossein-agha-beigi.jpg`
- `saba-ghassemi.jpg`
- `saeid-ekraminia.jpg`
- `hailong-cao.jpg`
- `karl-minta.jpg`
- `amirreza-zarei.jpg`

**Projects** (`assets/images/projects/`)
- Card thumbnail (shown on `projects.html`): `p01-heavy-axle-load-capacity.jpg`, `p02-corrosion-smooth-reinforcement.jpg`, etc. (one flat file per project, filenames as listed above)
- Gallery photos (shown at the bottom of each project's own page): inside a folder named after the project, numbered in order —
  `assets/images/projects/p01-heavy-axle-load-capacity/1.jpg`, `2.jpg`, `3.jpg`, `4.jpg`
  `assets/images/projects/p02-corrosion-smooth-reinforcement/1.jpg`, `2.jpg`, `3.jpg`
  `assets/images/projects/p03-railway-earthwork-stability/1.jpg`, `2.jpg`
  `assets/images/projects/p04-rc-slabs-fibre-optic/1.jpg`, `2.jpg`
  `assets/images/projects/p05-composite-segmental-bridges/1.jpg`, `2.jpg`
  `assets/images/projects/p06-next-gen-bridge-design/1.jpg`, `2.jpg`
  `assets/images/projects/p07-corroded-bridge-columns/1.jpg`, `2.jpg`, `3.jpg`, `4.jpg`
  `assets/images/projects/p08-crossrail-elizabeth-line/1.jpg`, `2.jpg`
  (the empty folders are already included in this export, ready for your photos)

**Events** (`assets/images/events/`)
- `e01-revive-workshop.jpg`
- `e02-13ncee.jpg`
- `e03-fib-congress.jpg`
- `e04-istructe-award.jpg`
- `e05-revive-grant.jpg`
- (e06, the ICE medal item, has no photo slot yet — add one in `news.html` if you have an image)

Recommended sizes: people photos roughly square (e.g. 500×500px);
project/event photos landscape (e.g. 800×500px). JPG or PNG both work —
just match the filename exactly (or update the `src=` in the HTML if you'd
rather use a different name/extension).

## Publishing with GitHub Pages

1. Create a new repository on GitHub (e.g. `bridges2f-site`).
2. Push this folder's contents to the repository root:
   ```
   git init
   git add .
   git commit -m "Initial site"
   git branch -M main
   git remote add origin https://github.com/<your-username>/<repo-name>.git
   git push -u origin main
   ```
3. In the repo, go to **Settings → Pages**, set branch to `main` and folder
   to `/ (root)`, then save.
4. GitHub will publish it at `https://<your-username>.github.io/<repo-name>/`.
5. To use `bridges2f.com`: add a `CNAME` file to the repo root containing
   just `bridges2f.com`, then in your domain registrar's DNS settings point
   an `A` record to GitHub Pages' IPs (or a `CNAME` record to
   `<your-username>.github.io` if using a `www` subdomain). GitHub's own
   docs for "Managing a custom domain for your GitHub Pages site" cover the
   exact records needed.

## Editing content

There's no CMS — text lives directly in the HTML files. Open the relevant
page in any text editor, find the text, and edit it directly. The
publications and news sections use `<details>`/`<summary>` for the
collapsible panels; keep that structure when adding new entries.
