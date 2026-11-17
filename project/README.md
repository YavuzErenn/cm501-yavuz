# Vanto

**What it is:** A website for Vanto, a small campervan workshop in Bursa, so that people who dream of travelling by van can compare models and request a quote.

**Audience:** Couples and families in Türkiye planning a camping holiday, and van owners who want their own van converted.

**Pages:**

- `index.html` (Home): what we build, upcoming trade fairs, contact details
- `models.html` (Models): five motorhome sizes and two towed caravans, with a spec table and a floor plan
- `about.html` (About us): the workshop, the team and the FAQ
- `contact.html` (Contact and quote): the quote form, address and opening hours

**The form:** a quote request: name, e-mail, phone, city, the van you own, the motorhome size you want, and a privacy checkbox.

**What changes:** the list of trade fairs (dates and cities) and later the model list.

**Real or fictional?** Fictional. Vanto is inspired by a real caravan maker in Bursa, but the name, texts, contact details and numbers are invented. The site may switch to the real company's content later, only with the company's written permission.

**Live:** not published yet

## HTML baseline (Session 4 · prerequisite for EPA 3)

Fill in **where** each feature is used (file and element or line). Must items (M) are required; pick optional items (O) that fit your content.

| # | Feature | Where (file · element / line) |
|:--:|------------------------------------------------------------|------------------------------|
| M1 | `lang`, `charset`, `viewport`, unique `title` ("Page · Site"), `meta description`, favicon | all pages · `<head>` (index.html l. 4–10); titles: Home / Models / About us / Contact and quote · Vanto |
| M2 | landmarks `header` `nav` `main` `footer`; skip link as first element | all pages · skip link first in `<body>` (index.html l. 15), `header` l. 17, `nav` l. 20, `main` l. 30, `footer` l. 77 |
| M3 | navigation as a list, identical on all pages, `aria-current="page"` | all pages · `nav` > `ul` (index.html l. 20–27); `aria-current` on each page's own link |
| M4 | one `h1` per page, no skipped heading levels | index.html · `h1` l. 31 → `h2` l. 37, 57 → `h3` l. 41–68; one `h1` on every stub page |
| M5 | images: `alt` (or `alt=""`), `width`/`height`, `loading="lazy"` below the fold; one `figure` + `figcaption` | planned: models.html (step 5) |
| M6 | lists for lists; `article`/`section` with headings where they fit | index.html · two `section`s (l. 36, 56), each a `ul` of `article`s (l. 38–72) |
| M7 | meaningful link texts; `<address>` with `tel:` / `mailto:` links | index.html · links "Compare our motorhome sizes", "See our caravan models"; `<address>` l. 78 with `tel:` l. 81, `mailto:` l. 82 |
| M8 | `<time datetime="…">` for at least one date or time | index.html · trade fair dates l. 62, 69 |
| M9 | one form: visible labels, right `type`, `autocomplete`, "(required)" + `required`, real `<button>`; `fieldset`/`legend` for groups | planned: contact.html (step 6) |
| M10 | W3C validator 0 errors · axe 0 violations · keyboard: everything reachable, focus visible | planned: step 9 |
| O1 | responsive image: `srcset` + `sizes` or `<picture>` | not planned |
| O2 | data table with `<caption>` and `<th scope>` | planned: models.html spec table (step 5) |
| O3 | `<details>` / `<summary>` (e.g. FAQ) | planned: about.html FAQ (step 7) |
| O4 | `<dl>` for name–value pairs (e.g. opening hours, facts) | planned: contact.html opening hours (step 6) |
| O5 | `<blockquote>` with source, `<abbr>` with the expansion written out once | not planned |
| O6 | icon-only link or button with `aria-label` and `aria-hidden="true"` on the icon | planned: Instagram / YouTube icon links in the footer (step 8) |
| O7 | `<iframe>` with `title` (map, video), privacy considered | not planned |
| O8 | `lang` on a passage in another language (e.g. `<span lang="de">`) | index.html l. 34 · `<span lang="tr">` motto |

**Tests:** validator: TODO date + result · axe: TODO · keyboard: TODO · screen reader: TODO (which one, what you checked)

**AI use:** TODO, one sentence (or "none").

## Swap list: fictional → real (only with permission)

Every place that has to change if the real company agrees:

- company name "Vanto": `<title>`, header link and footer of all pages, this README
- `meta description` of all pages
- address, phone and e-mail: `<address>` in the footer of all pages, `contact.html`
- motto in `index.html` (`<span lang="tr">`)
- model names and specs: `index.html`, `models.html`
- trade fairs: `index.html`
- photos and their credits
- footer note "fictional company"
