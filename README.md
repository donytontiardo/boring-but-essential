# Stand-Up Timer

Reminds you to stand up while you work. You sit for a set block, it tells you to stand, and it counts how often you did today.

- Routines: 20·8·2 (sit 20, stand 8, move 2), 30·5, 45·5, 50·10, or your own minutes.
- When a sitting block ends it chimes, shows **STAND UP** and keeps nagging until you tap **I'm standing**. You can snooze for 5 minutes.
- A running timer survives closing the page or app.

## Android app

Every push to `main` builds an APK with GitHub Actions and attaches it to the
[Latest APK release](../../releases/tag/apk-latest).

To install: open that release page on your phone, download `stand-up-timer.apk`, and allow
"Install unknown apps" for your browser when Android asks. On first start, allow notifications.
The app schedules real phone notifications, so reminders arrive even when the app is closed.

The APK is a debug build signed with a debug key. It is fine for your own phone but not for the Play Store.

## Web version

Open `www/index.html` in Chrome, Edge or Firefox and keep the tab open. Tick
**Desktop notification** to get pop-ups.

## Project layout

- `www/index.html` is the whole app (HTML, CSS, JS, no build step).
- `capacitor.config.json` and `package.json` wrap it as an Android app with
  [Capacitor](https://capacitorjs.com) and its Local Notifications plugin.
- `.github/workflows/android.yml` generates the Android project and builds the APK.

To build locally you need Node 22, JDK 21 and the Android SDK:

```sh
npm ci
npx cap add android
npx cap sync android
cd android && ./gradlew assembleDebug
```
