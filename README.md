# Mufattish
A cross-platform PyQt6 system management and security analysis tool for files, APKs, and active processes.


# 🛡️ Mufattish (v2.0)

> **Inspect • Analyze • Clean • Protect**  
> *A comprehensive system inspection, cache management, and deep file analysis tool.*

---

## 📌 Project Overview

**Mufattish** (المفتش - *The Inspector*) is a system administration and security analysis desktop application built in Python using a modern **PyQt6** graphical interface.

The application enables system administrators and general users to:
- 📊 **Monitor Hardware & System Health**: Battery status/thresholds, CMOS/RTC clock, storage drives, audio cards, and active network/Bluetooth interfaces.
- 💻 **Manage System Processes**: Instantly identify and filter high-memory processes (≥ 300 MB) with options for safe termination.
- 🗑️ **Clean System Junk**: Calculate and purge user cache (`~/.cache` or temporary directories) and detect large space-consuming files.
- 🔍 **Inspect File Security (APK & Generic Files)**:
  - Inspect executable files and documents for suspicious command execution signatures.
  - **In-Depth APK Analysis (Deep Scan)**: In-memory decompilation, manifest extraction, critical permission checking, and detection of Indicators of Compromise (IoC / RAT / Spyware).
- 🌐 **Multilingual Support & Accessibility**: Dual-language interface (French / English) with dynamic UI zoom scale adjustment (50% to 200%).

---

## 📁 Repository Structure

```text
.
├── main.py                     # Entry point (Splash screen & module initialization)
├── mufattish_icon.png          # Official application icon
├── requirements.txt            # Python dependencies list
├── modules/
│   ├── apk_decompiler.py       # APK deep analysis and in-memory decompilation module
│   ├── battery_manager.py      # Battery health & charge threshold management
│   ├── cleaner_manager.py      # Cache calculation and purging logic
│   ├── network_manager.py      # Network interface scanning & port/service inspection
│   ├── scanner_manager.py      # Generic file signature and pattern scanner
│   ├── system_manager.py       # Hardware detection, audio, Bluetooth & process manager
│   └── translations.py         # Internationalization dictionary (FR / EN)
└── ui/
    └── widget.py               # PyQt6 user interface, Catppuccin theme styling & UI logic

⚠️ Challenges Encountered During Development
Developing Mufattish required solving several complex technical challenges:

In-Memory Reverse Engineering & APK Parsing Without Heavy External Tools:

Challenge: Analyzing Android packages (.apk) thoroughly required fast extraction without writing temporary files to disk or relying on heavy Java dependencies.

Solution: Implemented an on-the-fly decompilation pipeline using zipfile to analyze binary .dex and .xml contents directly within byte streams in memory.

Cross-Platform Hardware Detection Compatibility:

Challenge: System commands for retrieving audio devices, MAC addresses, or Bluetooth adapters differ significantly between Linux (wpctl, pactl, bluetoothctl) and Windows (PowerShell).

Solution: Designed abstract parser wrappers inside system_manager.py capable of dynamically handling subprocess output based on the host operating system.

Asynchronous Execution & UI Responsiveness:

Challenge: Traversing directories for large files or scanning heavy APK files caused the graphical user interface to freeze.

Solution: Integrated asynchronous worker threads (QThread / ScanWorker / LargeFilesWorker) to segregate intensive background calculations from the main UI rendering thread.

📦 Installation & Setup
⚠️ Important Compatibility Note:

Pre-compiled Binary: The executable version provided in the Releases tab is designed exclusively for Linux environments.

Source Code Mode: For Windows, macOS, or other operating systems, the application must be executed using Python 3.9+.

🚀 Method 1: Running on Linux (Pre-compiled Executable)
If you are using a Linux system (Debian, Ubuntu, Arch, Fedora):

Go to the Releases section of this GitHub repository.

Download the binary file mufattish.

Grant execution permissions and run the application:

Bash
chmod +x mufattish
./mufattish
🐍 Method 2: Running from Source Code (Cross-Platform: Linux, Windows, macOS)
1. Prerequisites
Ensure Python 3.9 (or higher) and git are installed on your machine.

2. Clone the Repository
Bash
git clone [https://github.com/Ahmadou-Alim/mufattish.git](https://github.com/Ahmadou-Alim/mufattish.git)
cd mufattish
3. Create a Virtual Environment (Recommended)
Linux / macOS:

Bash
python3 -m venv venv
source venv/bin/activate
Windows (PowerShell):

PowerShell
python -m venv venv
.\venv\Scripts\Activate.ps1
4. Install Dependencies
Bash
pip install -r requirements.txt
5. Launch the Application
Bash
python main.py
⚙️ Core Dependencies
PyQt6: Cross-platform GUI framework.

psutil: Cross-platform process and system monitoring library.

🧑‍💻 Author
Ahmadou Alim Ibrahim — Physicist && Mathematics and Computer Science Student at the University of Bangui.
