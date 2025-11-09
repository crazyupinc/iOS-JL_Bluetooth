# 🚀 iOS-JL_Bluetooth SDK 온보딩 가이드

환영합니다! 이 가이드는 JieLi Bluetooth SDK를 처음 사용하는 개발자를 위한 단계별 온보딩 문서입니다.

## 📋 목차

1. [시작하기 전에](#시작하기-전에)
2. [개발 환경 설정](#개발-환경-설정)
3. [SDK 다운로드 및 설치](#sdk-다운로드-및-설치)
4. [첫 번째 프로젝트 만들기](#첫-번째-프로젝트-만들기)
5. [데모 프로젝트 실행하기](#데모-프로젝트-실행하기)
6. [기본 통합 가이드](#기본-통합-가이드)
7. [일반적인 문제 해결](#일반적인-문제-해결)
8. [다음 단계](#다음-단계)

---

## 시작하기 전에

### ✅ 사전 요구사항

개발을 시작하기 전에 다음 사항을 확인하세요:

#### 하드웨어 요구사항
- **iOS 기기**: iOS 12.0 이상을 실행하는 iPhone 또는 iPad
- **Mac**: macOS 10.15 (Catalina) 이상 권장
- **JieLi 블루투스 기기**: RCSP 프로토콜을 지원하는 JieLi 음향 기기
  - 지원 칩셋: AC693X, AC697X, AC695X, AC701N 등

#### 소프트웨어 요구사항
- **Xcode**: 13.0 이상 (최신 버전 권장)
- **CocoaPods**: 1.10.0 이상 (의존성 관리용)
- **Git**: 버전 관리 및 SDK 다운로드용

#### 개발 지식
- **Objective-C** 또는 **Swift** 기본 지식
- iOS 개발 기초 이해
- 블루투스 Low Energy (BLE) 개념에 대한 기본 이해 (권장)

### 📖 SDK 개요

JieLi Bluetooth SDK는 다음을 제공합니다:

- 🎵 **음향 기기 제어**: 음량, 재생/일시정지, 트랙 제어
- 🔗 **BLE 연결 관리**: 기기 스캔, 페어링, 연결 관리
- 🎤 **오디오 코덱**: Opus, Speex 오디오 인코딩/디코딩
- 🔧 **OTA 업데이트**: 무선 펌웨어 업데이트
- 🎧 **고급 기능**: TWS 이어폰, ANC 노이즈 캔슬링, Auracast 지원

---

## 개발 환경 설정

### 1단계: Xcode 설치

1. Mac App Store에서 Xcode를 다운로드하고 설치합니다
2. Xcode를 실행하고 추가 구성 요소 설치를 완료합니다
3. 터미널에서 Xcode Command Line Tools를 설정합니다:
   ```bash
   xcode-select --install
   ```

### 2단계: CocoaPods 설치

CocoaPods는 iOS 의존성 관리자입니다. 터미널에서 설치하세요:

```bash
# Ruby gem을 통한 CocoaPods 설치
sudo gem install cocoapods

# CocoaPods 설정
pod setup
```

설치를 확인합니다:
```bash
pod --version
```

### 3단계: iOS 개발자 계정 설정

1. [Apple Developer](https://developer.apple.com)에 로그인합니다
2. Xcode의 Preferences > Accounts에서 Apple ID를 추가합니다
3. 무료 개발자 계정으로도 물리적 기기에서 테스트할 수 있습니다

---

## SDK 다운로드 및 설치

### 옵션 1: Git Clone (권장)

```bash
# 저장소 클론
git clone https://github.com/Jieli-Tech/iOS-JL_Bluetooth.git

# 디렉토리로 이동
cd iOS-JL_Bluetooth
```

### 옵션 2: ZIP 다운로드

1. [GitHub 저장소](https://github.com/Jieli-Tech/iOS-JL_Bluetooth)를 방문합니다
2. "Code" 버튼을 클릭하고 "Download ZIP"을 선택합니다
3. ZIP 파일을 압축 해제합니다

### SDK 구조 이해하기

다운로드 후 다음 디렉토리가 표시됩니다:

```
iOS-JL_Bluetooth/
├── libs/           # 핵심 SDK 프레임워크 (여기서 시작!)
├── code/           # 데모 애플리케이션
├── docs/           # 문서 및 API 참조
├── README.md       # 프로젝트 개요 (중국어)
└── README_EN.md    # 프로젝트 개요 (영어)
```

### 주요 프레임워크

`libs/` 디렉토리에는 다음이 포함됩니다:

| 프레임워크 | 목적 |
|-----------|------|
| `JL_BLEKit.xcframework` | 핵심 블루투스 연결 라이브러리 |
| `JL_OTALib.xcframework` | OTA (무선) 펌웨어 업데이트 |
| `JLAudioUnitKit.framework` | 오디오 인코딩/디코딩 (Opus, Speex) |
| `JLDialUnit.xcframework` | 스마트워치 문자판 처리 |
| `JLBmpConvertKit.xcframework` | 이미지 변환 유틸리티 |
| `JL_AdvParse.xcframework` | BLE 광고 파싱 |

---

## 첫 번째 프로젝트 만들기

SDK 테스트 도우미를 사용하여 SDK 기능을 빠르게 테스트해 봅시다.

### 1단계: SDK 테스트 도우미 프로젝트 열기

```bash
cd iOS-JL_Bluetooth/code/SDKTestHelper
open SDKTestHelper.xcworkspace
```

> ⚠️ **중요**: `.xcworkspace` 파일을 열어야 합니다 (`.xcodeproj` 아님!). 이렇게 하면 CocoaPods 의존성이 포함됩니다.

### 2단계: 의존성 설치

프로젝트가 이미 설정되어 있지만, 의존성이 누락된 경우:

```bash
pod install
```

### 3단계: 프로젝트 빌드 및 실행

1. Xcode에서 상단 도구 모음에서 개발 팀을 선택합니다
2. iOS 기기를 연결합니다 (시뮬레이터는 블루투스를 지원하지 않음)
3. 대상 기기를 선택합니다
4. ⌘ + R을 누르거나 "Run" 버튼을 클릭합니다

### 4단계: 권한 허용

앱을 처음 실행할 때:
1. 블루투스 권한 허용
2. 로컬 네트워크 권한 허용 (필요한 경우)

### 5단계: 기기 연결 테스트

1. JieLi 블루투스 기기의 전원을 켭니다
2. 앱에서 "스캔" 버튼을 탭합니다
3. 목록에서 기기를 선택합니다
4. 연결을 기다립니다
5. 기능을 테스트합니다!

---

## 데모 프로젝트 실행하기

SDK에는 세 가지 주요 데모 프로젝트가 포함되어 있습니다:

### 1. SDKTestHelper (권장 시작점)

**목적**: SDK API에 대한 포괄적인 테스트 도구

**특징**:
- ✅ 기기 검색 및 연결
- ✅ 오디오 코덱 테스트
- ✅ Auracast 브로드캐스트 기능
- ✅ 로깅 및 디버깅 도구

**실행 방법**:
```bash
cd code/SDKTestHelper
open SDKTestHelper.xcworkspace
```

### 2. JieLi_Home_Demo (전체 기능 앱)

**목적**: 완전한 기능을 갖춘 애플리케이션 예제

**특징**:
- ✅ 완전한 사용자 인터페이스
- ✅ 기기 관리
- ✅ 음악 재생 제어
- ✅ 이퀄라이저 및 음향 효과
- ✅ 카라오케 기능

**실행 방법**:
```bash
cd code/JieLi_Home_Demo
open NewJieliZhiNeng.xcworkspace
```

### 3. JLAudioUnitKitDemo (오디오 코덱)

**목적**: 오디오 인코딩/디코딩에 집중

**특징**:
- ✅ Opus 코덱 예제
- ✅ Speex 코덱 예제
- ✅ 오디오 처리 파이프라인

**실행 방법**:
```bash
cd code/JLAudioUnitKitDemo_V1.3.0_Beta1_20250827/code/JLAudioUnitKitDemo
open JLAudioUnitKitDemo.xcworkspace
```

---

## 기본 통합 가이드

### 새 프로젝트에 SDK 통합

#### 1단계: 새 Xcode 프로젝트 만들기

1. Xcode를 엽니다
2. "Create a new Xcode project"를 선택합니다
3. "iOS" > "App"을 선택합니다
4. 프로젝트 세부 정보를 입력합니다:
   - Product Name: "MyJieLiApp"
   - Language: Swift 또는 Objective-C
   - Interface: UIKit

#### 2단계: SDK 프레임워크 추가

1. Xcode 프로젝트에 다음 프레임워크를 드래그 앤 드롭합니다:
   ```
   libs/JL_BLEKit.xcframework
   libs/JL_OTALib.xcframework
   libs/JLLogHelper.xcframework
   ```

2. "Copy items if needed"를 체크합니다
3. 대상에서 프레임워크가 선택되었는지 확인합니다

#### 3단계: Info.plist 구성

프로젝트의 `Info.plist`에 다음 권한을 추가합니다:

```xml
<key>NSBluetoothAlwaysUsageDescription</key>
<string>JieLi 기기와 통신하기 위해 블루투스 액세스가 필요합니다</string>

<key>NSBluetoothPeripheralUsageDescription</key>
<string>주변 기기에 연결하기 위해 블루투스가 필요합니다</string>

<key>NSLocalNetworkUsageDescription</key>
<string>로컬 네트워크 통신이 필요합니다</string>
```

#### 4단계: CocoaPods 의존성 추가 (선택 사항)

Podfile을 만듭니다:
```ruby
platform :ios, '12.0'
use_frameworks!

target 'MyJieLiApp' do
  pod 'RxSwift', '~> 6.0'
  pod 'RxCocoa', '~> 6.0'
  pod 'SnapKit', '~> 5.0'
end
```

설치:
```bash
pod install
```

#### 5단계: SDK 초기화 (Swift)

```swift
import UIKit
import JL_BLEKit

@main
class AppDelegate: UIResponder, UIApplicationDelegate {
    
    func application(_ application: UIApplication, 
                    didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {
        
        // SDK 초기화
        JL_RunSDK.share()
        
        return true
    }
}
```

#### 5단계: SDK 초기화 (Objective-C)

```objective-c
#import <JL_BLEKit/JL_BLEKit.h>

- (BOOL)application:(UIApplication *)application 
    didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
    
    // SDK 초기화
    [JL_RunSDK share];
    
    return YES;
}
```

#### 6단계: 기기 검색 구현

**Swift 예제:**

```swift
import JL_BLEKit

class BluetoothManager {
    
    func startScanning() {
        // BLE 스캐닝 시작
        JL_RunSDK.share().startScanBLE()
        
        // 검색된 기기 관찰
        NotificationCenter.default.addObserver(
            self,
            selector: #selector(handleDeviceFound(_:)),
            name: NSNotification.Name("kJL_BLE_FOUND"),
            object: nil
        )
    }
    
    @objc func handleDeviceFound(_ notification: Notification) {
        guard let device = notification.object as? JL_BLEEntity else { return }
        print("기기 발견: \(device.mName ?? "Unknown")")
        
        // 기기에 연결
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

#### 7단계: 연결 상태 처리

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
        print("기기 연결됨!")
        // 여기서 UI 업데이트 또는 초기화
    }
    
    @objc func handleDisconnection(_ notification: Notification) {
        print("기기 연결 해제됨")
        // 연결 해제 처리
    }
}
```

---

## 일반적인 문제 해결

### 문제 1: "Framework not found JL_BLEKit"

**해결 방법:**
1. 프레임워크가 프로젝트에 올바르게 추가되었는지 확인
2. Build Settings > Framework Search Paths를 확인
3. Clean Build Folder (⇧⌘K) 후 다시 빌드

### 문제 2: 블루투스 기기가 발견되지 않음

**해결 방법:**
1. JieLi 기기의 전원이 켜져 있고 페어링 모드인지 확인
2. Info.plist에 블루투스 권한이 추가되었는지 확인
3. 물리적 iOS 기기를 사용 중인지 확인 (시뮬레이터 아님)
4. 블루투스가 iOS 설정에서 활성화되어 있는지 확인

### 문제 3: 앱이 충돌함 "dyld: Library not loaded"

**해결 방법:**
1. Build Settings에서 "Embed & Sign"으로 프레임워크가 설정되었는지 확인
2. General > Frameworks, Libraries, and Embedded Content를 확인
3. "Embed Without Signing"을 "Embed & Sign"으로 변경

### 문제 4: CocoaPods 의존성 문제

**해결 방법:**
```bash
# CocoaPods 캐시 정리
pod cache clean --all

# Pods 디렉토리 제거
rm -rf Pods/

# Podfile.lock 제거
rm Podfile.lock

# 재설치
pod install
```

### 문제 5: Xcode 서명 문제

**해결 방법:**
1. Xcode > Preferences > Accounts에서 Apple ID를 추가
2. 프로젝트 설정 > Signing & Capabilities에서
3. "Automatically manage signing"을 활성화
4. 개발 팀을 선택

---

## 다음 단계

축하합니다! 이제 JieLi Bluetooth SDK의 기본 사항을 익혔습니다. 다음 단계로 계속 진행하세요:

### 📚 학습 리소스

1. **API 문서 읽기**
   - [온라인 문서](https://doc.zh-jieli.com/Apps/iOS/jielihome/zh-cn/master/index.html)
   - `docs/` 디렉토리의 로컬 문서

2. **데모 코드 탐색**
   - `SDKTestHelper` - API 사용 예제
   - `JieLi_Home_Demo` - 전체 앱 구조
   - `JLAudioUnitKitDemo` - 오디오 처리

3. **고급 기능 이해**
   - TWS 이어폰 연결
   - ANC 노이즈 캔슬링
   - OTA 펌웨어 업데이트
   - Auracast 오디오 브로드캐스트

### 🎯 실습 프로젝트

간단한 앱부터 시작하세요:

**프로젝트 아이디어 1: 기본 음악 컨트롤러**
- 기기 검색 및 연결
- 재생/일시정지 버튼
- 음량 슬라이더
- 트랙 다음/이전

**프로젝트 아이디어 2: 기기 관리자**
- 여러 기기 나열
- 배터리 상태 표시
- 연결/연결 해제 기능
- 설정 동기화

**프로젝트 아이디어 3: 오디오 스트리밍**
- 마이크 입력 캡처
- Opus로 인코딩
- 블루투스로 스트리밍
- 오디오 품질 모니터링

### 🔧 개발 모범 사례

1. **항상 물리적 기기에서 테스트** - 시뮬레이터는 블루투스를 지원하지 않음
2. **연결 해제 우아하게 처리** - 연결이 예기치 않게 끊어질 수 있음
3. **오류 처리 구현** - SDK 작업을 try-catch로 래핑
4. **메모리 관리** - 옵저버 등록 해제 및 연결 정리
5. **사용자에게 알림** - 블루투스 상태와 연결 상태를 표시

### 📞 도움 받기

막혔나요? 다음 리소스를 사용하세요:

- 📖 [SDK 문서](https://doc.zh-jieli.com/)
- 🌐 [JieLi 공식 웹사이트](https://www.zh-jieli.com/)
- 📧 기술 지원: 공식 채널을 통해 문의
- 💬 커뮤니티 포럼 및 토론

### 🎉 성공!

이제 JieLi Bluetooth SDK로 강력한 iOS 애플리케이션을 구축할 준비가 되었습니다!

즐거운 코딩하세요! 🚀

---

## 📝 추가 참고 자료

### 코드 스니펫 참조

- [Swift 통합 예제](./code/SDKTestHelper/)
- [Objective-C 통합 예제](./code/JieLi_Home_Demo/)
- [오디오 처리](./code/JLAudioUnitKitDemo_V1.3.0_Beta1_20250827/)

### 문서 파일

- [API 사양](./docs/JL_OTALib.framework API 说明.md)
- [릴리스 노트](./docs/杰理之家SDK(iOS)发布记录.pdf)
- [플랫폼 통합 가이드](./docs/杰理开放平台接入说明文档_V1.0.3.pdf)

### 프로젝트 정보

- **라이선스**: Apache 2.0
- **회사**: 珠海市杰理科技股份有限公司 (Zhuhai JieLi Technology Co., Ltd.)
- **최소 iOS 버전**: 12.0+

---

<div align="center">

**즐거운 개발되세요! 질문이 있으시면 문의해주세요! 🎵**

© 2024 JieLi Technology | Apache License 2.0

</div>
