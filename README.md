
# Tasmota MQTT Plugin for Soomfon 

**by Schiewo**

---

## 🧩 What it does

This plugin lets your StreamDock **display live data from any Tasmota device** using MQTT —
for example: power usage, voltage, temperature, humidity, CO₂, and more.

It automatically detects what values your device sends and shows them directly on the key display.
No extra setup, no JSON parsing, no MQTT coding needed.

---

## ⚙️ Features

✅ Works with **all Tasmota-based devices**  
✅ Supports **MQTT over WebSocket**  
✅ **Auto-detects** ENERGY / SENSOR fields (W, V, °C, %, etc.)  
✅ **Auto language switch** (German 🇩🇪 / English 🇬🇧 — more coming soon)  
✅ Clean, modern **dark UI**  
✅ Easy setup – enter your device base once  
✅ Works on **Soomfon** hardware  

---



## 🧠 Mosquitto Setup

Before installing the plugin, make sure your MQTT broker is configured correctly.

Add the following lines to your Mosquitto configuration (for example in `/etc/mosquitto/conf.d/01-listeners.conf`):

listener 1883
protocol mqtt
allow_anonymous true

listener 9001
protocol websockets
allow_anonymous true

Then restart Mosquitto:
sudo systemctl restart mosquitto



Your broker is now ready, and you can connect using:
ws://<broker-ip>:9001

No `/mqtt` path is needed with this configuration.


## 🪄 Quick Setup

1. Make sure your **MQTT broker** supports WebSockets  
   (e.g. ws://127.0.0.1:9001 — or if your broker uses a WebSocket path, ws://192.168.x.x:9001/mqtt)

2. In the plugin:
   - Enter your **device base name** (e.g. `tasmota_D6763C`)
   - Click **“Fill from base”**

   → The plugin automatically fills your topics:
   ```
   stat/<base>/POWER
   cmnd/<base>/POWER
   ```

3. Choose what you want to display:
   - **Auto (recommended)**
   - Watt (W), Voltage (V), Temperature (°C), Humidity (%), etc.

4. Done!
   The key will now show the latest telemetry from your Tasmota device.

---

## 🌍 Language Support

| Language | Status  |
|-----------|----------|
| **English** | ✅ Default |
| **Deutsch (German)** | ✅ Auto-selected |
| Français, Español, Português, etc. | ➡️ Falls back to English automatically |

Your Soomfon language is detected automatically — no manual setting required.

---

## 🖼️ Screenshots

| Property Inspector (top) | Property Inspector (values) |
|---|---|
| ![PI top](screenshots/screenshot-2.png) | ![PI values](screenshots/screenshot-3.png) |

| Key grid (Watt) | Key grid (Voltage) |
|---|---|
| ![Key W](screenshots/screenshot-1.png) | ![Key V](screenshots/screenshot-4.png) |

---

## 🧠 Notes

- This plugin is **Tasmota-only** by design. (Generic MQTT devices are out of scope for stability.)
- All communication happens **locally over MQTT** – no cloud required.
- Tested with Tasmota 13.x+ and Mosquitto broker.

---

## 🧰 Installation (Soomfon)

1. Download this repository or the release ZIP  
2. Place your plugin folder alongside the docs:
   ```
   tasmota-mqtt-plugin/
    ├─ README.md
    ├─ LICENSE
    ├─ screenshots/
    └─ com.schiewo.mqtt.toggle.sdPlugin/
         ├─ manifest.json
         ├─ index.html
         ├─ mqtt.html
         ├─ images/
         │   ├─ brand.png
         │   └─ icon.png
         └─ lib/
             └─ mqtt.min.js
   ```
3. Re-zip the whole `tasmota-mqtt-plugin/` folder  to your plugins directory.

---

## 💬 Contribute / Test

If you want to help test or translate:
- Open a GitHub issue or pull request
- You can easily add your language in the built-in `I18N` block

---

## 🪪 License

MIT License — see `LICENSE` for details.

---

## ❤️ Credits

Created with ❤️ by **Schiewo**  
For the Soomfon StreamDock community.
