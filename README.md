# courtneylkPortfolio

Instructional design portfolio for Courtney Lewis-Kroodsma.
Live at **https://keiria.github.io/courtneylkPortfolio/**

Static site — plain HTML and CSS, no build step, no dependencies.

---

## Structure

```
.
├── index.html          # the site: hero, intro, stats, work, experience, contact
├── style.css           # all styling; palette is the :root variables at the top
├── .nojekyll           # tells GitHub Pages to serve files as-is (required — see below)
├── .gitignore
├── LICENSE
└── courses/            # published Rise 360 courses, one folder each
    └── <course-name>/
        └── index.html
```

---

## Hosting a Rise 360 course here

Rise's web export is a folder of static files, which is exactly what GitHub Pages serves.

**1. Export from Rise.** Open the course → **Export** → choose **Web**. You'll get a zip.
(Web export needs a standard Articulate 360 license.)

**2. Unzip it into `courses/`.** Use a short, lowercase, hyphenated folder name — it becomes
part of the public URL, so `onboarding-narrative` beats `Course Final v3 FINAL`.

```
courses/onboarding-narrative/index.html
courses/onboarding-narrative/lib/...
courses/onboarding-narrative/assets/...
```

Don't rename or reorganize anything inside the exported folder. Rise links its own files by
relative path and moving them breaks the course.

**3. Commit and push.**

```bash
git add courses/onboarding-narrative
git commit -m "Add onboarding narrative course"
git push
```

**4. Link to it** from a work card in `index.html`:

```html
<p class="card-link"><a href="courses/onboarding-narrative/index.html">View the course &rarr;</a></p>
```

Live at `https://keiria.github.io/courtneylkPortfolio/courses/onboarding-narrative/index.html`

### Why `.nojekyll` matters

GitHub Pages runs files through Jekyll by default, and Jekyll **ignores any file or folder whose
name starts with an underscore**. Rise output can contain those, and when it does the course loads
a blank or broken page with no error explaining why. The empty `.nojekyll` file in the repo root
turns Jekyll off entirely. Don't delete it — this is the single most common reason a Rise course
"works locally but not on Pages."

### Size limits

GitHub Pages: **100 MB per file** (a hard git limit), **1 GB per repository**, and a **1 GB published
site limit**. Bandwidth is a soft 100 GB/month, which a portfolio will never approach.

Course video is what breaks this. A few narrated modules with embedded video will pass 1 GB faster
than you'd expect. Host video on YouTube or Vimeo as unlisted and embed it in the Rise course
rather than committing the files — that keeps the repo small and the course loading fast.

---

## Publishing checklist

Repo **Settings → Pages → Source: Deploy from a branch → `main` / `/ (root)` → Save.**
First build takes a minute or two.

**Custom domain:** Settings → Pages → Custom domain. Add the domain, then at your registrar create
a CNAME record pointing at `keiria.github.io`. Tick **Enforce HTTPS** once the certificate issues.
Free apart from the domain registration.

---

## Before each commit

**This repository is public.** GitHub Pages serves from public repos on the free plan, so everything
here is world-readable — including everything in git history. Removing a file in a later commit does
not remove it from history.

Which means: **nothing proprietary goes in this repo.** No employer course content, no internal
screenshots, no customer names, no material built on company time or with company tooling. Portfolio
pieces published here should be work you built for the portfolio, or work you have written permission
to show.

---

## Editing

Change the palette in the `:root` block at the top of `style.css` — `--accent` is the one colour
doing real work, everything else is a neutral. Light and dark are both defined; dark follows the
visitor's system setting.

Work samples are `<article class="card">` blocks in the `#work` section. Copy one to add another.
Anything in `[square brackets]` is a placeholder waiting on real content.
