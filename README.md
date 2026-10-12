<p align="center"><img src="assets/orthovision_icon.png" width="144" alt="OrthoVision icon"></p>

<h1 align="center">OrthoVision for Windows</h1>

<p align="center">A focused, dark-mode viewer for exported C-arm X-ray images.</p>

<p align="center"><a href="https://github.com/Sa3d-99/OrthoVision_/releases/latest"><strong>Download the latest Windows installer</strong></a></p>

This is the official **installer distribution repository**. Application source is
maintained privately. Installers include the compiled app, its runtime files,
and the Microsoft-signed Visual C++ x64 prerequisite—not the Flutter project.
The current installer is visible directly in the repository root, not inside a
folder. [Download OrthoVision v1.0.6](https://github.com/Sa3d-99/OrthoVision_/releases/download/v1.0.6/OrthoVision-Setup.exe).

## Install

1. Open **Releases** and download `OrthoVision-Setup.exe`.
2. Run Setup on Windows 10/11 x64 and approve Windows administrator permission.
3. Launch OrthoVision from the Start menu or optional desktop shortcut.
4. Activate with a device-bound license from your OrthoVision administrator.

Setup installs the app and checks its Visual C++ runtime dependency. The app
installer itself is not Authenticode-signed; Windows may display a publisher or
SmartScreen warning. Download only from this repository and check the published
SHA-256 digest if needed. Do not bypass your hospital's security policies.

The main installer is always `OrthoVision-Setup.exe`; the version is shown in
its properties and the app's bottom footer. Releases also contain an identical
version-named compatibility asset so older installed updaters can find the update.

## Activate and renew

OrthoVision opens its dashboard directly. Without a valid license, a
frosted-glass blur locks the image area and operational controls are disabled.
The LAN receiver and updater stay off. Window controls and Settings remain
available. No internet connection is needed for activation or capture.

1. Open **Settings > License**. Select a physical Ethernet/Wi-Fi adapter and click
   **Copy device MAC**. Send that MAC address to your administrator.
2. The administrator issues a signed license for this device and an agreed end
   date, or a lifetime license. Paste the complete compact `OVL2.…` code and
   select **Activate**. Existing `OVL1.…` licenses continue to work.
3. The app stores the accepted license for future launches. An invalid,
   different-device, or expired code leaves the dashboard locked and displays an
   error in the License panel. A correct code immediately unlocks the viewer and
   starts capture; no restart is required for first activation. A saved valid code
   unlocks automatically on later launches, without a popup or separate screen.
   MAC discovery uses a direct local Windows API for fast startup.
4. If 30 days or less remain at startup, a persistent top banner asks you to
   contact support. It does not cover the image or interrupt capture.
5. To renew, obtain a replacement code, close the app **after the procedure**,
   and restart. If the saved code has expired, enter the replacement on the
   License panel in Settings. To replace a still-valid code early, close OrthoVision,
   remove only `%APPDATA%\OrthoVision\OrthoVision\license.txt`, then reopen and
   enter the replacement. Do not remove capture files or other settings.

**Licensing is startup/pre-activation only:** once the viewer is unlocked, expiry during that session
never locks the screen, blocks reception, or closes the app. The next launch
checks the license again. The banner's day count is a startup snapshot, rounded
up. The administrator's end date is inclusive in UTC. Keep Windows date/time
correct. MAC changes (including Wi-Fi randomization or adapter replacement) can
require a new license; an unplugged licensed adapter can still be recognized.
Prefer the adapter's **hardware** MAC when requesting a license. Version 1.0.3
also recognizes permanent hardware addresses to reduce Wi-Fi randomization issues.

Open **Settings > License** (shield icon) for the device MAC, license ID, and
valid-through date or **Lifetime license · No expiry**. Before activation this
panel accepts a code; after activation it is read-only session information.
Opening Settings does not rerun validation or interrupt capture.
Lifetime licenses never show an expiry warning. New compact/lifetime codes
require v1.0.3 or later, while your existing dated v1.0.2 codes remain supported.

## Review images

- **Find devices:** view LAN adapters, cable/link status, known LAN neighbors, and
  compatible image-export bridges. Click **Connect** beside a compatible bridge;
  its TCP image port is detected automatically.
- **LAN preview:** receive exported PNG/JPEG/BMP/WebP captures and display the
  strongest technical-quality frame from each capture burst. Noise-aware scoring
  discounts pixel noise; Best changes only for a meaningful score improvement.
  v1.0.6 excludes black/white perimeter background and peripheral labels from
  scoring, checks native-resolution grain, and strengthens blur/clipping/blank
  penalties. Original images are never cropped or modified. Corrupt frames cannot
  replace Best, and LAN ranking restarts after a local import. These are technical
  suggestions, not a clinically validated quality judgment; the clinician chooses.
- **Best / Latest:** hold the suggested Best or view every incoming frame live,
  including weaker ones. Latest is not a capture-history archive. Metrics and
  Manual Save apply to the image on screen; original pixels are unchanged.
- **Connection badge:** LAN READY means the local receiver has a LAN address and
  is listening. SENDER CONNECTED means a TCP sender session is active. Returning
  to LAN READY between individual captures is normal, not a transfer failure.
- **Local receiver IP / Setup Guide:** read the laptop's active IPv4 address and
  listening port in the integrated title bar. Copy IP/port, refresh after connecting a cable,
  or choose another active interface from the dark, step-by-step guide.
- **Auto Save:** turn automatic retention on or off. Only the top 10 ranked
  automatic captures are retained; weaker automatic captures are deleted.
- **Manual Save:** keep the displayed source image explicitly. Manual saves are
  not removed by the automatic top-10 limit.
- **Open Image:** import a supported local image for review.
- **Brightness:** adjust the preview without modifying source pixels or saves.
- **Positive / Negative:** switch original or inverted display polarity; saved
  captures always keep their original pixels.
- **Zoom / pan / Reset view:** zoom from 50% to 400%, drag to pan, or reset zoom,
  polarity and brightness together.
- **Full screen:** fill the monitor with the image viewer, hiding the workspace
  header, footer and side panels. Exit full screen or Escape restores the window;
  zoom and pan are preserved. F11 toggles full screen. Close and any license renewal warning stay available.
- **Dark glass workspace:** frosted translucent panels without decorative overline
  labels, integrated draggable title bar, outline controls,
  and brief reduced-motion-aware transitions. Latest remains immediate during
  rapid image arrival; saved files, licensing and the receiver are unchanged.
- **Settings:** choose a persistent capture folder and view update status.
- **Window controls:** minimize, maximize/restore, or close with graceful worker
  shutdown. The layout adapts to the window size.
- **Installed version:** shown in the bottom footer; the current release is v1.0.6.

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
