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
Initialize the SDK
No explicit initialization is required; the facebook_app_events plugin handles it automatically.
