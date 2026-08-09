# Jahanzaib AI Android Companion

This native companion adds Android-only controls to the existing PC assistant and
browser dashboard. It does not replace the dashboard: chat, phone microphone, file
sharing, camera/screen requests and the live avatar remain in the dashboard.

## Build

1. Install Android Studio (JDK 17) and open this `android-companion` folder.
2. Let Android Studio install Android SDK 35 and sync Gradle.
3. Choose **Build > Build APK(s)**. The debug APK is written below
   `app/build/outputs/apk/debug/`.
4. Install the APK on your own Android phone. Android may ask you to allow this
   one sideloaded app.

## Pair

1. Start Jahanzaib AI on the PC and press **Remote Control**.
2. Put the displayed HTTPS address and six-character one-time key in the app.
3. Grant only the permissions you want. Contacts are needed for spoken contact
   matching. “Modify system settings” is needed for brightness. “Do Not Disturb”
   access may be needed for silent mode on some phones.
4. Keep the foreground companion notification enabled; it is the visible proof
   that PC-to-phone control is active.

The first HTTPS connection uses trust-on-first-use for the PC's locally generated
self-signed certificate. The certificate fingerprint is pinned on the phone; a
later fingerprint change is rejected until **Forget link** is used.

## Honest Android/WhatsApp limits

- SIM calls open the Android dialer; the user taps **Call**.
- SMS and WhatsApp text open a pre-filled compose screen; the user taps **Send**.
- WhatsApp has no public consumer API for silently starting a voice/video call.
  `whatsapp_call` opens the matched chat and asks the user to tap the call icon.
- OEM battery managers may stop a long-running companion. Exclude this app from
  battery optimisation if the link is frequently closed.
