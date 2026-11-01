# Calculator Vault — Android project

A native Kotlin + Jetpack Compose Android app. The launcher is disguised as a calculator. On first launch, create a 4- or 6-digit PIN. Enter that PIN in the calculator and press `=` to open the vault.

## Build an APK

1. Extract this ZIP on a computer with Android Studio installed.
2. Open the extracted `CalculatorVault` folder in Android Studio.
3. Install Android SDK Platform 35 and use JDK 17 if Android Studio asks.
4. Wait for Gradle sync to finish (internet is needed the first time to download dependencies).
5. Select **Build → Build Bundle(s) / APK(s) → Build APK(s)**.
6. Android Studio shows a notification with **Locate**. The APK is normally at `app/build/outputs/apk/debug/app-debug.apk`.
7. Transfer that APK to your Android phone and install it. Allow installation from that file manager if Android asks.

## Current features

- Calculator with basic decimal arithmetic.
- First-run PIN creation and confirmation.
- PIN is stored as a salted PBKDF2-HMAC-SHA256 hash in DataStore.
- Secret PIN + `=` opens the vault.
- Imported files are encrypted with AES-256-GCM using an Android Keystore key; export decrypts them back to a chosen destination.
- Vault is locked when the app is sent to the background.

## Important security notes

This is a starter implementation, not a professionally audited secure-storage product. The calculator interface is a disguise, not a guarantee that the app cannot be discovered. There is no PIN retry lockout or biometric unlock yet. Keep a separate backup of important originals before relying on vault storage. Uninstalling the app or clearing its data can permanently remove the locally stored encryption key and vault files.
