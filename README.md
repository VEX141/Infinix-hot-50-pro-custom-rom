# 📱 Infinix Hot 50 Pro - Custom ROM Installation Guide (PC-less Method)

> **⚠️ WARNING!**
> This process will void your device's warranty. Proceed at your own risk. Make sure to **backup** all your important data before performing this procedure.

This guide provides a detailed and unique approach to installing a Custom ROM on the Infinix Hot 50 Pro **without requiring a PC**. It utilizes a secondary Android device to execute the necessary Fastboot commands for bootloader unlocking.

---

## 🛠️ Prerequisites (What You Need)

Before starting, you must ensure you have the following items and software:

1.  **Main Device:** Your Infinix Hot 50 Pro (must have at least **60% battery** charge).
2.  **Secondary Device:** Another Android phone/tablet. This device must have the **Bugjaeger** application installed to execute Fastboot commands.
3.  **Official Charger:** You must use the official Infinix charger that came in the box.
4.  **OTG Adapter:** An On-The-Go (OTG) adapter is necessary to connect the two devices for Fastboot mode and bootloader unlocking.
5.  **Custom ROM:** You will need the Generic System Image (GSI) ROM file in `.img` or `.gz` format (details on how to find this are below).

---

## 🔓 Bootloader Unlock Process (Bugjaeger Method)

### Step 1: Enable Developer Options and Debugging

1.  On **both** the Infinix phone and the secondary device, go to: `Settings` > `My Phone` (or `About Phone`) > `Version Information` > `Build Number`.
2.  Tap the **"Build Number"** 5 times until you see the message: "You are now a developer!"
3.  The Developer Options are located under the `System` section.
4.  In the Developer Options:
    * Enable **"USB Debugging"** on both devices.
    * Enable **"OEM Unlocking"** on the Infinix device.

### Step 2: Connect Devices and Enter Fastboot Mode

1.  Connect the **OTG adapter** to the secondary device.
2.  Connect the official USB cable from the Infinix phone to the **OTG adapter**.
3.  On the secondary device, prepare the **Bugjaeger** app. Check if it recognizes the Infinix device. If it connects, you can proceed.
4.  In Bugjaeger, navigate to the **Lightning Bolt icon (Fastboot)** tab.
5.  Press **"Reboot to Bootloader"** or manually type the command:
    ```bash
    reboot bootloader
    ```

The Infinix phone should now display the **Fastboot text** and a USB icon.

### Step 3: Execute the Unlock Command

1.  In Bugjaeger, tap the blue icon with a lightning bolt `<⚡>` located at the bottom (this opens the command console).
2.  Enter the following command:
    ```bash
    fastboot flashing unlock
    ```
    *If that fails, try:*
    ```bash
    fastboot oem unlock
    ```
3.  **Look at the Infinix screen!** It should display a confirmation text: **"Unlock bootloader?"**
4.  Use the **Volume buttons** (Up/Down) to select the unlock option and confirm with the **Power button**.

> **Note:** The phone will perform a factory reset. If the phone gets stuck on the Fastboot screen, press and hold the **Power button for 8 seconds** until it restarts. Reconfigure your phone after the reset!

---

## 🚀 Custom ROM Installation (DSU Sideloader Method)

Now that the bootloader is unlocked, we will use the DSU Sideloader app.

### Step 1: Check Treble and Download GSI

1.  After configuring your reset phone, go to your browser and search for **"Treble Check"**.
2.  Confirm that Project Treble is supported.
3.  Tap the button to view GSI Images, which will take you to a GitHub page with official and unofficial GSI ROMs. **Download the ROM you prefer.**
    * *Tip:* To prevent long downloads from cutting or canceling, install the **1DM** app, copy the ROM link, and paste it into 1DM's browser.

### Step 2: Prepare for Installation

1.  While the ROM downloads, search for and install the **DSU Sideloader** app on your Infinix phone.
2.  Grant the app the necessary permissions and set the path where your ROM file will be saved.

### Step 3: Configure and Install the ROM

1.  Once the ROM download is complete (it must be in `.img` or `.gz` format; **DO NOT UNZIP**), open DSU Sideloader.
2.  Select your Custom ROM file.
3.  Activate the **"Userdata size"** option and set it to **40 GB**. This is recommended for the ROM to run stably.
4.  Tap **"Install."**

### Step 4: Grant Permissions via LADB

The app will request installation permission. We will use the LADB method:

1.  Download **LADB** (Local ADB) from GitHub or the Play Store.
2.  Pair LADB with your device using **Wireless Debugging** (found in Developer Options). The LADB console should show it is connected, and the system should send a notification.
3.  Go back to **DSU Sideloader** and copy the command it requests.
4.  Paste the command into the LADB console and execute it.

The system will now begin creating the secondary system partition using the native DSU Loader feature.

### ❓ What is DSU Loader?

The **DSU Loader (Dynamic System Update Loader)** is a feature introduced in Android 11 that simplifies the installation and testing of Generic System Images (GSI).

Found in your device's Developer Options, DSU Loader allows users to perform the following actions through a simple UI:

* Download a GSI (a standard, pure version of the Android OS).
* Install that GSI into a **new dynamic partition** separate from the main OS.
* Boot the GSI as a temporary guest operating system, leaving the original system intact.
* Easily switch between the original system and the GSI by simply restarting the device.

The main purpose of the Dynamic System Updates (DSU) functionality is to allow developers and advanced users to quickly test new Android versions (or different system configurations) without the risk of corrupting or overwriting their primary installation.

### Step 5: Reboot into the New ROM

Once the system finishes installing the ROM, tap **"Restart."** The Custom ROM will begin to boot.

> **Note on Permanence:**
> This DSU process is **not permanent**. If you constantly reboot the temporary ROM, your main system (XOS) will eventually delete it.
>
> **I will upload the process for permanent installation on your device soon.**

---

## 🚨 Disclaimer

If your phone suffers a hard brick or any other damage during this process, **I will not be held responsible** for the resulting damage.

## 🤝 Contributions

If you have any suggestions to improve this guide or find that any commands are no longer working, please open an **Issue** or submit a **Pull Request**. All help is welcome!
