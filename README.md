# Game Clock

A pitch-side game clock and flagging tool for hockey. Built to live on a phone home screen, work with no signal, and hand a coded timeline straight to Sportscode.

## What it does

- Counts **down** from the quarter length, so it reads the same as the scoreboard
- Wall-clock anchored, so a locked phone or a reloaded tab still reads the right time
- Stamps the time of day each quarter starts and each flag is tapped
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

### Lining up with video

Two ways, and the first is exact.

1. **Video start, clock time.** Every flag carries the real time of day it was tapped. Enter the wall clock time your recording started and each clip lands on the right frame, no matter how long the quarter breaks ran. **Use Q1 start** fills the field with the time you pressed start on Q1, which is right if you started recording at the same moment.
2. **Fine tune.** A seconds nudge applied to every clip, for when the recording start is a few seconds out.

Leave the video start blank and clips fall back to cumulative game time, which assumes no gap between quarters.

The XML carries a comment block listing all four quarter start times, and each instance gets a **Time of day** label.

## Files

| File | Purpose |
| --- | --- |
| `index.html` | The whole app, no dependencies |
| `manifest.webmanifest` | Home screen name, icon and full screen behaviour |
| `sw.js` | Service worker, caches the app so it opens offline |
| `icon-*.png` | App icons |

## Updating

Edit `index.html`, bump `CACHE` in `sw.js`, commit. Phones pick the new version up next time they open with signal.
