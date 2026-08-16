# Game Clock

A pitch-side game clock and flagging tool for hockey. Built to live on a phone home screen, work with no signal, and hand a coded timeline straight to Sportscode.

## What it does

- Wall-clock anchored timer, so a locked phone or a reloaded tab still reads the right time
- Four quarters, adjustable quarter length
- Two teams with editable names and colours, so it works for any fixture
- Eight tagged flag buttons, four per team, with editable labels
- Corner and Goal buttons that stop the clock and auto restart after 40 seconds
- Undo on the confirmation toast, plus a full log you can edit
- Keeps the screen awake while you use it
- Exports XML for Sportscode, CSV for a spreadsheet, plus copy and share

## Install on a phone

1. Open the live URL in Safari on iPhone, or Chrome on Android
2. iPhone: Share, then **Add to Home Screen**. Android: menu, then **Install app**
3. Open it from the home screen icon. It runs full screen and works offline

## Export

The XML export writes one instance per flag:

- `code` is `Team Action`, for example `Wales Press`, so each combination gets its own timeline row
- label groups for **Team**, **Action**, **Quarter** and **Game clock**
- a `ROWS` block that colours each row to match the team colour in the app
- `start` and `end` come from the flag time, minus the lead in and plus the lag out

Set **video offset** to the number of seconds between your video starting and Q1 starting, and the instance times line up with the footage.

## Files

| File | Purpose |
| --- | --- |
| `index.html` | The whole app, no dependencies |
| `manifest.webmanifest` | Home screen name, icon and full screen behaviour |
| `sw.js` | Service worker, caches the app so it opens offline |
| `icon-*.png` | App icons |

## Updating

Edit `index.html`, bump `CACHE` in `sw.js`, commit. Phones pick the new version up next time they open with signal.
