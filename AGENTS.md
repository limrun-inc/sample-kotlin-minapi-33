# AGENTS

For testing the app, always use the `lim` CLI which provides remtoe Android Emulator
through `adb` tunnel.

Install `lim`:
```bash
npm install -g lim
```

Ensure `LIM_API_KEY` exists either as environment variable or in `.env` files.

## Development flow

Once you have an APK file, you can get an emulator from Limrun:

```bash
lim android create
```
This will start the `adb` tunnel automatically. Also, it will return a signed stream URL
that you can open in the browser to or tell user to open in their browser to stream the
Android screen.

You can install your APK with the following command:
```bash
lim android install-app <path to apk file>
```

For quick tests, you can use `lim android` commands like tapping, screenshots, element tree etc.

See what's available with `lim android --help`

## Cursor Cloud specific instructions

### Environment

- **Android SDK** is installed at `/opt/android-sdk` with `platform-tools`, `platforms;android-36`, and `build-tools;36.0.0`.
- Environment variables (`ANDROID_HOME`, `ANDROID_SDK_ROOT`, `PATH`) are set in `~/.bashrc`.
- `local.properties` (with `sdk.dir`) is auto-generated and gitignored.
- **JDK 21** is the system default (required by Gradle daemon JVM config).
- **Gradle 9.4.1** is managed via the wrapper (`./gradlew`); no global install needed.

### Key commands

| Task | Command |
|------|---------|
| Build debug APK | `./gradlew assembleDebug` |
| Run unit tests | `./gradlew test` |
| Run lint | `./gradlew lint` |
| Install on emulator | `adb install app/build/outputs/apk/debug/app-debug.apk` |
| Launch app | `adb shell am start -n com.limrun.samplekotlin33/.MainActivity` |

### Gotchas

- The first Gradle build downloads the Gradle distribution (~200 MB) and SDK platform packages; subsequent builds are fast (~3-4s for incremental).
- `lim android create` starts the ADB tunnel automatically as a background process; no extra `adb connect` is needed.
- Use `lim android screenshot <path> --id <instance-id>` for capturing screenshots.
- When done testing, clean up emulator instances with `lim android delete <instance-id>` to avoid stale resources.
