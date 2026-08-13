<div align="center">

# 🔌 YunuUSBNet V1.0.0

**Ultra-Lightweight Windows Reverse Tethering GUI — Powered by Gnirehtet & ADB**

</div>

---

## 🖼️ Screenshots

> _Place your application screenshots/GIFs here (main window, tray icon, speedometer in action)._

<div align="center">

| Main Window | Live Speedometer | System Tray |
| :---: | :---: | :---: |
| _screenshot.png_ | _screenshot.png_ | _screenshot.png_ |

</div>

---

## 📖 What is YunuUSBNet?

**YunuUSBNet** is an ultra-lightweight, portable Windows GUI wrapper built in **AutoIt** for **Gnirehtet** and **ADB**. It shares your PC/Laptop's internet connection (Ethernet or Wi-Fi) with an Android smartphone via **USB reverse-tethering** — no root, no complicated CMD commands, no driver hell.

It's purpose-built for **budget and low-spec PCs (2GB RAM)** — the kind of "potato PC" that chokes on heavier tethering tools. YunuUSBNet strips away the bloat and gives you a clean, one-click GUI on top of the proven Gnirehtet engine.

Perfect for:
- 💻 Old laptops / budget PCs with 2GB RAM
- 🏢 Office or campus computers with strict spec limits
- 📶 Areas with no Wi-Fi but a spare Android phone with mobile data (or vice versa)
- 🙅 Anyone tired of fiddling with raw `adb` and `gnirehtet` CMD commands

---

## 🔥 What's New in Official Release V1.0.0 🎉

This is the **first official release** of YunuUSBNet. Here's everything packed into it:

### 📊 Dual-Unit Live Speedometer & 4-State Color Matrix
- Real-time network speed display showing **both** `KB/s` (or `MB/s`) **and** `Mbps` simultaneously — e.g. `768.0 KB/s (6.1 Mbps)`.
- Powered by a **WMI Raw Performance Engine** (`Win32_PerfRawData_Tcpip_NetworkInterface`) with a **2-sample Moving Average** smoothing filter to eliminate false `0 KB/s` dips.
- **Dynamic 4-State Color Matrix**: switches between Theme Blue (`#00AAFF`) when active and Gray (`#666666`) when disconnected/idle — with zero flicker.
- Flat visual progress meter bars rendered via native Windows `uxtheme.dll` calls.
- **WMI Warm-Up** on launch: instantly detects PC internet status at startup via ping and octet checks.

### 🪖 Military-Grade Hardware Resilience & Cable Shake Protection
- **Non-Destructive Instant Re-Attach (~100ms)**: automatically re-injects Gnirehtet without killing the ADB daemon or corrupting the phone's ADB session when physical micro-jitters occur.
- **Soft Hysteresis Retry Loop**: 3x soft retries before escalating, making the connection immune to continuous cable shaking/vibration ("Rage-Gamer Proof").
- **Windows PnP Auto-Heal** (`WM_DEVICECHANGE` `0x8000` / `0x8004`): listens directly to Windows OS PnP kernel hardware messages for near-instant reconnection on USB insertion — fixes the classic "ding-dong" USB sound lockup.
- **Offline Device Auto-Recovery**: automatically issues `adb reconnect offline` if ADB desyncs.
- **Graceful Android VPN Teardown**: sends `gnirehtet stop` and `am force-stop` to the phone before closing PC-side processes on manual disconnect.

### 🪶 Ultra-Lightweight & System Hardening (Crash-Proof)
- **Single-Instance Enforcer** (`_Singleton`): prevents multiple instances from fighting over USB sockets.
- **Explicit System Path Resolution** (`@SystemDir`): protects against Windows `%PATH%` corruption or DLL side-loading.
- **Memory & Handle Leak Prevention**: explicit `StdioClose()` handle cleanup and 15,000-character log buffer auto-purge.
- **High Priority Elevation** (`ProcessSetPriority(4)`): elevates Gnirehtet to High Priority to prevent ping spikes during heavy gaming or 100% CPU load.
- **0% CPU Idle Footprint**: non-blocking single-loop execution with `Sleep(10)` yield.

### 📌 System Tray & Window Lifecycle Overhaul
- **Minimize (`_`)**: minimizes normally to the Windows Taskbar.
- **Close (`X`)**: hides to the System Tray near the clock **only** when a connection is active. Exits completely when stopped.
- **Left-Click Tray Icon**: instantly restores and activates the main window.
- **Headless Mode** (`--background`): command-line argument support for silent execution without a GUI.

---

## ✨ Key Features

- 📊 **Dual-Unit Live Speedometer** — See real-time speed in `KB/s` / `MB/s` and `Mbps` at once
- 🪖 **Cable-Shake-Proof Connection** — Instant re-attach with zero ADB session corruption
- 🪶 **Ultra-Low RAM Usage** — Runs smoothly on 2GB RAM systems (yes, really)
- ⚡ **0% CPU Idle** — Non-blocking loop keeps your PC free for gaming or work
- 🔌 **No Root Required** — Works entirely through standard USB debugging + ADB
- 🖱️ **One-Click GUI** — No manual `adb` or `gnirehtet` CMD typing needed
- 📌 **Smart System Tray Behavior** — Stays out of your way when active, exits clean when stopped
- 📦 **Fully Portable** — No installation needed, ~15MB including the Engine folder
- 🖥️ **Broad Compatibility** — Windows 7, 8, 10, and 11 (32-bit & 64-bit)

---

## 🆚 Overview / Performance Comparison

| Feature | 🔌 YunuUSBNet | ⌨️ Official Gnirehtet CMD | 💰 Commercial Tethering Tools |
| --- | :---: | :---: | :---: |
| RAM Usage | **3–8 MB** | 30MB+ | 150MB+ |
| CPU Usage (Idle) | **0–1%** | 1–3% | 3–5% |
| Setup Complexity | ✅ One-click GUI | ❌ Manual CMD commands | ⚠️ Installer + Account |
| Root Required | ❌ No | ❌ No | ❌ No |
| Cable-Shake Resilience | ✅ Instant Re-Attach | ❌ Manual restart needed | ⚠️ Varies |
| Live Speedometer | ✅ Dual-Unit (KB/s + Mbps) | ❌ None | ⚠️ Basic |
| Portable (No Install) | ✅ Yes | ✅ Yes (CMD only) | ❌ No |
| Price | 🆓 Free | 🆓 Free | 💰 Often Paid |
| Size | ~15MB | Varies | 50MB+ |

**Bottom Line:** YunuUSBNet gives you the reliability and speed of Gnirehtet, wrapped in a lightweight GUI that's actually pleasant to use — even on a potato PC.

---

## 💻 System Requirements

### Minimum (Tested & Works)
- **CPU:** Dual Core 2.0 GHz (Intel i3 2nd Gen or equivalent)
- **RAM:** 2GB
- **OS:** Windows 7, 8, 10, or 11 (32-bit & 64-bit)
- **USB:** A working USB port + data-capable USB cable
- **Android:** USB Debugging enabled on the phone

### Recommended
- **CPU:** Intel i3 3rd Gen or higher
- **RAM:** 4GB+
- **USB:** USB 3.0 port for best throughput

---

## 🚀 Quick Start / Installation Guide

### 🖥️ Windows Installation (7 / 8 / 10 / 11)

1. Download `YunuUSBNet_V1.0.0.zip` from **Releases**.
2. Extract using WinRAR, 7-Zip, or Windows' built-in extractor.
3. Enable **USB Debugging** on your Android phone (Settings → Developer Options).
4. Connect your phone via USB cable and allow the ADB authorization prompt on the phone.
5. Open the extracted folder and run `YunuUSBNet.exe`.
6. Click **Start/Connect** and watch the speedometer come alive. 🎉

💡 **Tip for First-Time Users:** If your phone isn't detected, install the correct **USB/ADB driver** for your device model first, then reconnect the cable.

---

## ⚙️ Features Explained

### 📊 Dual-Unit Live Speedometer
Reads live traffic counters straight from Windows' WMI performance layer and applies a 2-sample moving average, so the number you see is smooth and accurate instead of jumping to `0 KB/s` between polling intervals. Both `KB/s`/`MB/s` and `Mbps` are shown together so you don't have to do the math yourself.

### 🪖 Hardware Resilience
USB reverse-tethering is notoriously fragile — a loose cable or a bump on the desk usually kills the whole session and forces a full restart. YunuUSBNet listens directly to Windows' PnP hardware events and re-injects the Gnirehtet tunnel in roughly 100ms, without tearing down the underlying ADB session. Combined with the soft hysteresis retry loop, this makes the connection resilient enough to survive continuous cable movement.

### 🪶 System Hardening
Because the tool is meant to run for hours in the background on low-spec machines, every part of the codebase is written to avoid leaks: handles are explicitly closed, the log buffer is capped and auto-purged, and only a single instance is ever allowed to run — preventing two copies from fighting over the same USB socket.

### 📌 Tray & Lifecycle Behavior
YunuUSBNet only occupies your taskbar or tray depending on connection state — it disappears completely once you've stopped tethering, so it never lingers as background clutter.

---

## 📊 Performance Comparison (Real-World Test)

Tested on a potato PC — **Intel i3 2nd Gen + 2GB RAM**:

| Tool | RAM | CPU (Idle) | CPU (Active) | Setup Time |
| --- | :---: | :---: | :---: | :---: |
| **YunuUSBNet** | 3–8 MB | 0–1% | 1–2% | ~10 sec |
| Official Gnirehtet CMD | 30MB+ | 1–3% | 3–5% | ~2–5 min |
| Commercial Tethering Tool | 150MB+ | 3–5% | 5–10% | ~1–3 min |

**YunuUSBNet uses up to 4–5x less RAM than a typical commercial tethering tool**, while staying just as fast — because it's just a thin, well-optimized GUI shell around Gnirehtet, not a reinvented network stack.

---

## 🛠️ Troubleshooting

**Q: My phone isn't detected at all?**
A: Make sure USB Debugging is enabled and you've accepted the "Allow USB Debugging" prompt on the phone. Reinstall the correct ADB driver for your device if needed.

**Q: The connection drops when I move the cable slightly?**
A: This is exactly what the Hardware Resilience system is built to fix — update to the latest version. If it still happens, try a different USB cable (some cheap cables have poor shielding).

**Q: The speedometer shows `0 KB/s` even though internet is working?**
A: Wait a few seconds for the WMI Warm-Up to finish detecting your active network adapter, or check that your PC's internet connection itself is active.

**Q: ADB says "device offline"?**
A: YunuUSBNet automatically issues `adb reconnect offline` in the background. If it persists, unplug and replug the USB cable once.

**Q: The app won't close from the tray icon?**
A: By design, YunuUSBNet only fully exits when the connection is stopped — this prevents an abrupt VPN teardown on the phone. Click Stop first, then close.

**Q: Can I run it without a visible window?**
A: Yes — launch it with the `--background` argument for headless/silent mode.

---

## 💬 Community & Support

- 🐛 **Report a Bug:** Open an Issue
- 💡 **Request a Feature / Ask Questions:** Use Discussions
- ⭐ **Enjoying YunuUSBNet?** Consider starring the repo — it helps a lot!

---

## 📝 License

Other

## 👤 Author

**YunuP-Dev**
_Modified & Engineered by: Yunu – Skanesa_

Built for people with old computers who still want a reliable connection.


"Powered by Genymobile/gnirehtet"
---

**Keywords:** USB reverse tethering Windows • Gnirehtet GUI • ADB tethering tool • share internet via USB Android • lightweight tethering 2GB RAM • potato PC internet sharing • Windows 7/8/10/11 USB tethering • portable Gnirehtet wrapper • no root USB tethering • ADB reverse tether GUI • YunuUSBNet
