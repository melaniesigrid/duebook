# Duebook

**Bring customers back before they forget you.**

Duebook is the repeat-customer engine for service businesses. It tracks customer
service dates, flags who is due for maintenance or renewal, and drafts reminder
emails your team reviews and sends — nothing goes out without a person approving it.

This repository contains the Duebook marketing site.

## Live site

https://melaniesigrid.github.io/duebook/

## What Duebook does

- **Due list** — every customer who is due, why they're due, and how overdue they are, in one ranked view.
- **Per-service intervals** — a six-month oil change and an annual inspection can live on the same customer with separate due dates.
- **Drafted reminders** — Duebook writes the reminder; staff edit, snooze, skip, or send.
- **Renewals and maintenance** — contract/membership end dates and interval-based service, tracked side by side.
- **Import and export** — bring in a spreadsheet from your current system; take your data back out any time.

Built for auto shops, HVAC and plumbing, dental and vet practices, med spas,
pest control, and gyms — any business where the next booking depends on
remembering the last one.

## Repository contents

| File | Purpose |
| --- | --- |
| `index.html` | The entire site — markup, styles, and scripts in one self-contained file |
| `favicon.svg` | Tear-off calendar mark used as the browser icon |
| `.nojekyll` | Tells GitHub Pages to serve files as-is, without Jekyll processing |

There is no build step and there are no dependencies. Fonts load from Google Fonts;
everything else is local.

## Running it locally

Open `index.html` in a browser, or serve the folder:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

## Deployment

The site deploys to GitHub Pages from the `main` branch, root directory.
Pushing to `main` publishes the change within a minute or so.

## Get in touch

- **Book a scope call:** https://cal.com/northboundsoftwarestudio/scope-call
- **Email:** hello@northboundsoftwarestudio.com

---

Made by [Northbound Software Studio](https://northboundsoftwarestudio.com)
