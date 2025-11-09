# 🚀 iOS-JL_Bluetooth SDK Onboarding Guide

Welcome! This guide provides a step-by-step onboarding experience for developers who are new to the JieLi Bluetooth SDK.

## 📋 Table of Contents

1. [Before You Begin](#before-you-begin)
2. [Setting Up Your Development Environment](#setting-up-your-development-environment)
3. [Downloading and Installing the SDK](#downloading-and-installing-the-sdk)
4. [Creating Your First Project](#creating-your-first-project)
5. [Running Demo Projects](#running-demo-projects)
6. [Basic Integration Guide](#basic-integration-guide)
7. [Common Troubleshooting](#common-troubleshooting)
8. [Next Steps](#next-steps)

---

## Before You Begin

### ✅ Prerequisites

Before starting development, ensure you have:

#### Hardware Requirements
- **iOS Device**: iPhone or iPad running iOS 12.0 or later
- **Mac Computer**: macOS 10.15 (Catalina) or later recommended
- **JieLi Bluetooth Device**: A JieLi audio device supporting RCSP protocol
  - Supported chipsets: AC693X, AC697X, AC695X, AC701N, etc.

#### Software Requirements
- **Xcode**: Version 13.0 or later (latest version recommended)
- **CocoaPods**: Version 1.10.0 or later (for dependency management)
- **Git**: For version control and SDK download

#### Development Knowledge
- Basic knowledge of **Objective-C** or **Swift**
- Understanding of iOS development fundamentals
- Basic understanding of Bluetooth Low Energy (BLE) concepts (recommended)

### 📖 SDK Overview

The JieLi Bluetooth SDK provides:

- 🎵 **Audio Device Control**: Volume, play/pause, track control
- 🔗 **BLE Connection Management**: Device scanning, pairing, connection management
- 🎤 **Audio Codecs**: Opus and Speex audio encoding/decoding
- 🔧 **OTA Updates**: Over-the-air firmware updates
- 🎧 **Advanced Features**: TWS earphones, ANC noise cancellation, Auracast support

---

## Setting Up Your Development Environment

### Step 1: Install Xcode

1. Download and install Xcode from the Mac App Store
2. Launch Xcode and complete the installation of additional components
3. Set up Xcode Command Line Tools in Terminal:
   ```bash
   xcode-select --install
   ```

### Step 2: Install CocoaPods

CocoaPods is an iOS dependency manager. Install it via Terminal:

```bash
# Install CocoaPods via Ruby gem
sudo gem install cocoapods

# Set up CocoaPods
pod setup
```

Verify installation:
```bash
pod --version
```

### Step 3: Configure iOS Developer Account

1. Sign in to [Apple Developer](https://developer.apple.com)
2. Add your Apple ID in Xcode's Preferences > Accounts
3. You can test on physical devices even with a free developer account

---

## Downloading and Installing the SDK

### Option 1: Git Clone (Recommended)

```bash
# Clone the repository
git clone https://github.com/Jieli-Tech/iOS-JL_Bluetooth.git

# Navigate to the directory
cd iOS-JL_Bluetooth
```

### Option 2: Download ZIP

1. Visit the [GitHub repository](https://github.com/Jieli-Tech/iOS-JL_Bluetooth)
2. Click the "Code" button and select "Download ZIP"
3. Extract the ZIP file

### Understanding the SDK Structure

After downloading, you'll see these directories:

```
iOS-JL_Bluetooth/
├── libs/           # Core SDK frameworks (start here!)
├── code/           # Demo applications
├── docs/           # Documentation and API references
├── README.md       # Project overview (Chinese)
└── README_EN.md    # Project overview (English)
```

### Key Frameworks

The `libs/` directory contains:

| Framework | Purpose |
|-----------|---------|
| `JL_BLEKit.xcframework` | Core Bluetooth connection library |
| `JL_OTALib.xcframework` | OTA (over-the-air) firmware updates |
| `JLAudioUnitKit.framework` | Audio encoding/decoding (Opus, Speex) |
| `JLDialUnit.xcframework` | Watch face processing for smart watches |
| `JLBmpConvertKit.xcframework` | Image conversion utilities |
| `JL_AdvParse.xcframework` | BLE advertisement parsing |

---

## Creating Your First Project

Let's quickly test the SDK features using the SDK Test Helper.

### Step 1: Open the SDK Test Helper Project

```bash
cd iOS-JL_Bluetooth/code/SDKTestHelper
open SDKTestHelper.xcworkspace
```

> ⚠️ **Important**: Always open the `.xcworkspace` file (not `.xcodeproj`!). This ensures CocoaPods dependencies are included.

### Step 2: Install Dependencies

The project is already configured, but if dependencies are missing:

```bash
pod install
```

### Step 3: Build and Run the Project

1. In Xcode, select your development team in the top toolbar
2. Connect your iOS device (simulators don't support Bluetooth)
3. Select your target device
4. Press ⌘ + R or click the "Run" button

### Step 4: Grant Permissions

When the app launches for the first time:
1. Allow Bluetooth permissions
2. Allow local network permissions (if prompted)

### Step 5: Test Device Connection

1. Power on your JieLi Bluetooth device
2. Tap the "Scan" button in the app
3. Select your device from the list
4. Wait for connection
5. Test the features!

---

## Running Demo Projects

The SDK includes three main demo projects:

### 1. SDKTestHelper (Recommended Starting Point)

**Purpose**: Comprehensive testing tool for SDK APIs

**Features**:
- ✅ Device discovery and connection
- ✅ Audio codec testing
- ✅ Auracast broadcast functionality
- ✅ Logging and debugging tools

**How to run**:
```bash
cd code/SDKTestHelper
open SDKTestHelper.xcworkspace
```

### 2. JieLi_Home_Demo (Full-Featured App)

**Purpose**: Complete application example with full functionality

**Features**:
- ✅ Complete user interface
- ✅ Device management
- ✅ Music playback control
- ✅ Equalizer and sound effects
- ✅ Karaoke features

**How to run**:
```bash
cd code/JieLi_Home_Demo
open NewJieliZhiNeng.xcworkspace
```

### 3. JLAudioUnitKitDemo (Audio Codec Focus)

**Purpose**: Focused on audio encoding/decoding

**Features**:
- ✅ Opus codec examples
- ✅ Speex codec examples
- ✅ Audio processing pipeline

**How to run**:
```bash
cd code/JLAudioUnitKitDemo_V1.3.0_Beta1_20250827/code/JLAudioUnitKitDemo
open JLAudioUnitKitDemo.xcworkspace
```

---

## Basic Integration Guide

### Integrating the SDK into a New Project

#### Step 1: Create a New Xcode Project

1. Open Xcode
2. Select "Create a new Xcode project"
3. Choose "iOS" > "App"
4. Fill in project details:
   - Product Name: "MyJieLiApp"
   - Language: Swift or Objective-C
   - Interface: UIKit

#### Step 2: Add SDK Frameworks

1. Drag and drop the following frameworks into your Xcode project:
   ```
   libs/JL_BLEKit.xcframework
   libs/JL_OTALib.xcframework
   libs/JLLogHelper.xcframework
   ```

2. Check "Copy items if needed"
3. Ensure frameworks are selected for your target

#### Step 3: Configure Info.plist

Add these permissions to your project's `Info.plist`:

```xml
<key>NSBluetoothAlwaysUsageDescription</key>
<string>We need Bluetooth access to communicate with JieLi devices</string>

<key>NSBluetoothPeripheralUsageDescription</key>
<string>Bluetooth is required to connect to peripherals</string>

<key>NSLocalNetworkUsageDescription</key>
<string>Local network communication is required</string>
```

#### Step 4: Add CocoaPods Dependencies (Optional)

Create a Podfile:
```ruby
platform :ios, '12.0'
use_frameworks!

target 'MyJieLiApp' do
  pod 'RxSwift', '~> 6.0'
  pod 'RxCocoa', '~> 6.0'
  pod 'SnapKit', '~> 5.0'
end
```

Install:
```bash
pod install
```

#### Step 5: Initialize the SDK (Swift)

```swift
import UIKit
import JL_BLEKit

@main
class AppDelegate: UIResponder, UIApplicationDelegate {
    
    func application(_ application: UIApplication, 
                    didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {
        
        // Initialize SDK
        JL_RunSDK.share()
        
        return true
    }
}
```

#### Step 5: Initialize the SDK (Objective-C)

```objective-c
#import <JL_BLEKit/JL_BLEKit.h>

- (BOOL)application:(UIApplication *)application 
    didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
    
    // Initialize SDK
    [JL_RunSDK share];
    
    return YES;
}
```

#### Step 6: Implement Device Discovery

**Swift Example:**

```swift
import JL_BLEKit

class BluetoothManager {
    
    func startScanning() {
        // Start BLE scanning
        JL_RunSDK.share().startScanBLE()
        
        // Observe discovered devices
        NotificationCenter.default.addObserver(
            self,
            selector: #selector(handleDeviceFound(_:)),
            name: NSNotification.Name("kJL_BLE_FOUND"),
            object: nil
        )
    }
    
    @objc func handleDeviceFound(_ notification: Notification) {
        guard let device = notification.object as? JL_BLEEntity else { return }
        print("Device found: \(device.mName ?? "Unknown")")
        
        // Connect to the device
        connectToDevice(device)
    }
    
    func connectToDevice(_ device: JL_BLEEntity) {
        JL_RunSDK.share().connectBLE(device)
    }
    
    func stopScanning() {
        JL_RunSDK.share().stopScanBLE()
    }
}
```

#### Step 7: Handle Connection Status

```swift
class BluetoothManager {
    
    func observeConnectionStatus() {
        NotificationCenter.default.addObserver(
            self,
            selector: #selector(handleConnectionStatus(_:)),
            name: NSNotification.Name("kJL_BLE_CONNECTED"),
            object: nil
        )
        
        NotificationCenter.default.addObserver(
            self,
            selector: #selector(handleDisconnection(_:)),
            name: NSNotification.Name("kJL_BLE_DISCONNECTED"),
            object: nil
        )
    }
    
    @objc func handleConnectionStatus(_ notification: Notification) {
        print("Device connected!")
        // Update UI or initialize features here
    }
    
    @objc func handleDisconnection(_ notification: Notification) {
        print("Device disconnected")
        // Handle disconnection
    }
}
```

---

## Common Troubleshooting

### Issue 1: "Framework not found JL_BLEKit"

**Solution:**
1. Verify frameworks are properly added to the project
2. Check Build Settings > Framework Search Paths
3. Clean Build Folder (⇧⌘K) and rebuild

### Issue 2: Bluetooth Devices Not Appearing

**Solution:**
1. Ensure JieLi device is powered on and in pairing mode
2. Verify Bluetooth permissions are added in Info.plist
3. Confirm you're using a physical iOS device (not simulator)
4. Check that Bluetooth is enabled in iOS Settings

### Issue 3: App Crashes with "dyld: Library not loaded"

**Solution:**
1. Verify frameworks are set to "Embed & Sign" in Build Settings
2. Check General > Frameworks, Libraries, and Embedded Content
3. Change from "Embed Without Signing" to "Embed & Sign"

### Issue 4: CocoaPods Dependency Issues

**Solution:**
```bash
# Clean CocoaPods cache
pod cache clean --all

# Remove Pods directory
rm -rf Pods/

# Remove Podfile.lock
rm Podfile.lock

# Reinstall
pod install
```

### Issue 5: Xcode Signing Issues

**Solution:**
1. Add your Apple ID in Xcode > Preferences > Accounts
2. In Project Settings > Signing & Capabilities
3. Enable "Automatically manage signing"
4. Select your development team

---

## Next Steps

Congratulations! You've mastered the basics of the JieLi Bluetooth SDK. Continue with these next steps:

### 📚 Learning Resources

1. **Read the API Documentation**
   - [Online Documentation](https://doc.zh-jieli.com/Apps/iOS/jielihome/zh-cn/master/index.html)
   - Local documentation in `docs/` directory

2. **Explore Demo Code**
   - `SDKTestHelper` - API usage examples
   - `JieLi_Home_Demo` - Full app architecture
   - `JLAudioUnitKitDemo` - Audio processing

3. **Understand Advanced Features**
   - TWS earphone connectivity
   - ANC noise cancellation
   - OTA firmware updates
   - Auracast audio broadcasting

### 🎯 Practice Projects

Start with a simple app:

**Project Idea 1: Basic Music Controller**
- Device discovery and connection
- Play/pause buttons
- Volume slider
- Track next/previous

**Project Idea 2: Device Manager**
- List multiple devices
- Show battery status
- Connect/disconnect functionality
- Settings synchronization

**Project Idea 3: Audio Streaming**
- Capture microphone input
- Encode with Opus
- Stream over Bluetooth
- Monitor audio quality

### 🔧 Development Best Practices

1. **Always test on physical devices** - Simulators don't support Bluetooth
2. **Handle disconnections gracefully** - Connections can drop unexpectedly
3. **Implement error handling** - Wrap SDK operations in try-catch
4. **Manage memory** - Unregister observers and clean up connections
5. **Keep users informed** - Show Bluetooth status and connection state

### 📞 Getting Help

Stuck? Use these resources:

- 📖 [SDK Documentation](https://doc.zh-jieli.com/)
- 🌐 [JieLi Official Website](https://www.zh-jieli.com/)
- 📧 Technical Support: Contact through official channels
- 💬 Community Forums and Discussions

### 🎉 You're Ready!

You're now ready to build powerful iOS applications with the JieLi Bluetooth SDK!

Happy coding! 🚀

---

## 📝 Additional References

### Code Snippet References

- [Swift Integration Example](./code/SDKTestHelper/)
- [Objective-C Integration Example](./code/JieLi_Home_Demo/)
- [Audio Processing](./code/JLAudioUnitKitDemo_V1.3.0_Beta1_20250827/)

### Documentation Files

- [API Specifications](./docs/JL_OTALib.framework API 说明.md)
- [Release Notes](./docs/杰理之家SDK(iOS)发布记录.pdf)
- [Platform Integration Guide](./docs/杰理开放平台接入说明文档_V1.0.3.pdf)

### Project Information

- **License**: Apache 2.0
- **Company**: 珠海市杰理科技股份有限公司 (Zhuhai JieLi Technology Co., Ltd.)
- **Minimum iOS Version**: 12.0+

---

<div align="center">

**Happy Development! Feel free to reach out with questions! 🎵**

© 2024 JieLi Technology | Apache License 2.0

</div>
