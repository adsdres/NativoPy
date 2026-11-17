<div align="center">

🌐 **Language / Idioma:** [🇪🇸 Español](README.md) | **🇺🇸 English**

# 🚀 NativoPy Studio PRO
### Integrated Native Python-to-C/C++ Compiler (`.exe` / `.pyd`), NSIS Installer Builder & Code Signing Suite

[![Version](https://img.shields.io/badge/Version-2.8.0_Global-blue?style=for-the-badge)](https://github.com/adsdres/NativoPy/releases)
[![Platform](https://img.shields.io/badge/Platform-Windows_10_%7C_11_(x64_%2F_x86)-0078D6?style=for-the-badge&logo=windows)](https://github.com/adsdres/NativoPy)
[![Engine](https://img.shields.io/badge/Backend-Nuitka_%2B_MSVC_%2B_NSIS-27ae60?style=for-the-badge&logo=python)](https://github.com/adsdres/NativoPy)
[![Languages](https://img.shields.io/badge/UI_Languages-EN_%7C_ES_%7C_FR_%7C_PT_%7C_ZH-8e44ad?style=for-the-badge)](https://github.com/adsdres/NativoPy)

**Transform your Python projects into high-performance native executables (`.exe`), protected binary extension modules (`.pyd`), and cryptographically signed Windows installers (`Setup.exe`).**

[⬇️ Download Latest Release](https://github.com/adsdres/NativoPy/releases) · [📖 6-Step Workflow](#6-step-workflow) · [❓ FAQ](#frequently-asked-questions-faq)

</div>

---

## ✨ Key Features

### 🛠️ 1. True Native C/C++ Compilation (Intellectual Property Protection)
* **Real Machine Code Translation:** Unlike traditional packagers that merely bundle `.pyc` bytecode inside a self-extracting archive, **NativoPy Studio** orchestrates **Nuitka + Microsoft Visual C++ (MSVC)** to translate your Python source code into native C/C++ machine code.
* **Dual Output Modes:**
  * **Standalone / Onefile Executable (`.exe`):** Build an optimized standalone distribution folder for instant startup or a single portable `.exe` file.
  * **Protected Binary Module (`.pyd`):** Compile proprietary algorithms and core modules into native C extensions that cannot be decompiled, ready to be imported from any Python script.
* **Dual Architecture (64-bit & 32-bit):** Switch seamlessly between 64-bit and 32-bit targets with automatic isolation of virtual environments (`venv` / `venv32`) and dependencies (`requirements.txt` / `requirements_32.txt`).

### 🔍 2. Smart AST Auto-Analyzer & MSVC Crash Prevention
* **Static AST Code Inspection:** Automatically detects GUI frameworks and libraries used in your project (`PySide6`, `PyQt6`, `PyQt5`, `PySide2`, `Tkinter`/`CustomTkinter`, `NumPy`, `Pandas`, `SciPy`, `Pillow`, `Cryptography`, `Google GenAI`, etc.) and injects the required Nuitka plugins automatically.
* **Preventive Qt/Shiboken Memory Diagnostics:** Detects `.connect(lambda...)` signal patterns that can cause memory corruption (`Access Violation 0xC0000005`) in compiled C++ binaries.
* **Automatic MSVC `C1002` (Out of Heap Space) Mitigation:** Includes a 1-click assistant to apply the **`/Od` Low-Memory Patch** and force the native 64-bit MSVC toolchain (`vcvars64.bat`), allowing massive libraries (such as `google.genai` with 160,000+ lines of generated C code) to compile in seconds without exhausting the compiler heap.

### 📦 3. Professional Windows Installer Generator (NSIS MUI2)
* **1-Click `Setup.exe` Wizard:** Automatically packages your compiled application into a commercial Windows installer using high-density **solid LZMA compression**.
* **Full Windows OS Integration:**
  * Creates **Desktop** and **Start Menu** shortcuts.
  * Registers your application in *Add or Remove Programs* with estimated disk size and a clean `Uninstall.exe` that preserves user licenses in `%APPDATA%`.
  * Supports standard user mode or **UAC Administrator Elevation (`RequestExecutionLevel admin`)**.
  * **Automatic EULA Injection:** Automatically detects `EULA.txt` or `LICENSE.txt` in your project folder and injects the official `MUI_PAGE_LICENSE` agreement step.

### 🔐 4. Multi-Mode Digital Code Signing (`SignTool`) + RFC 3161 Timestamp + SHA-256
* **Cryptographic Signing for Binaries & Installers:** Automatically signs both your `.exe` and final `Setup.exe` installer to build reputation with *Windows Defender SmartScreen*.
* **3 Certificate Modes Supported:**
  1. **PKCS#12 Files (`.pfx` and `.p12`)** with password protection.
  2. **SHA1 Thumbprint (40 hex characters)** directly from your **Hardware USB Token** or Windows Certificate Store (`/s MY /sha1`).
  3. **Subject Name** from the Windows Certificate Store (`/s MY /n`).
* **RFC 3161 Timestamping (`http://timestamp.digicert.com`):** Ensures your digital signature remains valid indefinitely even after your certificate expires, with **automatic offline fallback** when compiling without an internet connection.
* **Automatic SHA-256 Checksum:** Generates and logs the SHA-256 integrity hash after every build.

---

## 📊 Edition Comparison (FREE vs PRO)

| Feature | FREE Edition | 7-Day TRIAL | PRO Edition (Commercial) |
| :--- | :---: | :---: | :---: |
| Virtual Environment (`venv`) & Dependency Manager | ✅ | ✅ | ✅ |
| Basic *Standalone* Compilation (`.exe`) | ✅ | ✅ | ✅ |
| Smart AST Dependency Auto-Analyzer | ✅ | ✅ | ✅ |
| Single-File Packaging (`--onefile`) | ❌ | ✅ | ✅ |
| Hide Windows Console (`--windows-console-mode=disable`) | ❌ | ✅ | ✅ |
| Protected Binary Module Compilation (`.pyd`) | ❌ | ✅ | ✅ |
| Batch Mode (Compile entire folders of `.py` scripts) | ❌ | ✅ | ✅ |
| Custom Application Icon (`.ico`) & Windows Version Metadata | ❌ | ✅ | ✅ |
| LTO Optimization (`--lto=yes`), Native MSVC & `/Od` Patch | ❌ | ✅ | ✅ |
| CPU Core Scaling (`--jobs`) & OS Process Priority | Max 4 cores | ✅ Unlimited | ✅ Unlimited |
| Professional `Setup.exe` Installer Builder (NSIS + EULA) | ❌ | ✅ | ✅ |
| Digital Code Signing (`SignTool` `.pfx`/`.p12`/USB Token + Timestamp) | ❌ | ❌ | ✅ |
| Devices per License (with unlimited reinstalls on the same PC) | — | 1 PC | **1 PC (Single-Seat)** |

---

## 🔄 6-Step Workflow

1. **Isolate (`1. ✨ Create venv`):** Create a clean 64-bit or 32-bit virtual environment for your project.
2. **Generate Requirements (`2. 📝 Generate reqs`):** Scan your project's actual imports and generate `requirements.txt`.
3. **Install (`3. 📦 Install`):** Install all required packages and Nuitka inside the isolated virtual environment.
4. **Auto-Analyze (`🔍 Auto-Analyze`):** Let the AST engine configure GUI plugins (`PySide6`, `PyQt6`, `Tkinter`) and optimal flags automatically.
5. **Resources & Metadata (Tab 2):** Assign your `.ico` icon, bundle data folders (`assets`, `db`, `img`) with automatic relative paths, and fill in Windows executable properties.
6. **Compile, Package & Sign (Tabs 3 & 4):** Configure CPU cores, enable the NSIS Installer + Digital Signature, and click **`Compile Project!`**.

---

## 💻 System Requirements

* **Operating System:** Windows 10 or Windows 11 (64-bit; supports 32-bit cross-compilation with a 32-bit Python interpreter installed).
* **RAM:** 8 GB minimum (16 GB recommended for large projects).
* **Disk Space:** At least 3 GB of free space for temporary C compilation cache.
* **C/C++ Compiler:** [Microsoft Visual Studio Build Tools 2022](https://visualstudio.microsoft.com/visual-cpp-build-tools/) (*Desktop development with C++* workload).
* **Installer Packager (Optional):** [NSIS (Nullsoft Scriptable Install System) 3.x](https://nsis.sourceforge.io/Download).

---

## 🌐 Native Multi-Language Support

The graphical interface, built-in Help Center, and generated NSIS installers natively support 5 languages:
* 🇺🇸 **English** (`en`)
* 🇪🇸 **Español** (`es`)
* 🇫🇷 **Français** (`fr`)
* 🇧🇷 **Português** (`pt`)
* 🇨🇳 **简体中文** (`zh`)

---

## ❓ Frequently Asked Questions (FAQ)

<details>
<summary><b>Why does SignTool report "After Private Key filter, 0 certs were left" when signing?</b></summary>
<br>
This means SignTool found the certificate but could not access its Private Key:
<ol>
  <li>Make sure you select a <b><code>.p12</code> or <code>.pfx</code></b> file (which bundles the private key) and enter its password—never a <code>.cer</code> or <code>.crt</code> file (which only contains the public key).</li>
  <li>If your private key is stored on a <b>Hardware USB Token</b> or in the Windows Certificate Store, paste your <b>40-character SHA1 Thumbprint</b> or <b>Subject Name</b> directly into the Certificate field.</li>
</ol>
</details>

<details>
<summary><b>How do I fix "fatal error C1002: compiler is out of heap space in pass 2"?</b></summary>
<br>
In <b>Tab 3 (Advanced Performance)</b>, click <b><code>⚡ /Od Patch (C1002)</code></b>, check <b><code>Low RAM memory (--low-memory)</code></b>, and enable <b><code>Force MSVC (Native Tools)</code></b>. This prevents Microsoft's optimizer from exhausting its control-flow graph memory on massive generated C files.
</details>

<details>
<summary><b>How do I include my EULA in the generated Setup.exe installer?</b></summary>
<br>
Place an <code>EULA.txt</code> or <code>LICENSE.txt</code> file in your Python script's directory before compiling. NativoPy Studio will automatically detect it and inject the license agreement page into the NSIS installer wizard.
</details>

---

## ⚖️ Legal Notice & Intellectual Property

**NativoPy Studio PRO** is commercial software protected by copyright laws and international intellectual property treaties. See [LICENSE](LICENSE) and [EULA.txt](EULA.txt) for details.

> *NativoPy Studio is an independent graphical frontend and orchestration tool for Nuitka and NSIS. It is not affiliated with, sponsored, or endorsed by the Nuitka project or the Python Software Foundation.*

© 2026 **Adsdres** (`Adsdres@gmail.com`). All rights reserved.
