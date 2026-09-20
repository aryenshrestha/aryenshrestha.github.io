# Updating Your Website

All changes auto-deploy within ~2 minutes of pushing to `main`. You can make every edit directly on GitHub in your browser — no local tools needed.

---

## Add a new paper

1. Go to `data/papers.yaml` on GitHub and click the pencil (edit) icon.
2. Add a new entry at the top of the appropriate section. Copy an existing entry as a template:

```yaml
- title: "Your Paper Title"
  authors: ["Aryen Shrestha", "Coauthor Name"]
  year: 2025
  status: "working paper"   # working paper | under review | accepted | published | work in progress
  venue: ""                 # journal name if published
  volume: ""
  pages: ""
  pdf: ""                   # e.g. "files/your-paper.pdf"
  link: ""                  # DOI or external URL
  abstract: "One-paragraph abstract."
  note: ""                  # optional, e.g. "Coverage in the New York Times"
  note_link: ""             # optional, makes the note above clickable
  job_market_paper: false
  type: "working-paper"     # working-paper | work-in-progress | published
```

3. If you have a PDF, upload it to `static/files/` and set `pdf: "files/filename.pdf"`.
4. Commit. The site rebuilds automatically.

Two things happen automatically from this entry:

- **Your name is bolded** in the author list wherever it matches the
  `author` value in `hugo.yaml`. Spell it identically ("Aryen Shrestha")
  or it won't match.
- **`year` is displayed** for working papers and works in progress. (For
  published papers the year already appears at the end of the venue
  line, so it isn't repeated.) Leave `year: ""` to show nothing.

---

## Mark a paper as published

In `data/papers.yaml`, change the entry:
- `status:` → `"published"`
- `type:` → `"published"`
- `venue:` → the journal name
- Add `volume:` and `pages:` if known
- Add `link:` with the DOI

---

## Update your bio

Edit `content/_index.md`. The text there is the three-paragraph bio on your homepage. Write in plain Markdown.

---

## Update your CV

Replace `static/files/cv.pdf` with the new version. Keep the same filename — both the "CV" nav link and the "Download CV" button on the About page open this file directly.

---

## Change your photo

Replace `static/images/photo.jpg` with your new headshot. Keep the same filename. The photo displays at 220×220px as a rounded rectangle — a square or portrait image works best.

---

## Add a policy writing entry

Edit `data/policy.yaml` and add an entry:

```yaml
- title: "Your Essay Title"
  authors: ["Aryen Shrestha"]
  year: 2025
  venue: "Publication Name"
  date: "Month Year"
  link: "https://..."
  note: "Coverage in the Boston Globe"   # optional
  note_link: "https://..."              # optional, makes the note text above clickable
```

---

## Google Scholar indexing

The research page carries `citation_*` meta tags describing your
**working papers**, which is how Scholar finds papers hosted on a
personal site. Published papers are left out on purpose — Scholar
already has them through their DOIs, and it expects one paper's worth of
tags per page.

For Scholar to actually index a working paper it has to fetch the PDF
from your own site. So upload the PDF to `static/files/` and set
`pdf: "files/your-paper.pdf"` in `data/papers.yaml`; an external link
(Dropbox, Google Drive) does not count, and no `citation_pdf_url` tag is
emitted for one.

If you ever list more than one working paper, the tags stop pointing at
a single paper and Scholar's guidance is to give each paper its own
page — worth revisiting then.

---

## Change your email, Scholar link, or institution info

Edit `hugo.yaml` and update the relevant field under `params:`.

The `scholar:` field is the Google Scholar link under your photo on the
About page. Clear it (`scholar: ""`) and the link disappears.

---

## Questions?

If something breaks, check the **Actions** tab in GitHub — it shows the build log and any errors.
