<p align="center"><img src="assets/orthovision_icon.png" width="144" alt="OrthoVision icon"></p>

<h1 align="center">OrthoVision for Windows</h1>

<p align="center">A focused, dark-mode viewer for exported C-arm X-ray images.</p>

<p align="center"><a href="https://github.com/Sa3d-99/OrthoVision_/releases/latest"><strong>Download the latest Windows installer</strong></a></p>

This is the official **installer distribution repository**. Application source is
maintained privately. Installers include the compiled app, its runtime files,
and the Microsoft-signed Visual C++ x64 prerequisite—not the Flutter project.
The current installer is visible directly in the repository root, not inside a
folder. [Download OrthoVision v1.0.2](https://github.com/Sa3d-99/OrthoVision_/releases/download/v1.0.2/OrthoVision-Setup-1.0.2.exe).

## Install

1. Open **Releases** and download `OrthoVision-Setup-<version>.exe`.
2. Run Setup on Windows 10/11 x64 and approve Windows administrator permission.
3. Launch OrthoVision from the Start menu or optional desktop shortcut.
4. Activate with a device-bound license from your OrthoVision administrator.

Setup installs the app and checks its Visual C++ runtime dependency. The app
installer itself is not Authenticode-signed; Windows may display a publisher or
SmartScreen warning. Download only from this repository and check the published
SHA-256 digest if needed. Do not bypass your hospital's security policies.

## Activate and renew

OrthoVision v1.0.2 requires a valid license before the viewer and LAN receiver
start. No internet connection is needed for activation or capture.

1. On **Activate OrthoVision**, select a physical Ethernet/Wi-Fi adapter and click
   **Copy device MAC**. Send that MAC address to your administrator.
2. The administrator issues a signed license for this device and an agreed end
   date. Paste the complete `OVL1.…` code and select **Activate**.
3. The app stores the accepted license for future launches. An invalid,
   different-device, or expired code keeps the startup activation screen open.
4. If 30 days or less remain at startup, a persistent top banner asks you to
   contact support. It does not cover the image or interrupt capture.
5. To renew, obtain a replacement code, close the app **after the procedure**,
   and restart. If the saved code has expired, enter the replacement on the
   activation screen. To replace a still-valid code early, close OrthoVision,
   remove only `%APPDATA%\OrthoVision\OrthoVision\license.txt`, then reopen and
   enter the replacement. Do not remove capture files or other settings.

**Licensing is startup-only:** once the viewer opens, expiry during that session
never locks the screen, blocks reception, or closes the app. The next launch
checks the license again. The banner's day count is a startup snapshot, rounded
up. The administrator's end date is inclusive in UTC. Keep Windows date/time
correct. MAC changes (including Wi-Fi randomization or adapter replacement) can
require a new license; an unplugged licensed adapter can still be recognized.

## Review images

- **Find devices:** view LAN adapters, cable/link status, known LAN neighbors, and
  compatible image-export bridges. Click **Connect** beside a compatible bridge;
  its TCP image port is detected automatically.
- **LAN preview:** receive exported PNG/JPEG/BMP/WebP captures and display the
  strongest technical-quality frame from each capture burst.
- **Local receiver IP / Setup Guide:** read the laptop's active IPv4 address and
  listening port below the header. Copy IP/port, refresh after connecting a cable,
  or choose another active interface from the dark, step-by-step guide.
- **Auto Save:** turn automatic retention on or off. Only the top 10 ranked
  automatic captures are retained; weaker automatic captures are deleted.
- **Manual Save:** keep the displayed source image explicitly. Manual saves are
  not removed by the automatic top-10 limit.
- **Open Image:** import a supported local image for review.
- **Brightness:** adjust the preview without modifying source pixels or saves.
- **Settings:** choose a persistent capture folder and view update status.
- **Window controls:** minimize, maximize/restore, or close with graceful worker
  shutdown. The layout adapts to the window size.

## Network compatibility — read before connecting

**An Ethernet cable alone does not make every C-arm compatible.** Find devices
uses the OrthoVision image-export bridge discovery protocol, not an undocumented
detector/service protocol. A vendor-approved exporter must support the discovery
reply and framed raster-image stream. A bare OSCAR/ZENIS C-arm is not automatically
supported, DICOM is not currently supported, and real C-arm integration has not
been validated.

The PC and exporter need an active link, compatible IP subnet, and allowed
firewall traffic. OrthoVision does not change machine IP addresses, DHCP settings,
or firewall rules, and does not scan detector service ports. Unknown devices are
shown from the Windows neighbor cache, which can contain stale entries and is not
a full LAN inventory. Only advertised compatible exporters have a Connect button.
Use a trusted, isolated clinical LAN: image transport and discovery currently have
no encryption or sender authentication.

## OSCAR / ZENIS connection guide

1. Connect the laptop and your approved image exporter to the same trusted LAN.
2. Open **Setup Guide**. Copy the displayed laptop IP and port (normally `4040`).
   Active Ethernet is preferred over Wi-Fi; unplugged and virtual Windows
   adapters are excluded. Address detection refreshes automatically every 30 seconds.
3. On ZENIS, locate **Option**, then **Network / DICOM**, if available. Exact labels
   depend on your version—refer to the machine's supplied operator manual.
4. Set up ZENIS export to your approved bridge. In that bridge's outgoing
   OrthoVision destination, enter the copied laptop IP and port. **Do not add
   OrthoVision directly as a DICOM Storage node: it does not implement DICOM.**
5. Save and test sending an existing non-patient image. Verify its preview before
   clinical use. Automatic routing after a pedal exposure requires verified
   vendor/exporter configuration; connecting a cable alone does not enable it.

“Ready to receive” confirms the local listener only. If no active IPv4 address
appears, connect Ethernet/Wi-Fi and select **Refresh IP**. Check the subnet and
hospital-approved firewall access if delivery fails; do not change detector or
existing PACS settings or expose a patient just to test networking.

## Technical-quality suggestions

Sharpness, contrast, exposure balance, and clipping are used to suggest a frame.
This is **not diagnosis or a clinically validated “best X-ray” decision**. The
clinician must make the final selection; retain the original machine workflow.

## Updates

The app checks for updates automatically and offers **Update now** or **Later**
when a newer version is published here. **Update now** downloads and verifies the
update inside the app, displays progress, closes the image worker cleanly, applies
the update in the background, and reopens OrthoVision automatically. You do not
download an installer manually or complete a Setup wizard again. Windows may
request administrator permission. The workstation is never rebooted automatically;
if a Windows restart is necessary, the app explains this instead of reopening.
Finish the
procedure and save needed images before updating. Upgrades preserve settings and
saved captures. Builds made before this repository was configured may need a
one-time manual installation of the latest release to use this update feed.
An installed updater-enabled v1.0.1 can update to v1.0.2 using **Update now**;
activation is required when the new build restarts. The unlicensed v1.0.1 release
and installer have been retired from current downloads. Copies previously
downloaded or available through Git history cannot be revoked remotely.

## Uninstall

Use Windows **Installed apps** or **Uninstall OrthoVision** in the Start menu.
The uninstaller removes installed program files, shortcuts, registration, and
known settings and the saved license for the uninstalling Windows account. Saved X-ray captures,
imported originals, untracked user files, and the shared Visual C++ runtime are
preserved. Delete retained patient images separately only under your retention
and privacy policy.
