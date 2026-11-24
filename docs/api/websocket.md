# Alerts over WebSocket

Open a WebSocket to `/ws` with your overlay token. The server sends one JSON object per
alert. There is no subscription message and no handshake: if the connection is open, you
are subscribed to that streamer's alerts.

## A tip

```json
{
  "type": "tip",
  "name": "Wanjiku",
  "amount": 50000,
  "message": "for the stream",
  "tier": "big",
  "occurred_at": "2026-11-24T18:02:11Z"
}
```

`amount` is minor units, so 50000 is KES 500. `tier` is `default`, `small` or `big`, and
it is decided by the server, not the client, so two overlays never disagree about which
sound to play.

## A gift

```json
{
  "type": "gift",
  "name": "Brian",
  "gift": "Rose",
  "gift_count": 3,
  "coins": 120,
  "occurred_at": "2026-11-24T18:03:40Z"
}
```

Gifts carry coins, not money, because coins are not money. Nothing in this event should
be added to a balance.

## Reconnecting

Assume the connection drops: laptops sleep, wifi flaps, a host reboots. Reconnect with
backoff and expect no replay. An alert is for the moment it happened, so a client that
comes back five minutes later should not play five minutes of missed sounds at once.
