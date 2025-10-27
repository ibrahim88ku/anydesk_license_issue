# 🧰 Reset AnyDesk ID (Windows)

**Script:** `reset-anydesk-id.bat`  
**Purpose:** Force AnyDesk to generate a **new ID** by clearing all local configuration files and restarting the service.

> ⚠️ **Warning:**  
> Running this script will **delete all existing AnyDesk settings**, including your **current ID**, aliases, trusted devices, and **Unattended Access configuration**.  
> If you need to keep your current AnyDesk session or ID, see the [Keep your existing ID](#keep-your-existing-id) section **before** running it.

---

## 🧩 What the script does

The script performs a full cleanup and reset of AnyDesk:

1. Stops and disables the **AnyDesk service**.
2. Kills any running `AnyDesk.exe` processes.
3. Takes ownership of and deletes:
   - `C:\ProgramData\AnyDesk` — global config (contains AnyDesk ID and key)
   - `%AppData%\AnyDesk` — per-user settings
4. Re-enables and starts the service.
5. Detects OS architecture (32-bit or 64-bit) and launches AnyDesk.
6. Cleans up temporary files.

After running, AnyDesk will recreate configuration files from scratch — often resulting in a **new AnyDesk ID**.

---

## 🧠 Why use this

Use this script if:

- AnyDesk won’t start or has corrupted settings.
- You intentionally need a **fresh AnyDesk identity**.
- You’re preparing a **clean image** (VM/template) that shouldn’t share the same ID.

It **won’t fix**:
- Network, DNS, or firewall problems  
- License/account issues  
- Remote-side connectivity issues

---

## ⚙️ Requirements

- Windows 10 / 11 / Server 2016 or newer  
- **Administrator privileges** (right-click → *Run as administrator*)  
- AnyDesk installed as a system service  
- Local/physical access — unattended access will stop working

---

## ▶️ Usage

1. Download or clone this repository.
2. Right-click **Command Prompt** → **Run as administrator**.
3. Navigate to the folder containing the script.
4. Run:

   ```bat
   reset-anydesk-id.bat
