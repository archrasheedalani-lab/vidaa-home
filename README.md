# VIDAA Home — custom launcher for Hisense VIDAA TVs

A single web page (`index.html`) you install on the TV through VIDAA's built-in debug installer.
It shows a clock, Hijri + Gregorian date, next prayer, Ramadan countdown, weather,
a favourites shelf, and a screensaver after 10 minutes idle. The background changes
with the time of day (dawn / day / sunset / night).

Built for VIDAA's old browser: no flex `gap`, no `inset`, no full-screen image animation.

## 1. Edit the settings (top of the `<script>` in index.html)

| Setting | What it does |
|---|---|
| `lang` | `'ar'` or `'en'` |
| `digits` | `'latn'` = 123, `'arab'` = ١٢٣ |
| `clock24` | `true` for 24-hour clock |
| `city` | name + latitude/longitude (default Dubai) |
| `prayerMethod` | 16 = Dubai, 4 = Umm al-Qura, 8 = Gulf, 3 = MWL |
| `screensaverMinutes` | idle time before the screensaver |
| `apps` | your tiles: `name`, `color`, and `url` if the app is a web app |

## 2. Host the page (pick one)

**A. GitHub Pages (recommended — no laptop needed afterwards)**
1. Create a free GitHub account → New repository (public) → upload `index.html`.
2. Settings → Pages → Branch: `main` → Save.
3. Your URL will be `https://<username>.github.io/<repo>/`.

**B. Your laptop on the same Wi-Fi (for testing)**
```
python3 -m http.server 8080
```
URL: `http://<laptop-ip>:8080/` — the laptop must stay on.

## 3. Install it on the TV

1. Open the **Browser** app on the TV.
2. In the address bar type `hisense://debug` and press OK.
3. Enter a name (e.g. `My Home`) and your URL from step 2 → **Install**.
4. Restart the TV if it doesn't appear; it shows at the end of the apps list.

If `hisense://debug` gives a blank page on your firmware, the community tool
**vidaa-edge** (github.com/weinzii/vidaa-edge) installs the same URL another way.

## Limits (honest)

- **Home button still goes to VIDAA's home.** VIDAA has no setting to replace it.
  Open this app from the apps list (move it to the first slot).
- **Native apps (Netflix, Prime, Shahid) can't be opened from a web page.** Those tiles
  show a hint; use the remote's app buttons. Tiles with a `url` (YouTube TV, Twitch,
  any website) open directly.
- **HDMI inputs** can't be switched from a web page.
- Full control (opening any app, switching inputs, auto-takeover of Home) needs an
  always-on computer running a bridge — see github.com/Zfinix/vidaa-launcher.

## Undo

Long-press the app in the apps list → Remove. Nothing on the TV is changed.

Data: prayer times and Hijri dates from api.aladhan.com, weather from open-meteo.com
(no keys, no accounts).
