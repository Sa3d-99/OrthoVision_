# OrthoVision v1.0.2

v1.0.2 introduces offline RSA-3072 device-bound activation, startup-only license validation, and a persistent non-blocking renewal warning for licenses expiring within 30 days. Active viewer sessions are never interrupted by license expiry. The public key only is bundled; signing tools and the private key remain owner-only. Existing updater-enabled v1.0.1 installations can choose Update now to upgrade and restart into activation. Captures and preferences are preserved. The unlicensed v1.0.1 release is retired only after this installer is verified and published.

Only the Windows installer is distributed here; app source is private. Image discovery requires a compatible export bridge, not just a LAN cable. No real C-arm integration has been validated.
