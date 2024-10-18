# Facebook SDK Integration in Flutter

## Prerequisites

- **Facebook Developer Account:** A registered app with access to the App ID and Client Token.
- **Privacy Policy:** Updated and accessible within the app.
- **Development Environment:**
  - **Flutter SDK Version:** Latest stable release.
  - **Dart SDK Version:** Compatible with the Flutter SDK used.
  - **Development Tools:** Android Studio or VS Code with Flutter and Dart plugins.

## Adding Facebook SDK to the Flutter Project

### Add Dependencies

Add the `facebook_app_events` plugin to your `pubspec.yaml` file:

```yaml
dependencies:
  flutter:
    sdk: flutter
  facebook_app_events: ^0.14.0  # Use the latest version
```
Run flutter pub get to fetch the package.

## Android Integration

Add Facebook App ID

In android/app/src/main/AndroidManifest.xml, within the <application> tag, add:
```xml
<meta-data android:name="com.facebook.sdk.ApplicationId" android:value="@string/facebook_app_id"/>
```
In android/app/src/main/res/values/strings.xml, add:
```xml
<string name="facebook_app_id">YOUR_FACEBOOK_APP_ID</string>
```
**Initialize the SDK**

No explicit initialization is required; the facebook_app_events plugin handles it automatically.

## iOS Integration

**Add Facebook App ID and Client Token**

In ios/Runner/Info.plist, add the following entries:

```xml
<key>FacebookAppID</key>
<string>YOUR_FACEBOOK_APP_ID</string>
<key>FacebookClientToken</key>
<string>YOUR_FACEBOOK_CLIENT_TOKEN</string>
<key>CFBundleURLTypes</key>
<array>
  <dict>
    <key>CFBundleURLSchemes</key>
    <array>
      <string>fbYOUR_FACEBOOK_APP_ID</string>
    </array>
  </dict>
</array>
```

**Initialize the SDK**

In ios/Runner/AppDelegate.swift (for Swift) or AppDelegate.m (for Objective-C), add:

```swift
import UIKit
import Flutter
import FBSDKCoreKit

@UIApplicationMain
@objc class AppDelegate: FlutterAppDelegate {
  override func application(
    _ application: UIApplication,
    didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?
  ) -> Bool {
    ApplicationDelegate.shared.application(
      application,
      didFinishLaunchingWithOptions: launchOptions
    )
    GeneratedPluginRegistrant.register(with: self)
    return super.application(application, didFinishLaunchingWithOptions: launchOptions)
  }
}
```
## Handling User Consent

Implement mechanisms to obtain user consent for data collection in compliance with GDPR and CCPA. Use the setAdvertiserTrackingEnabled method to reflect user consent:

```dart
bool userConsent = await getUserConsentStatus();
FacebookAppEvents.setAdvertiserTracking(enabled: userConsent);
```
