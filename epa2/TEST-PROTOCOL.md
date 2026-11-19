# Accessibility Test Protocol – Campus Café

EPA 2 · CM-501 Frontend Web Development · Yavuz Eren Yasar

- `before/` = the starter kit, not changed
- `after/` = my repaired pages

## C1 · Issues before and after

| # | Page | Problem before | WCAG | My fix |
|---|------|----------------|------|--------|
| 1 | both | No doctype, no `lang` | 3.1.1 | Added `<!DOCTYPE html>` and `lang="en"` |
| 2 | both | Both pages have the title "Home" | 2.4.2 | "Menu – Campus Café" and "Contact – Campus Café" |
| 3 | both | No viewport tag | 1.4.4 | Added the viewport meta tag |
| 4 | both | Menu and Contact are `div`s with `onclick`. You can't reach them with Tab. | 2.1.1, 4.1.2 | Real links in a `<nav>` list, `aria-current="page"` on the current page |
| 5 | both | Only `div`s, no landmarks, no skip link | 1.3.1, 2.4.1 | `header`, `nav`, `main`, `footer` and a skip link |
| 6 | both | `outline: none` hides the focus | 2.4.7 | Removed it and added a `:focus-visible` outline |
| 7 | both | Light grey text on white, dark text on the dark header | 1.4.3 | New colours with at least 4.5 : 1 |
| 8 | both | Social icons link to `#` and have no name | 2.4.4, 4.1.2 | Real links with `aria-label="Facebook"` and `aria-label="Instagram"`, icon has `aria-hidden="true"` |
| 9 | menu | Headings jump from `h1` to `h4` | 1.3.1 | `h1` for the page, `h2` for each section |
| 10 | menu | Layout table, `<font>`, `<b>`, `<i>` | 1.3.1 | Lists inside sections, `<strong>` for the names, prices as normal text |
| 11 | menu | Today's special is only inside an image with no `alt` | 1.1.1 | The special is now text, the image has `alt=""` |
| 12 | menu | `latte.jpg` has no `alt` | 1.1.1 | It is decoration, so `alt=""` |
| 13 | contact | Phone and e-mail are only inside an image | 1.1.1 | Text in `<address>` with `tel:` and `mailto:` links |
| 14 | contact | Map `iframe` has no title and loads Google right away (privacy) | 4.1.2 | Replaced by a link to Google Maps. Nothing loads until you click. |
| 15 | contact | The form heading is a `div` | 1.3.1 | Now an `<h2>` |
| 16 | contact | Fields only have a placeholder, no label | 1.3.1, 3.3.2 | A visible `<label>` for every field |
| 17 | contact | All fields are `type="text"`, no autocomplete | 1.3.5 | `email`, `tel`, `date` and `autocomplete` |
| 18 | contact | You can't see which fields are required | 3.3.2 | `required` and "(required)" in the label; e-mail hint linked with `aria-describedby` |
| 19 | contact | "Send" is a `div`. You can't reach it with Tab. | 2.1.1, 4.1.2 | A real `<button type="submit">` |
| 20 | contact | Field text and borders are too light | 1.4.3, 1.4.11 | Darker text, border and button |
| 21 | contact | No error messages | 3.3.1 | `required` and `type="email"`: the browser stops the form and shows a message |
| 22 | contact | The form uses `get`, so personal data goes into the URL | – (privacy) | `method="post"` |

## C2 · Automated tests

Tested on 18 Nov 2026: W3C validator, Lighthouse 12 and axe.

| Tool | Menu before | Menu after | Contact before | Contact after |
|------|-------------|------------|----------------|---------------|
| Validator errors | 14 | 0 | 2 | 0 |
| Lighthouse accessibility | 46 (screenshot) / 49 (new run) | 100 | 48 | 100 |
| axe violations | 7 | 0 | 7 | 0 |

- Validator before: no doctype, `img` without `alt`, 10 × `<font>`, `h1` → `h4`.
- axe before: low contrast, missing `alt`, links without names, no `lang`, no `main`, `iframe` without title.
- Screenshots: `screenshots/lighthouse-menu-before.png`, `screenshots/lighthouse-menu-after.png`.

The tools did **not** find these problems on the old contact page: fields with only a placeholder, the `div` "Send" button, no autocomplete and the phone number inside the image.

## C3 · Manual tests

**Keyboard (Tab and Shift+Tab)**

| Page | Before | After |
|------|--------|-------|
| menu | Only the two empty social links get focus, and you can't see the focus. Menu and Contact can't be reached. | Skip link → Menu → Contact → Facebook → Instagram. The focus is always visible. |
| contact | Only the fields and the empty social links get focus. Menu, Contact and "Send" can't be reached. | Skip link → Menu → Contact → phone → e-mail → map link → all fields → Send → social links. The focus is always visible. |

**Screen reader:** Windows Narrator (Ctrl + Win + Enter), plus the accessibility tree in Chrome DevTools

| Task | Before | After |
|------|--------|-------|
| What is today's special and what does it cost? | Not possible: it is only in an image with no `alt` | "Pumpkin Spice Latte 3,90 € – only until 4 pm!" as text under the heading "Today's special" |
| How much is a flat white? | The text is there, but the headings are `h4` and there is no list | Heading "Coffee", level 2, list item "Flat White 3,60 €" |
| Find the café's phone number | Not possible: it is only in an image | Link "+49 89 000 000 00" |
| What is said on the e-mail field? | Only "E-Mail" (the placeholder), not said as required | "E-mail (required)", the field is required, then the hint "We send the newsletter and your reservation to this address." |
| Headings list | menu: Menu, Coffee, Tea & more, Food (levels 1 → 4) | menu: Menu (1), Today's special, Coffee, Tea & more, Food (2); contact: Contact (1), Newsletter & reservations (2) |

**Zoom 200 %:** All text gets bigger and stays readable. Nothing overlaps. The page is fixed at 1100 px, so you have to scroll sideways to see the Menu and Contact links. Responsive layout is part of EPA 3.

**Reduced motion:** The pages have no animations, so there is nothing to turn off.

## C4 · Peer test

Tester - Haluk. Screen reader - Narrator. Screen reader tested.

What Haluk found and what I did

1. Both pages, the skip link can not be seen when it gets focus. WCAG 2.4.7, 2.4.11, serious. He was right, the skip link was behind the header. I added `z-index: 1` to `.skip:focus`, now it shows on top.
2. Both pages, at 200 % zoom you have to scroll sideways. WCAG 1.4.10, serious. I did not change this. The page is fixed at 1100 px and the brief says the layout may stay, responsive layout is part of EPA 3.
3. Both pages, the social links are called Campus Café on Facebook and Instagram, but they go to the Facebook and Instagram home pages. WCAG 2.4.4, minor. I changed the names to Facebook and Instagram.

Haluk liked the clear labels and prices.

## C5 · Limits of the tools

Tools can only check simple rules, like a missing `alt`, a missing label or low contrast. They can't tell if an alt text or a link name makes sense. They also don't use the keyboard. On my old contact page, axe did not report the fields with only a placeholder or the `div` "Send" button. I found these only with the keyboard and the accessibility tree. A score of 100 does not prove that a page is accessible.

## AI use

I used an AI assistant to explain WCAG and CSS, to review my code, to help me when I was stuck and to improve the language of this protocol.

