# API reference

This section is for developers: the overlay is a web page, so everything it does is
reachable over HTTP and WebSocket. If you are a streamer setting up your channel, you do
not need this page.

## What exists today

| Surface | What it is for |
| --- | --- |
| `GET /api/overlay/song` | what is playing now |
| `GET /api/overlay/queue` | the next requests |
| `WS /ws` | alerts, pushed as they happen |

All overlay endpoints take the token from your overlay link. Treat that link as a
password: anyone holding it can watch your alerts, so rotate it if it leaks.

## Conventions

- Money is returned as integer minor units. 10050 means KES 100.50. Never a float.
- Timestamps are RFC 3339 in UTC.
- Errors are JSON with a `code` and a human sentence, so a client can show the sentence
  without inventing one.
