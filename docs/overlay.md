# Your overlay

The overlay is the part of Tuza your viewers see. It is a web page, and OBS can show a
web page. That is the whole mechanism.

## Get the link

1. Open your [Tuza dashboard](https://app.tuza.stream).
2. Find **Your overlay link** and press **Copy URL**.
3. Keep the tab open the first time, so you can send a test alert while OBS is running.

You will see three more links below it: **Alerts only**, **Now playing only** and
**Up next only**. Most streamers never need them. The main link already contains all
three, and that is deliberate: one link to paste, not three to arrange.

## Put it in OBS

1. In OBS, add a source and choose **Browser**.
2. Paste the link into the URL field.
3. Set the width to **1920** and the height to **1080**.
4. Tick **Shutdown source when not visible** off, and **Refresh browser when scene
   becomes active** off. A refresh reloads the page and loses an alert that was
   mid-animation.
5. Press OK.

Nothing else is required. There is no plugin, no scene collection to import, and no
second URL for sounds.

## Prove it works

Press **Test alert** in the dashboard. You should see the alert card on stream within a
second, and hear the sound if you have one.

If the card appears but you hear nothing, the problem is audio, not the overlay: OBS
captures browser audio only when the source has **Control audio via OBS** enabled, or
when the source is inside a scene with audio monitoring on.

If nothing appears at all, check the source is visible in the scene you are actually
streaming, and that the URL in OBS still matches the one in your dashboard. If you
rotate the link, the old one stops working on purpose.

## Changing where alerts sit

The dashboard has a position grid and four presets: **Vertical stream**, **Corner
alerts**, **Centre stage** and **Top banner**. Pick one, adjust the size, press **Save
overlay look**. The overlay updates on its next alert, so you do not need to reload OBS.
