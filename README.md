# Hand Control

Use a phone with your hand instead of your fingers. The front camera watches one hand, a small dot follows the middle of it, and closing your fist presses whatever the dot is on.

## Download the app

- **Download page:** <https://site-161fe0c8bd6b447d8812ca0ec7d53b1f.freebuff.page/setup> — the file plus the install steps, with a picture of every screen.
- **Direct file:** <https://site-161fe0c8bd6b447d8812ca0ec7d53b1f.freebuff.page/app.apk> — about 29 MB, Android 8+, 64-bit phones.

The link downloads immediately. If the phone warns about the file, keep it, allow installs from the browser, then open the APK. On a Samsung, turn off **Auto Blocker** first (Settings → Security and privacy), otherwise it refuses every app that is not from the Play Store.

## The dot

The dot is deliberately small — 24 px on the web page, a 12 dp ring in the app — so it marks a spot instead of covering it. On the web page a fist is a real press anywhere: links open, buttons work, fields focus.

## Two versions

- **Android app** — the real one. Works inside the app, and optionally over other apps such as YouTube, TikTok and Instagram.
- **Web page** — the same gestures in a browser, no install, at <https://site-161fe0c8bd6b447d8812ca0ec7d53b1f.freebuff.page>. A web page can only press things on itself, so YouTube needs the app.

## How the gestures work

- The dot follows the **middle of the hand** (wrist plus the four knuckles), not a fingertip, so closing the hand does not drag the aim.
- A **fist presses**. Every finger has to curl in: the finger still sticking out decides, so a two-finger pinch presses nothing.
- A press happens only when a fist **closes**. The hand must open again before the next press counts, plus a pause, so holding a fist presses once.
- A quick **swipe** of an open hand up or down scrolls.
- **Fist sensitivity** sets how closed the hand must be. The readout shows the least curled finger against that limit, so tuning is copying a number rather than guessing.

## Privacy

Camera frames are processed on the phone and thrown away. Nothing is recorded, and the Android app declares **no internet permission** at all, so it cannot send anything anywhere.

## Control other apps (YouTube, TikTok, Instagram)

Press **Control other apps (YouTube)** in the app. It needs two permissions you grant yourself:

- **Display over other apps** — so the dot can float above the app you are using.
- **Hand Control** under **Accessibility** — the only thing Android allows an app to use to press the screen for you.

Both are switched on in Android Settings, never silently. Until both are on, the button tells you which one is missing. A notification stays in the shade while that mode is running.

## Building it yourself

The hand model (`hand_landmarker.task`, about 7.8 MB) is not committed here. Download it once:

```sh
curl -L -o hand-control/app/src/main/assets/hand_landmarker.task \
  https://storage.googleapis.com/mediapipe-models/hand_landmarker/hand_landmarker/float16/1/hand_landmarker.task
```

Then, with JDK 17 and the Android SDK:

```sh
cd hand-control
./gradlew assembleDebug
```

The APK lands in `hand-control/app/build/outputs/apk/debug/app-debug.apk`.
