# MoveSwipe prototype

MoveSwipe is an Android prototype for turning body movements into four directional swipe commands for Subway Surfers. Both phones must be on the same Wi-Fi network. The game phone runs the receiver and needs Android Accessibility permission so it can perform swipe gestures. The controller phone reads linear acceleration (gravity removed) and sends a direction over the local network.

## Prototype thresholds

- Left/right: lateral acceleration above 2.0 m/s² for 100 ms.
- Up/down: vertical acceleration above 2.5 m/s² for 100 ms.
- 500 ms cooldown between commands.

These are starting values. Phone placement and orientation matter; calibrate with the phone secured firmly at the waist, screen facing forward. Do not hold or swing a phone while jumping. Keep the play area clear.

## Build on GitHub

The included GitHub Actions workflow builds a debug APK on pushes to `main` or `master`, pull requests, and manual runs.

1. Create a GitHub repository and upload the contents of this `outputs` folder to its root.
2. Push to `main` (or `master`), or open **Actions → Build Android APK → Run workflow**.
3. Open the completed workflow run and download the `moveswipe-debug-apk` artifact.
4. Extract the downloaded ZIP. Install `app-debug.apk` on both Android phones. You may need to allow installation from your browser or file manager.

This is an unsigned debug APK, suitable for personal testing. It is not a Play Store release build.

## Pair and play

1. Install the app on both Android phones.
2. On the game phone, choose **Receiver**, enable MoveSwipe in Android Accessibility settings, and start the receiver. The screen shows its local Wi-Fi IP address and port `8765`.
3. On the controller phone, choose **Controller**, enter that IP, and connect.
4. Secure the controller phone at your waist and use **Calibrate neutral** while standing upright.
5. Start Subway Surfers on the receiver phone. Use the large **Test swipe** buttons first, then motion control.

Android may show an accessibility-service disclosure when it is enabled. MoveSwipe uses this permission only to dispatch the four swipe gestures requested by the controller.
