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
This will start the `adb` tunnel automatically.

You can install your APK with the following command:
```bash
lim android install-app <path to apk file>
```

For quick tests, you can use `lim android` commands like tapping, screenshots, element tree etc.

See what's available with `lim android --help`
