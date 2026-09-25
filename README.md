# Roller Blind Calibrator

A standalone, browser-based Web Bluetooth application to calibrate end limits (Upper & Lower) for compatible electronic roller blind motors without needing specialized remotes, proprietary gateways, or contractor installer accounts.

### 🌐 Live Web App (GitHub Pages)
👉 **[https://trafgals.github.io/blinds/](https://trafgals.github.io/blinds/)**

*(Open in Google Chrome on your Android phone, Windows, Mac, or Linux)*

---

## Features

- **📷 QR Code Scanner**: Scan the pull-off label sticker with your phone camera or upload a photo to automatically parse the Bluetooth MAC (`EUI48`), PIN Code, Zigbee IEEE (`EUI64`), and Install Code.
- **🔄 Auto-Derived EUI Addresses**: Automatically calculates Zigbee IEEE 64-bit (`EUI64`) from Bluetooth 48-bit MAC (`EUI48`) and vice versa.
- **⚡ Web Bluetooth (BLE)**: Connects directly from your browser to the motor's Bluetooth Low Energy interface. No gateway or app installation required.
- **🛡️ Safe Micro-Step Inching**: Calibration sends discrete 60ms–250ms movement pulses. The motor will **never run away continuously**, eliminating any risk of tearing fabric or jamming mechanical gears.
- **🔄 Direction Verification**: Test Up/Down rotation and invert motor direction with one tap.
- **💾 Multi-Blind Profiles**: Save multiple blinds (e.g. *Living Room 1*, *Living Room 2*, *Kitchen*) directly in your browser's local storage.
- **🐙 One-Click Diagnostic Export**: Copy, export, and stream live activity logs directly into GitHub issues for troubleshooting.
- **📱 PWA Ready**: Installable as a Progressive Web App on your phone home screen for offline use.

---

## How to Calibrate Your Blind

### 1. Wake the Motor
Press and hold the **action / programming button on the motor head for 2 seconds** until the blind does a single quick jog (up and down). This unlocks the motor and broadcasts Bluetooth for pairing.

### 2. Scan or Select Blind
- Open the [web app](https://trafgals.github.io/blinds/) in Google Chrome.
- Tap **📷 Camera QR Scan** (or **🖼️ Upload Sticker**) and scan the pull-off label that came with your blind.
- Tap **Save Profile**.

### 3. Connect via Bluetooth
> [!TIP]
> **Android Users**: Modern Android requires OS-level Bluetooth link-layer pairing before allowing motor movements. If you see `GATT operation not permitted`:
> 1. Open phone **Settings > Connected devices > Pair new device**.
> 2. Select the motor from the list.
> 3. Enter your blind's 6-digit PIN when prompted.
> 4. Return to Chrome and tap **⚡ Scan & Pair Bluetooth**.

- Tap **⚡ Scan & Pair Bluetooth**.
- In the browser dialog, select your blind motor.
- The app connects to the GATT server and authenticates with the PIN code from the label.

### 4. Set Limits
1. **Check Direction**: Tap **Jog Up**. If the blind moves down, tap **Invert Rotation Direction**.
2. **Set Upper Limit**:
   - Tap **Jog Up** to inch the blind to the desired top position (leave a safe 5–10 mm buffer below the top cassette).
   - Tap **Confirm & Save UPPER Limit**.
3. **Set Lower Limit**:
   - Tap **Jog Down** to inch the blind to your window sill.
   - Tap **Confirm & Save LOWER Limit**.
4. **Finalize**: Tap **Lock & Finalize Limits**. The motor will perform a confirmation jog.

Your blind limits are now stored in the motor's internal non-volatile memory and will be permanently respected by Home Assistant, Zigbee hubs, and remotes.
