<p align="center"><img src="assets/orthovision_icon.png" width="144" alt="OrthoVision icon"></p>

<h1 align="center">OrthoVision for Windows</h1>

<p align="center">A focused, dark-mode viewer for exported C-arm X-ray images.</p>

<p align="center"><a href="https://github.com/Sa3d-99/OrthoVision_/releases/latest"><strong>Download the latest Windows installer</strong></a></p>

This is the official **installer distribution repository**. Application source is
maintained privately. Installers include the compiled app, its runtime files,
and the Microsoft-signed Visual C++ x64 prerequisite—not the Flutter project.
The current installer is visible directly in the repository root, not inside a
folder. [Download OrthoVision v1.0.1](https://github.com/Sa3d-99/OrthoVision_/releases/download/v1.0.1/OrthoVision-Setup-1.0.1.exe).

## Install

1. Open **Releases** and download `OrthoVision-Setup-<version>.exe`.
2. Run Setup on Windows 10/11 x64 and approve Windows administrator permission.
3. Launch OrthoVision from the Start menu or optional desktop shortcut.

Setup installs the app and checks its Visual C++ runtime dependency. The app
installer itself is not Authenticode-signed; Windows may display a publisher or
SmartScreen warning. Download only from this repository and check the published
SHA-256 digest if needed. Do not bypass your hospital's security policies.

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
one-time manual installation of v1.0.1 to use this update feed.
This v1.0.1 release was replaced at the owner's request before distribution. A PC
already running the earlier v1.0.1 build must reinstall once: updates compare
version numbers and do not replace equal versions. Later higher-version releases
use the in-app update-and-restart flow above.

## Uninstall

Use Windows **Installed apps** or **Uninstall OrthoVision** in the Start menu.
The uninstaller removes installed program files, shortcuts, registration, and
known settings for the uninstalling Windows account. Saved X-ray captures,
imported originals, untracked user files, and the shared Visual C++ runtime are
preserved. Delete retained patient images separately only under your retention
and privacy policy.
