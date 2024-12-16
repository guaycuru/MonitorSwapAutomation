# README

This tool automatically switches your main display to a dummy plug (or any virtual display) that you have set up for **Sunshine**. The goal is to seamlessly switch from your normal monitor setup to a dummy display when you start streaming (e.g., using Moonlight on a mobile device).

## How It Works

- **Normal Operation:** When you’re not streaming, your PC uses your regular monitor arrangement.
- **While Streaming:** As soon as you start a Moonlight stream on another device, the script automatically switches to a dummy monitor configuration (or another specified monitor layout).

---

## Important Notes

1. **Dummy Plug / Virtual Display:**  
   This script is designed for systems with a dummy plug or virtual display, but it can be used in other scenarios. For instance, you can use it to switch from a dual-monitor setup to a single monitor while streaming.

2. **Windows 11 Users:**  
   Due to a known bug, you must set the default terminal to **Windows Console Host**.
   
   - On newer Windows 11 versions:
     1. Open **Settings**.
     2. Go to **System > For Developers**.
     3. Locate the **Terminal** setting (which defaults to "Let Windows decide").
     4. Change it to **Terminal [Windows Console Host]**.

   - On older Windows 11 versions:
     1. Open **Settings**.
     2. Go to **Privacy & Security > Security > For Developers**.
     3. Find the **Terminal** option.
     4. Change it from "Let Windows decide" to **Terminal [Windows Console Host]**.

   Without this setting, the script may not work correctly.

3. **Do Not Move the Script’s Folder After Installation:**  
   If you move the installation folder after setting up the script, it may stop working. In that case, simply reinstall it.

4. **Cold Reboots / Hard Crashes Issue:**  
   On a cold boot (from a fully powered-off state), Windows may not allow the script to switch monitors immediately.

   **Workaround:**  
   - After a cold boot, start your PC and log in using the "Desktop" stream option in Moonlight.
   - End the stream, then start it again.
   
   After doing this once, subsequent uses should work normally.

5. **Sunshine Web UI Setting:**  
   **Do not set an “Output Name” in the Sunshine Web UI under the Audio/Video tab.** Leave it blank. Setting an output name may break the script’s functionality.

---

## Requirements

- **For GFE (GeForce Experience) Users:**  
  This script no longer supports GFE. If you need the older version that worked with GFE, download the [Legacy Version](https://github.com/Nonary/MonitorSwapAutomation/releases/tag/legacy).

- **For Sunshine Users:**
  - Sunshine version **0.19.1 or higher**.
  - Host computer must be running Windows.

---

## Step-by-Step Setup

1. **Sunshine Output Settings:**  
   In the Sunshine Web UI, ensure the “Output Name” field is blank under Audio/Video settings.

2. **Install the Script:**  
   Follow the provided installer instructions to set up the script on your computer.

3. **Set Your Baseline (Primary) Monitor Setup:**  
   Arrange your monitors exactly how you want them for normal operation (i.e., when you’re not streaming).

4. **Save Your “Primary” Monitor Profile:**  
   - Open **Terminal/Command Prompt** in the script’s folder.
   - Run:
     ```  
     .\MonitorSwitcher.exe -save:Primary.xml
     ```
   This creates a snapshot of your current (normal) monitor configuration as “Primary.xml.”

5. **Prepare to Save Your “Dummy” Monitor Profile:**
   Start a Moonlight stream from another device (phone, tablet, etc.) so you can view and control your PC remotely. This is important because when you switch to the dummy monitor, your physical monitor will go dark.

6. **Configure the Dummy Monitor Setup (While Streaming):**  
   - With the remote stream running:
     1. On your Windows PC, open **Settings > System > Display**.
     2. Click **Identify** to determine the monitor number you want to use for streaming. For a dummy plug, identify which monitor number is not physically visible.
     3. In the display settings, change the dropdown to "show only on {NUMBER}" where {NUMBER} is the monitor you plan to use as the dummy/streaming display.
     4. Once you confirm this change, your local display goes black. Continue using your remote device to control the PC.

7. **Save Your “Dummy” Monitor Profile:**
   - Back in your Terminal window (still in the script’s folder), run:
     ```  
     .\MonitorSwitcher.exe -save:Dummy.xml
     ```
   This saves your dummy/streaming monitor setup as “Dummy.xml.”

8. **Completing the Setup:**
   - End the Moonlight stream session.
   - Your display should return to normal on your physical monitor.
   
   Now, whenever you start a stream, the script automatically switches to the dummy display configuration. When you stop streaming, it will restore your original setup.

---

## Troubleshooting

**If the ResolutionAutomation script doesn’t switch resolutions properly or is unreliable:**

- Increase the start delay in **settings.json** (located in the script’s folder) to 3 or 4 seconds. This gives the monitor-switching process more time before the resolution change occurs.

---

## Change Log

**v2.0.2**
- More bug fixes that prevented primary monitor from restoring after a stream was ended.

**v2.0.1**  
- Fixed a bug that prevented the primary monitor from restoring after ending a stream.

**v2.0.0**  
- Switched from Nirsoft MultiMonitorTool to MonitorSwitcher for better compatibility with Windows 24H2 and improved reliability.

**v1.2.0**  
- Added changes to support Hybrid GPU fixes, assisting laptop users in forcing NVIDIA encoding.

**v1.1.9**  
- Updated MultiMonitorTool to v2.10.
- Improved validation for restoring primary monitors.

**v1.1.8**  
- Added debug logging.
- Fixed monitor flicker issue related to known workarounds.

---