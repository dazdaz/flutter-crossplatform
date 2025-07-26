# Hello World App with Flutter for Android and iOS

This guide walks you through creating a simple "Hello World" Flutter app that runs on both Android and iOS, using a Mac for development. The process includes setting up the environment, creating the project, writing the code, and running it on simulators/emulators. Setup may take 30-60 minutes for first-time users due to software downloads and configuration.

## Prerequisites

* A Mac computer with macOS.
* Basic familiarity with the terminal and code editors.
* Internet connection for downloading software and dependencies.

## Step 1: Set Up Your Development Environment

1.  **Install Flutter SDK**:
    * Download the Flutter SDK from <https://flutter.dev/docs/get-started/install/macos>.
    * Unzip the downloaded file and move it to a folder (e.g., `~/Development/flutter`).
    * Add Flutter to your PATH by editing `~/.zshrc` or `~/.bash_profile`:

        ```bash
        export PATH="$PATH:~/Development/flutter/bin"
        ```

    * Run `source ~/.zshrc` (or `~/.bash_profile`) to apply changes.
    * Verify with `flutter --version`.

2.  **Install Xcode (for iOS development)**:
    * Download Xcode from the Mac App Store: <https://apps.apple.com/us/app/xcode/id497799835> (free).
    * Open Xcode to accept the license and install command-line tools (prompted automatically, or run `xcode-select --install` in terminal).

3.  **Install Android Studio (for Android development)**:
    * Download Android Studio from <https://developer.android.com/studio>.
    * Install it, then open Android Studio and use the SDK Manager to install:
        * Android SDK Platform (latest, e.g., Android 15).
        * Android SDK Build-Tools.
        * Android Emulator.
    * Add Android SDK to your PATH in `~/.zshrc` or `~/.bash_profile`:

        ```bash
        export ANDROID_HOME=$HOME/Library/Android/sdk
        ```

    * Run `source ~/.zshrc` to apply.

3.5.  **Install Ruby 3.4.5**:

         brew install rbenv ruby-build
         echo 'eval "$(rbenv init -)"' >> ~/.bash_profile # For bash
         source ~/.bash_profile # For bash
         rbenv install -l
         rbenv install 3.4.5
         rbenv global 3.4.5
         ruby -v
         which ruby
         gem update --system
         gem update


4.  **Install CocoaPods (for iOS dependencies)**:
    * Install via terminal: `sudo gem install cocoapods`.
    * Verify with `pod --version`.

5.  **Optional: Install Visual Studio Code**:
    * Download from <https://code.visualstudio.com/download>.
    * Install the Flutter and Dart extensions for better coding support.

6.  **Verify Setup**:
    * Run `flutter doctor` in the terminal to check your environment. Follow any instructions to resolve issues (e.g., accepting Android licenses with `flutter doctor --android-licenses`).

## Step 2: Create the Flutter Project

1.  Open a terminal and navigate to your desired project directory:

    ```bash
    cd ~/Development
    ```

2.  Create a new Flutter project:

    ```bash
    flutter create hello_world_app
    ```

3.  Navigate into the project:

    ```bash
    cd hello_world_app
    ```

## Step 3: Write the "Hello World" Code

1.  Open the project in Visual Studio Code:

    ```bash
    code .
    ```

2.  Open the `lib/main.dart` file and replace its contents with the following code to display a simple "Hello, World!" screen:

    ```dart
    import 'package:flutter/material.dart';

    void main() {
      runApp(const MyApp());
    }

    class MyApp extends StatelessWidget {
      const MyApp({super.key});

      @override
      Widget build(BuildContext context) {
        return MaterialApp(
          title: 'Hello World App',
          theme: ThemeData(
            primarySwatch: Colors.blue,
          ),
          home: Scaffold(
            appBar: AppBar(
              title: const Text('Hello World'),
            ),
            body: const Center(
              child: Text(
                'Hello, World!',
                style: TextStyle(fontSize: 24),
              ),
            ),
          ),
        );
      }
    }
    ```

## Step 4: Run on iOS Simulator

1.  Ensure an iOS simulator is available in Xcode (Window > Devices and Simulators).
2.  From the project root, run:

    ```bash
    flutter run
    ```

3.  Select the iOS simulator when prompted. The app will build and launch, displaying "Hello, World!".

## Step 5: Run on Android Emulator

1.  Open Android Studio, go to Tools > AVD Manager, and create/start an emulator (e.g., Pixel 6 with the latest Android version).
2.  From the project root, run:

    ```bash
    flutter run
    ```

3.  Select the Android emulator. The app will build and launch.

## Step 6: Build and Deploy (Optional for Production)

### For iOS:

* Run `flutter build ios` to generate build files.
* Open `ios/Runner.xcworkspace` in Xcode to archive and create an `.ipa` file for distribution (requires an [Apple Developer account](https://developer.apple.com/account/) for real devices or App Store).

### For Android:

* Run `flutter build apk` to generate an `.apk` file (or `flutter build appbundle` for a `.aab` file).
* Install on a device via `adb install` or upload to Google Play (requires a [Google Play Console account](https://play.google.com/console)).

### Physical Devices:

* Connect via USB, enable developer options/USB debugging (Android) or trust the Mac (iOS), then use `flutter run`.

## Troubleshooting

* If errors occur, run `flutter doctor` to diagnose issues.
* Check the [Flutter documentation](https://flutter.dev/docs) for detailed guides.
* Search [Stack Overflow](https://stackoverflow.com/questions/tagged/flutter) for specific error messages.
* For iOS issues, ensure `pod install` was run in the `ios/` directory.
* For Android, verify the emulator is running or the device is connected.

## Additional Resources

* [Flutter Official Site](https://flutter.dev/)
* [Flutter Installation Guide](https://flutter.dev/docs/get-started/install/macos)
* [React Native vs. Flutter Comparison](https://www.geeksforgeeks.org/react-native-vs-flutter-which-one-to-choose-for-app-development/) (if considering alternatives)
