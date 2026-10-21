# Machinecoin Android Wallet

## Install on Android

[Download the APK](https://github.com/amberhollow-ops/machinecoin-android-wallet/releases/download/v0.1.2-alpha/Machinecoin-Android-arm64-experimental.apk)

Scan this QR code with your phone camera to download the APK directly:

![Download the Android wallet](https://github.com/amberhollow-ops/machinecoin-android-wallet/releases/download/v0.1.2-alpha/download-qr-screen-lock.png)

Open the downloaded file and confirm the Android installation prompt. If prompted, allow installation from your browser. Android system prompts follow your device language; the wallet interface is English.

## Experimental build

Requires Android 13 or later and ARM64. Designed for the Galaxy S23 Plus. This is a debug-signed development build, not a security-audited production wallet. Do not use it to hold valuable funds.

Private keys and transaction signing stay on your phone. The app runs a complete Machinecoin node without a separate server or Raspberry Pi. Initial synchronization downloads and validates the blockchain and requires storage, time, Wi-Fi and preferably a charger. Pruning is not enabled.

The node runs on demand. Turning off or locking the screen keeps the current synchronization session running. Switching away to another app while the screen is unlocked requests a clean shutdown after about 15 seconds. Use Stop node safely in the wallet or Stop safely in the notification to end the session. Android or Samsung battery restrictions may still affect long sessions.

### Features

- English wallet interface, dialogs and notifications
- Receive addresses with QR codes
- Local transaction signing and fee confirmation
- Password-encrypted wallet backups and restoration
- Transaction history and synchronization status

Backups are encrypted wallet files, not recovery-word lists. Keep the backup and its password safe. The password alone cannot restore the wallet.

### Validation

Android emulator tests passed for block validation, test-transaction signing and confirmation, encryption, rejection of an incorrect password, and backup restoration. Mainnet peer connections and header download were also tested. The first build has been reported to launch on a Galaxy; full synchronization and real-device payment/recovery tests remain unverified. APK signature and ZIP alignment were checked. SHA256SUMS.txt is included.

### Version 0.1.2 — Screen-off synchronization fix

Fixed the activity lifecycle treating screen-off as leaving the app. Added screen/keyguard checks before scheduling and executing an automatic stop. The service keeps its CPU wake lock for the active session and releases it when stopped, rather than expiring after one hour.

Verified in the Android emulator: automatic display timeout reaches the asleep state while the same native node process remains alive beyond the previous stop deadline. Existing wallet and mainnet service tests also pass. Samsung-specific long-duration battery behavior still needs testing. Wallet data format and application identity are unchanged. Install as an update; do not uninstall the existing wallet or clear its data. Back up before updating.

This repository currently distributes an experimental APK and documentation. GitHub-generated source archives are not a complete source/build package.
