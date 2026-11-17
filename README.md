# cm501-yavuz

My coursework for **CM-501 Frontend Web Development** at MUDT. Every page in this repository is plain HTML and CSS written by hand, without frameworks or site builders.

## Repository layout

| Path | Contents |
|---|---|
| `index.html`, `about.html` | EPA 1: my personal profile site |
| `epa1-report/` | EPA 1: delivery report on burulas.com.tr |
| `epa2/` | EPA 2: accessibility repair of the Campus Café menu page |
| `session-3/`, `session-4/` | Lab pages from the sessions |
| `worksheets/` | Lab worksheets and homework |

## Assessments

### EPA 1 · Profile site

A small two-page site about me: `index.html` lists websites I love and hate, `about.html` tells a bit about me and my hobbies. The pages link to each other.

Live: https://yavuzerenn.github.io/cm501-yavuz/

### EPA 1 · Delivery report

A DevTools and Lighthouse analysis of https://www.burulas.com.tr (totals, largest files, images, third parties, render-blocking and unused code, headers): [epa1-report/REPORT.md](epa1-report/REPORT.md)

### EPA 2 · Repair the Campus Café

The café pages were handed out broken on purpose. My job is to make them semantic and accessible (WCAG 2.2 AA).

- `epa2/before/` is the starter kit exactly as it was handed out
- `epa2/after/` is my repaired version
- `epa2/TEST-PROTOCOL.md` is my test protocol
- `epa2/screenshots/` holds the Lighthouse results before and after the repair

## Labs

| Path | Contents |
|---|---|
| `session-3/events-fixed.html` | Lab D: the events page rebuilt with semantic elements |
| `session-4/workshop-booking-fixed.html` | Lab F: an accessible booking form |
| `session-4/workshop-booking-error.html` | Lab F2: the same form with error messages |
| `worksheets/` | Session 2 and 3 lab worksheets, detective sheets homework (burulas.com.tr compared with gov.uk across six lenses) |

## Running it locally

You can open any `.html` file straight in the browser. To get the same paths as on GitHub Pages, start a small server in the repository folder:

```
python -m http.server 8080
```

and open http://localhost:8080/ in the browser.

## Author

Yavuz Eren Yasar, MUDT
