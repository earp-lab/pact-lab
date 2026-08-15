# PACT Lab website

The site for PACT Lab (Patient and public Action, Collaboration, and Trust in Research), a joint initiative of the Centre for Biomedical Ethics, NUS Medicine, and the National University Health System.

Built with Jekyll and published through GitHub Pages. Every change pushed to `main` rebuilds and republishes the site within a minute or two.

## Making an edit without installing anything

Everything below can be done in a web browser, on github.com, with no software installed.

1. Click the file you want to change.
2. Click the pencil icon (Edit this file).
3. Make the change.
4. Scroll down, write one line saying what you changed, and click Commit changes.

The site rebuilds itself. If a build fails, the Actions tab shows why, and the previous version stays live.

## The three files you will actually edit

### `_data/people.yml` — who is on the team

Grouped into Leadership, Steering Committee, Core Staff, Affiliated Staff, Collaborators, and Advisors. Each person has a name, initials, and optionally a photo, role, affiliation, blurb, and profile link. Instructions are at the top of the file.

To add a photo: upload a square JPEG to `assets/images/people/` (Add file → Upload files), name it `firstname-lastname.jpg`, then write `photo: "people/firstname-lastname.jpg"` in that person's entry. Without a photo, the initials show in a circle instead.

### `_data/publications.yml` — the publication list

Grouped into sections (CREP, experimental bioethics, patient and public involvement), newest first within each. House format: authors as `Surname, A. B., & Surname, C. D.`, titles in sentence case, en dashes in page ranges, and the DOI as a full `https://doi.org/...` address. The title links to the DOI automatically.

### `_events/` — talks and workshops

One file per event, not a single list. To add an event, click Add file → Create new file inside `_events/`, name it something like `2026-11-mark-sheen.md`, and copy the top of an existing file:

```
---
title: "The title of the talk"
speaker: "Name"
affiliation: "Institution"
date: 2026-11-13
time: "4:00–5:30pm"
location: "MD11 Seminar Room, 10 Medical Drive"
blurb: "One or two sentences for the events list."
registration: "https://..."
---
```

Only `title` and `date` are required; leave out anything that does not apply. Keep the date as `YYYY-MM-DD`, since that is what sorts the list and decides whether the event shows under Upcoming or Past. Nothing needs deleting after an event happens.

Anything written below the closing `---` becomes a page of its own for that event, at `/events/its-file-name/`, and the card on the events list links to it. An event with nothing below the `---` shows its details on the list and links nowhere. So a short notice stays a short notice, and a substantial talk gets an abstract, a speaker biography, and slides afterwards.

**Registration.** Put the form's link in the `registration:` field and a Register button appears at the top of the event page. Leave it empty and the page says "Registration details to follow" instead. Any form works: Microsoft Forms through the NUS Office 365 account is the sanctioned option and collects responses into Excel.

A visit with more than one talk can list them under `talks:` in the front matter, as `_events/mark-sheehan-visit.md` does. Each talk then gets its own card on the events list, and all of them link to the same page, which shows the dates side by side. A `speakers:` list in the front matter adds photo cards at the top of the page, using the same fields as `_data/people.yml`.

### `_data/resources.yml` — guidance and training materials

Grouped into sections. Each item has a type label, title, blurb, and either a link or a "coming soon" note. To publish a PDF, upload it to `assets/docs/` and set `url: "/assets/docs/filename.pdf"`.

## Everything else

The site has four pages: the home page, `/publications/`, `/events/`, and `/resources/`. Each page file (`index.html`, `publications.html`, `events.html`, `resources.html`) is short and only sets the title and pulls in the pieces below.

- `_includes/section-*.html` — the standing prose sections (What we do, Our method, How it works, Governance, Research). Plain HTML; edit the text directly.
- `_includes/hero.html` — the top of the page, including the hub diagram.
- `_includes/nav.html`, `instbar.html`, `footer.html` — navigation, the institutional bar, the footer.
- `assets/css/style.css` — all styling. One file.
- `assets/docs/` — put PDFs and other documents here to link to them from the Resources section.
- `index.html` — the order the sections appear in.

## Going live

While the repository is private the site does not publish. When the content is cleared:

1. Settings → General → Change visibility → Public.
2. Settings → Pages → Source → Deploy from a branch → `main`, folder `/ (root)` → Save.

The site appears at `https://earp-lab.github.io/pact-lab`.

## Custom domain

Buy the domain first, then Settings → Pages → Custom domain, enter it, and follow the DNS instructions GitHub gives. Tick Enforce HTTPS once it verifies.

Then in `_config.yml`, set `url` to the domain and change `baseurl` to `""`. Leaving `baseurl` as `/pact-lab` after moving to a custom domain breaks image and stylesheet paths.

## Running it locally (optional)

Only needed to preview changes before publishing.

```
bundle install
bundle exec jekyll serve
```

Then open `http://localhost:4000/pact-lab/`.
