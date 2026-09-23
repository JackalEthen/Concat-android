<div align="center">

<table width="100%">
  <tr>
    <td align="left" width="120">
      <img src="https://cdn.jsdelivr.net/gh/jub0t/Concat@main/assets/logo-dark.png" alt="Concat" width="100" />
    </td>
    <td align="right">
      <h1>Concat for Android</h1>
      <h3 style="margin-top: -10px;">The truly free, open-source video editor — rebuilt for your pocket.</h3>
    </td>
  </tr>
</table>

<p>
  <a href="README-zh.md">简体中文</a> ·
  <b>English</b>
</p>

<p>
  <img src="https://img.shields.io/badge/Platform-Android%20arm64-c6f432?style=flat&logo=android&logoColor=F8F8F8&labelColor=000000" alt="Platform: Android arm64" />
  <img src="https://img.shields.io/badge/UI-Compact%20Mode-c6f432?style=flat&labelColor=000000" alt="UI: Compact Mode" />
  <img src="https://img.shields.io/badge/Languages-14-c6f432?style=flat&labelColor=000000" alt="Languages: 14" />
  <img src="https://img.shields.io/badge/License-AGPL%20v3-c6f432?style=flat&logo=gnu&logoColor=F8F8F8&labelColor=000000" alt="License: AGPL v3" />
</p>

</div>

---

## About

This is the Android home of [Concat](https://github.com/jub0t/Concat) —
the truly free, open-source cross-platform CapCut replacement. The
desktop engine is unchanged; what this fork adds is a **phone-first
compact interface** and the Android-specific engineering that makes a
video editor actually usable in one hand.

Phone screens are not small desktops. Squeezing a timeline editor into
a portrait window makes every target smaller than a fingertip. So
instead of shrinking the desktop layout, compact mode gives Concat a
**second layout, designed from the phone up** — same engine, same
project files, a UI that behaves the way thumbs do.

No watermarks. No paywalls. No account. 100% local.

## Compact mode

A window narrower than 860 px — which is every phone — switches to the
compact layout automatically. Rotate or widen the window and the
desktop layout returns exactly as it was.

<table>
<tr><td width="50%">

### 🎛️ Two-row transport

Play, split and the timecode live in a fixed two-row bar with generous
touch targets, centred by stretch spacers. No pinch-zooming to hit
play.

</td><td width="50%">

### 🎚️ Track headers that fit a hand

A fixed 44 px header column per track carries lock / show / mute
switches. Long-press opens a scrim overlay with the remove action —
no buried context menus.

</td></tr>
<tr><td>

### 📑 The panel drawer

The edit area holds at most two panels; everything else parks in a
drawer. Tap ↑/↓ on a parked row to take a seat — the displaced panel
parks itself back. The last seat refuses to close.

</td><td>

### 🍔 An icon title bar

A hamburger replaces the three text menus, the project name sits
inline, and the logo opens the drawer. No window buttons — Android
already has them.

</td></tr>
<tr><td>

### 👆 Gestures that respect children

A vertical swipe scrolls the panel stack even when a child control
handles its own gestures.

</td><td>

### 🧭 Two-level settings

Settings navigates in two levels instead of one endless page, and
modals are clamped to the window.

</td></tr>
</table>

## Android-specific engineering

Beyond the layout, this fork fixes what only shows up on phones:

- **CJK text renders everywhere.** Some ROMs (Huawei, OPPO) ship font
  configurations a third-party font stack cannot match — Chinese
  glyphs boxed while Japanese rendered fine. Concat bundles
  *Noto Sans CJK* (SIL OFL) in the APK, stages it before the font
  collection is built, and appends it to every script's fallback
  chain. All 14 interface languages render correctly, on any ROM.
- **Document picking, natively.** The system file picker is reached
  through a small Java fragment compiled into the APK — picked files
  are copied into app storage and handed to the editor by path.
- **Logging that survives the cable.** Everything the window prints
  goes to `logcat` (tag `concat`) *and* to a log file reachable from
  Settings — because a phone in somebody's hand has no cable.
- **Hardware decoding stays optional.** The decode-on-hardware switch
  is right there in settings.

## Building it yourself

You will need the Android SDK + NDK, a Rust `aarch64-linux-android`
target, and about an hour the first time.

```bash
cd src
cargo apk build -p concat-android --target aarch64-linux-android
adb install target/debug/apk/Concat.apk
```

FFmpeg and the engine cross-compile from source (`src/scripts/`);
sherpa-onnx and Skia come from their prebuilt releases.

## Credits & license

- **Upstream project**: [jub0t/Concat](https://github.com/jub0t/Concat) —
  the desktop engine, and this fork's reason to exist.
- **Font**: [Noto Sans CJK](https://fonts.google.com/noto) by Google,
  SIL Open Font License.
- Licensed **AGPL-3.0-or-later**, same as upstream. Contributions
  welcome.

---

<div align="center">
<sub>No watermarks · No paywalls · No account · 100% local</sub>
</div>
