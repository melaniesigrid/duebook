# _dev — asset sources

These files are not served. They're the sources the shipped images are rendered
from, kept in the repo so the assets can be regenerated instead of redrawn.

Rendering uses gstack `browse` (headless Chromium) plus macOS `sips`. From the
repo root:

```bash
B="$HOME/.claude/skills/gstack/browse/dist/browse"
```

## og-image.jpg (1200×630)

Source: `og-image-template.html`. The share card for Slack, iMessage, LinkedIn, X.

```bash
$B viewport 1200x630 --scale 2
$B goto "file://$PWD/_dev/og-image-template.html"
$B screenshot /tmp/og.png --clip 0,0,1200,630
sips -s format jpeg -s formatOptions 88 -z 630 1200 /tmp/og.png --out og-image.jpg
```

Rendered at 2× and downsampled so the type stays crisp. Keep it at exactly
1200×630 — that's the aspect ratio every scraper crops to.

## icon-512.png, icon-192.png, apple-touch-icon.png

Source: `icon-template.html` — the tear-off calendar mark on Duebook paper.

```bash
$B viewport 512x512 --scale 2
$B goto "file://$PWD/_dev/icon-template.html"
$B screenshot /tmp/icon.png --clip 0,0,512,512
sips -z 512 512 /tmp/icon.png --out icon-512.png
sips -z 192 192 /tmp/icon.png --out icon-192.png
sips -z 180 180 /tmp/icon.png --out apple-touch-icon.png
```

`favicon.svg` is hand-authored to match the same mark, not rendered.

## After regenerating

Social platforms cache OG images aggressively. If you change `og-image.jpg`,
re-scrape the URL in each platform's debugger, or the old card keeps showing.
