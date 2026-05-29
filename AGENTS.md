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

While testing, you can trigger recording of the Android screen:
```bash
lim android record start
```

Once the test is completed, you can have it written to a file you can show to user or upload:
```bash
lim android record stop -o recording.mp4
```

See what's available with `lim android --help`
