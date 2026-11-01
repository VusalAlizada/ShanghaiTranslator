# Shanghai Translator — Android

Three-language RU/EN/ZH translator with Shanghai phrasebook. Native Android Java application.

## Build APK
1. Install Android Studio (with Android SDK 35 and JDK 17).
2. Open this folder as a project and allow Gradle to sync. Internet is required for the initial Gradle/ML Kit dependency download.
3. Build > Build Bundle(s) / APK(s) > Build APK(s).
4. APK: `app/build/outputs/apk/debug/app-debug.apk`.

## Offline use
- Phrasebook is bundled and works offline immediately.
- Free-form translation uses Google ML Kit on-device translation. Each translation direction requires a model downloaded once while online. In the app select source and target and press `Загрузить языковую модель`. Once downloaded, the model is cached on-device and can be used without internet.
- For all 6 directions, download each pair/direction before travel. Model availability/download may depend on network access; test in airplane mode before departure.
- TTS uses Android's installed speech engine and may need separate offline voice data; translation itself does not depend on TTS.
- ML Kit translation quality may be lower than cloud translation, especially for long or nuanced text.

## Limitations
- This source project is not a prebuilt APK; build it in Android Studio as described above.

## Changes in 1.1
- Removed duplicate Kotlin DSL build files (`*.gradle.kts`) that conflicted with the Groovy ones (different package name, unused Kotlin plugin).
- Added Gradle wrapper (Gradle 8.11.1, compatible with AGP 8.7.3).
- targetSdk raised 28 → 34 (avoids the "built for an older version of Android" warning on new phones).
- Fixed a crash in phrasebook search on Android 6–7: `String.join` requires API 26, minSdk is 23.
- This version supports typed text and prepared phrases; microphone recognition and camera OCR are not included.
