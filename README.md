# Duebook

> [!CAUTION]
> **Spending rule: if this project spends more than US$10 in a day, stop and ask
> before doing anything else.**
>
> This binds every agent and every person, on every paid API: model calls,
> Places/Maps, email, storage, ads, build minutes. Say the running total, what it
> bought, and what the next step would cost. Then wait for a yes. Do not resume on
> your own judgment, and do not split work into smaller runs to stay under the line.
>
> - **The ceiling goes in before the loop does.** Anything that calls a paid API
>   more than once needs a hard maximum and a way to stop, written before the
>   first run, not after the first bill.
> - **A cap in the code is not a cap.** Set a budget alert and a quota ceiling in
>   the provider's own console as well. An application-level limit cannot survive
>   a bug in the application, and that is exactly when it is needed.
> - **Unmetered scripts are the hole.** A CLI, test or backfill that calls a paid
>   API without going through this project's meter spends money nothing counts.
>   If it costs money, it goes through the meter.
> - **Stop on the first sign of a runaway.** A retry storm, a loop that will not
>   terminate, a job that hangs: kill it and report. Never leave a process that
>   is spending money running while you investigate why.
>
> **Why this rule exists.** ZipQuarry spent roughly US$700 on Google Places
> between 2026-08-23 and 2026-09-02, on a product with zero users and zero
> revenue. Three failures stacked: the spend meter was written four days after
> the billing started; before that a pagination loop billed a request every 300ms
> until the process was killed by hand; and every request was on the most
> expensive Text Search tier. None of it was caught by a person, because nothing
> was watching and no console budget existed. The full postmortem is in
> `zipquarry-platform/docs/SPEND-INCIDENT-2026-08.md`.

**Bring customers back before they forget you.**

Most businesses are sitting on repeat customers they forgot to call or invoices
that haven't been paid. Duebook turns old customers into booked appointments and
recaptures that lost revenue.

It keeps every customer in one list, tells you who is due to come back, due to
renew, or due to pay, and writes the reminder email for you. Someone on your
team reads each one and clicks send. Nothing reaches a customer unless a person
approves it.

This repository contains the Duebook marketing site.

## Live site

https://melaniesigrid.github.io/duebook/

## What Duebook does

- **One list of who is due**: every customer who is due, why they are due, and how overdue they are, with the most overdue at the top.
- **A schedule for each service**: an oil change every six months and an inspection every year can sit on the same customer with separate dates.
- **Reminders written for you**: Duebook writes the email; staff change it, put it off, skip it, or send it.
- **Renewals, repeat visits, and unpaid invoices**: contract end dates, time since the last visit, and bills that have been sitting too long, all on one list.
- **Upload and download**: bring in a spreadsheet from whatever you use now, and take your data back out any time.

Built for auto shops, heating and plumbing companies, dentists, vets, med spas,
pest control, and gyms: any business where the next booking depends on
remembering the last one.

## Copy rules

Everything on the site must be understandable by a community college graduate.
Plain words, short sentences, no industry jargon (no "CRM", "intervals",
"recall", "pipeline"). Say what the app does for the owner, not how it works
inside. The anchor line is the one at the top of this file.

## Repository contents

| File | Purpose |
| --- | --- |
| `index.html` | The entire site: markup, styles, and scripts in one self-contained file |
| `404.html` | Not-found page, styled to match |
| `og-image.jpg` | 1200×630 share card for link previews |
| `favicon.svg` | Tear-off calendar mark used as the browser icon |
| `apple-touch-icon.png`, `icon-192.png`, `icon-512.png` | Home-screen and PWA icons |
| `site.webmanifest` | Web app manifest (name, icons, theme colors) |
| `robots.txt`, `sitemap.xml` | Crawler directives |
| `.nojekyll` | Tells GitHub Pages to serve files as-is, without Jekyll processing |
| `_dev/` | Sources the images are rendered from: see [`_dev/README.md`](_dev/README.md) |

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

- **Book a free call:** https://cal.com/northboundsoftwarestudio/scope-call
- **Email:** hello@northboundsoftwarestudio.com

---

Made by [Northbound Software Studio](https://northboundsoftwarestudio.com)
