# Tuza docs

The manual for creators using Tuza: https://docs.tuza.stream

Six pages, one per thing a creator actually has to do. The API reference is there
for the people who want to build against the overlay, not for the people who just
want their alerts working.

## Run it locally

```sh
python3 -m venv .venv && . .venv/bin/activate
pip install -r requirements.txt
mkdocs serve          # http://127.0.0.1:8000
```

`mkdocs build --strict` is what CI runs. It fails on a broken internal link, which
is the only kind of dead link a docs site can catch for itself.

## Layout

```
mkdocs.yml              nav, theme, extensions
requirements.txt        pinned, so a build cannot change under us
docs/index.md           start here
docs/overlay.md         the link, OBS setup, testing
docs/sounds.md          alert tiers, uploads, gift gating
docs/money.md           fees, settlement, payouts
docs/songs.md           Spotify and !play
docs/api/               endpoints, WebSocket payloads
.github/workflows/      build and deploy to Pages on push
```

## Deploy

Push to `main`. The workflow builds with `--strict` and publishes to GitHub Pages,
which is served under the custom domain `docs.tuza.stream` through Cloudflare.

The DNS record is proxied, and the zone SSL mode is Full. GitHub never issued its
own certificate for the custom domain, so Cloudflare terminates TLS and Pages stays
the origin. If that ever changes, set the record back to DNS only and let GitHub
provision.

## How these pages are written

- **Second person, short sentences.** "Paste the link into the URL field", not "the
  URL should be pasted".
- **The failure first, then the fix.** Say what the reader will see when it goes
  wrong before explaining the setting that prevents it.
- **Name the button that exists.** Every instruction refers to a label in the
  dashboard. If the UI changes, this repo changes in the same week.
- **No em dashes.** A colon or a full stop does the job.
- **No promise the product does not keep.** Payout timing, fee arithmetic and the
  temporary manual payout are stated as they are, because a creator who finds out
  later stops trusting the rest of the page.

## Adding a page

1. Write it in `docs/`.
2. Add it to `nav` in `mkdocs.yml`, or it exists and nobody can reach it.
3. Cross-link it from the page before it, so a reader arrives by following an
   instruction rather than by guessing.
4. Check it at 390px before you push. Most creators read this on a phone.
