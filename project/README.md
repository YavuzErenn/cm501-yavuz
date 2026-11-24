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
| M4 | one `h1` per page, no skipped heading levels | index.html · `h1` l. 31 → `h2` l. 37, 62 → `h3` l. 41–73; contact.html · `h1` → `h2` "Request a quote", "Opening hours of the workshop"; models.html · `h1` → `h2` Motorhomes / Towed caravans; about.html · `h1` → `h2` workshop, team, FAQ → `h3` team names |
| M5 | images: `alt` (or `alt=""`), `width`/`height`, `loading="lazy"` below the fold; one `figure` + `figcaption` | index.html · `figure` + `figcaption` with `img/vanto-13.svg`, descriptive `alt`, `width`/`height` 640×360, `loading="lazy"` (l. 55–58); models.html · floor plan `figure` with `img/vanto-13-floorplan.svg` (l. 91–94) |
| M6 | lists for lists; `article`/`section` with headings where they fit | index.html · two `section`s (l. 36, 61), each a `ul` of `article`s (l. 38–78); about.html · team as a `ul` of `article`s (l. 39–59) |
| M7 | meaningful link texts; `<address>` with `tel:` / `mailto:` links | index.html · links "Compare our motorhome sizes", "See our caravan models"; `<address>` l. 83 with `tel:` l. 86, `mailto:` l. 87 |
| M8 | `<time datetime="…">` for at least one date or time | index.html · trade fair dates l. 67, 74; contact.html · opening hours (l. 101–108) |
| M9 | one form: visible labels, right `type`, `autocomplete`, "(required)" + `required`, real `<button>`; `fieldset`/`legend` for groups | contact.html · quote form (l. 35–96): visible labels, `type="email"` / `tel`, `autocomplete` (name, email, tel, address-level2), "(required)" + `required`, hints with `aria-describedby`, `fieldset`/`legend` for the radio group (l. 57), privacy checkbox, `<button>` "Send quote request" |
| M10 | W3C validator 0 errors · axe 0 violations · keyboard: everything reachable, focus visible | all 4 pages · W3C validator 0 errors, Lighthouse accessibility (axe) 100; keyboard: see Tests |
| O1 | responsive image: `srcset` + `sizes` or `<picture>` | not planned |
| O2 | data table with `<caption>` and `<th scope>` | models.html · two tables with `<caption>`, `<th scope="col">` and `<th scope="row">` (l. 35, 101) |
| O3 | `<details>` / `<summary>` (e.g. FAQ) | about.html · FAQ with five `<details>` / `<summary>` (l. 64–87) |
| O4 | `<dl>` for name–value pairs (e.g. opening hours, facts) | contact.html · opening hours as `<dl>` with `<time>` (l. 101–108) |
| O5 | `<blockquote>` with source, `<abbr>` with the expansion written out once | not planned |
| O6 | icon-only link or button with `aria-label` and `aria-hidden="true"` on the icon | not planned: the fictional company has no social media accounts to link to |
| O7 | `<iframe>` with `title` (map, video), privacy considered | not planned |
| O8 | `lang` on a passage in another language (e.g. `<span lang="de">`) | index.html l. 34 · `<span lang="tr">` motto |

**Tests:** validator: 2026-11-17, 0 errors and 0 warnings on all 4 pages · axe (via Lighthouse 13.5 accessibility): 100 on all 4 pages, 0 violations · keyboard (2026-11-18, local files): skip link is the first Tab stop, every link, field and the button are reachable with Tab, focus is always visible, the radio group is one Tab stop and the options change with the arrow keys · screen reader: TODO

**AI use:** I used an AI assistant to explain HTML and to review my code. It also generated the models and the people for the site (model specs, floor plan, team and FAQ), the quote form and the Vanto 13 drawing. I chose the topic, checked every change and can explain every line.

## Design (EPA 3)

Vanto is for couples and families who dream of travelling by van, so the site should feel warm, handmade and ready for the road. The colours come from our Vanto 13 drawing: burnt orange for buttons, forest green for links and the focus ring, and a warm off-white and sand background; every text colour has at least 5 : 1 contrast, and dark mode only changes the colour tokens. I use system fonts, so nothing has to download on slow mobile data, and fluid headings with `clamp()` and a line length of at most `65ch` keep the text readable. The home page is mobile first, with Grid for the page layout and Flexbox inside the header, cards and footer. It changes at 40rem (intro text and motto side by side) and 60rem (the cards next to the drawing), because that is where the content has room. All colours, font sizes and spaces are tokens in `style.css` and documented in `styleguide.html`. The pages were tested at 320, 768, 1280 and 1920 px and at 400 % zoom in light and dark mode (no horizontal scrolling), contrast was calculated with the WCAG formula, and both pages pass the W3C validator. AI use: I built the design step by step with an AI assistant: I chose the colours, fonts, dark mode and plain CSS, the assistant wrote the CSS and the style guide, and I reviewed each part, had it simplified to what we learned in class, and tested it.

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
