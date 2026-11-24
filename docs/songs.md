# Song requests

A viewer pays, and their song joins the queue on your Spotify.

## Connect Spotify

Connect your account in the dashboard. Tuza needs permission to add to your queue, and
nothing else: it cannot read your playlists, and it never plays anything you did not
approve.

Spotify Premium is required, because the queue control is a Premium feature on their
side.

## Two ways in

**From the tip page.** A viewer pays for a request, adds the song, and it joins the
queue. The overlay shows what is playing and what is next.

**From chat.** Your viewers can type `!play <song>` if you turn chat requests on. Set a
per-viewer cooldown, and optionally a minimum gift, so one person cannot fill the queue.

## When it cannot play

Track not found, region locked, or already at the top of the queue: the viewer sees a
plain reason, not a spinner. Refunds follow the payment processor's rules, which are
shown on the tip page.

## The overlay parts

The **Now playing** and **Up next** widgets are separate pages if you want them placed
differently, and both are already inside your main overlay link. Most streamers use the
main link and move the widgets with the position grid.
