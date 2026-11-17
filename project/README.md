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

**Live:** https://yavuzerenn.github.io/cm501-yavuz/project/

## HTML baseline (Session 4 · prerequisite for EPA 3)

Fill in **where** each feature is used (file and element or line). Must items (M) are required; pick optional items (O) that fit your content.

| # | Feature | Where (file · element / line) |
|:--:|------------------------------------------------------------|------------------------------|
| M1 | `lang`, `charset`, `viewport`, unique `title` ("Page · Site"), `meta description`, favicon | all pages · `<head>` (index.html l. 4–10); titles: Home / Models / About us / Contact and quote · Vanto |
| M2 | landmarks `header` `nav` `main` `footer`; skip link as first element | all pages · skip link first in `<body>` (index.html l. 15), `header` l. 17, `nav` l. 20, `main` l. 30, `footer` l. 77 |
| M3 | navigation as a list, identical on all pages, `aria-current="page"` | all pages · `nav` > `ul` (index.html l. 20–27); `aria-current` on each page's own link |
| M4 | one `h1` per page, no skipped heading levels | index.html · `h1` l. 31 → `h2` l. 37, 62 → `h3` l. 41–73; contact.html · `h1` → `h2` "Request a quote", "Opening hours of the workshop"; one `h1` on every stub page |
| M5 | images: `alt` (or `alt=""`), `width`/`height`, `loading="lazy"` below the fold; one `figure` + `figcaption` | index.html · `figure` + `figcaption` with `img/vanto-13.svg`, descriptive `alt`, `width`/`height` 640×360, `loading="lazy"` (l. 55–58) |
| M6 | lists for lists; `article`/`section` with headings where they fit | index.html · two `section`s (l. 36, 61), each a `ul` of `article`s (l. 38–78) |
| M7 | meaningful link texts; `<address>` with `tel:` / `mailto:` links | index.html · links "Compare our motorhome sizes", "See our caravan models"; `<address>` l. 83 with `tel:` l. 86, `mailto:` l. 87 |
| M8 | `<time datetime="…">` for at least one date or time | index.html · trade fair dates l. 67, 74; contact.html · opening hours (l. 101–108) |
| M9 | one form: visible labels, right `type`, `autocomplete`, "(required)" + `required`, real `<button>`; `fieldset`/`legend` for groups | contact.html · quote form (l. 35–96): visible labels, `type="email"` / `tel`, `autocomplete` (name, email, tel, address-level2), "(required)" + `required`, hints with `aria-describedby`, `fieldset`/`legend` for the radio group (l. 57), privacy checkbox, `<button>` "Send quote request" |
| M10 | W3C validator 0 errors · axe 0 violations · keyboard: everything reachable, focus visible | all 4 pages · W3C validator 0 errors, Lighthouse accessibility (axe) 100; keyboard: see Tests |
| O1 | responsive image: `srcset` + `sizes` or `<picture>` | not planned |
| O2 | data table with `<caption>` and `<th scope>` | planned: models.html spec table (step 5) |
| O3 | `<details>` / `<summary>` (e.g. FAQ) | planned: about.html FAQ (step 7) |
| O4 | `<dl>` for name–value pairs (e.g. opening hours, facts) | contact.html · opening hours as `<dl>` with `<time>` (l. 101–108) |
| O5 | `<blockquote>` with source, `<abbr>` with the expansion written out once | not planned |
| O6 | icon-only link or button with `aria-label` and `aria-hidden="true"` on the icon | planned: Instagram / YouTube icon links in the footer (step 8) |
| O7 | `<iframe>` with `title` (map, video), privacy considered | not planned |
| O8 | `lang` on a passage in another language (e.g. `<span lang="de">`) | index.html l. 34 · `<span lang="tr">` motto |

**Tests:** validator: 2026-11-17, 0 errors and 0 warnings on all 4 pages · axe (via Lighthouse 13.5 accessibility): 100 on all 4 pages, 0 violations · keyboard (2026-11-18, local files): skip link is the first Tab stop, every link, field and the button are reachable with Tab, focus is always visible, the radio group is one Tab stop and the options change with the arrow keys · screen reader: TODO

**AI use:** Claude (AI) built the quote form and the opening hours on the contact page, drew the Vanto 13 illustration, filled in this table and ran the validator and Lighthouse; I chose the topic and checked every change.

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
