# Development

## Run locally
This plugin is pure HTML/JS and uses MQTT over WebSocket (no Node build steps).

1. Open `com.schiewo.mqtt.toggle.sdPlugin/index.html` in a browser for quick UI checks.
2. For full testing, install the folder as a plugin on your device (Soomfon/Elgato).

## Release
Create a git tag (e.g. `v1.0.0`) and push. GitHub Actions will package
`com.schiewo.mqtt.toggle.sdPlugin` into a `.zip` and attach it to the Release.
