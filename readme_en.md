> 📘 **Доступна русская версия!**  
> Откройте файл `readme.md`, чтобы прочитать README на русском языке.

# GNSS & GPS Fix Modules for EvolutionX 10.2 (Android 15) on Poco F4 5G (munch)

A set of KSU modules for fixing GNSS HAL operation and improving A-GPS/standard GPS on the custom EvolutionX 10.2 ROM by @AnkitSavani for Poco F4 5G (codename: `munch`).

---

## 📱 Supported versions and kernels

- **ROM**: EvolutionX 10.2 (Android 15) by @AnkitSavani  
- **Kernels** (tested and working):  
  - `perf+` (preinstalled in EvoX 10.2)  
  - FusionX-SUSFS-AOSP-EFF-1.7-Eclipse-0501 (with SuSFS and KSU-Next)  

---

## ⚙️ Requirements

- **KernelSU Next** (version ≥ 1.0.6) with SuSFS support (SuSFS is recommended but not required; testing was done with it)  
- A kernel that supports KernelSU Next  

---

## 🔧 Installation

1. Copy both ZIP files to any accessible location on your device (e.g., `/sdcard/Download/`).  
2. Open the **KernelSU Next** app → **Modules**.  
3. Tap **“Install”** and sequentially select:  
   - `FixGPS_KSU.zip`  
   - `FixGNSS_SELinux_KSU_v3.zip`  
4. After installation, **reboot** your device.  
5. For better initial fix (TTFF), launch any A-GPS app (e.g., GPS Test) → menu → **AGPS Data** → Reset & Download.  

---

## 🚀 What it fixes

- Bypasses **SELinux denials** for GNSS HAL and `hal_power_default` (debug prop file and capability).  
- Enables and improves **A-GPS / XTRA** functionality, ensuring fast Time-To-First-Fix.  
- Restores stable **3D-Fix** and maintains the fix even with brief signal losses.  
- Enables **GPS + GLONASS** (and if supported by ROM — BeiDou/Galileo/QZSS).  

---

## 📈 Test results

- **Indoors**: stable fix, 4–6 satellites in use, accuracy of 20–50 m (depending on conditions).  
- **Outdoors / near window**: expected accuracy of 3–10 m and 10+ satellites.  
- **SELinux logs** (`dmesg | grep denied`) cleared of critical GNSS-related denials.  

---

## 📝 License

MIT © 2025 [FireTIA](https://github.com/FireTIA) & o4-mini  

---

> **Demo screenshots and detailed logs** can be found in the `/examples` folder in the repository.  
> If you see new `avc: denied` entries in `dmesg` or `logcat`, please open an issue — we’ll include a fix in the next patch.
