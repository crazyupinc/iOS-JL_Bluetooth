# 🎯 iOS-JL_Bluetooth SDK 온보딩 가이드

환영합니다! 이 가이드는 새로운 개발자가 iOS-JL_Bluetooth SDK 프로젝트에 빠르게 적응할 수 있도록 도와줍니다.

---

## 📚 목차

1. [프로젝트 소개](#-프로젝트-소개)
2. [개발 환경 설정](#-개발-환경-설정)
3. [프로젝트 구조 이해](#-프로젝트-구조-이해)
4. [첫 실행하기](#-첫-실행하기)
5. [핵심 개념](#-핵심-개념)
6. [개발 워크플로우](#-개발-워크플로우)
7. [문제 해결](#-문제-해결)
8. [추가 학습 자료](#-추가-학습-자료)

---

## 🌟 프로젝트 소개

### 프로젝트 개요

iOS-JL_Bluetooth SDK는 **珠海市杰理科技股份有限公司(Zhuhai Jieli Technology)**에서 개발한 블루투스 음향 기기 제어 SDK입니다. 주로 블루투스 스피커, 이어폰, TWS 이어폰 등의 제어를 위한 완전한 iOS 솔루션을 제공합니다.

### 주요 기능

- 🎵 **음향 기기 제어**: 스피커, 이어폰 등 다양한 기기 지원
- 🔊 **오디오 제어**: 완전한 오디오 재생 및 제어 기능
- 🎤 **오디오 코덱**: Opus, Speex 등 전문 오디오 코덱 라이브러리
- 🖼️ **이미지 처리**: 워치페이스 이미지 변환 및 처리
- 🔄 **OTA 업그레이드**: 무선 펌웨어 업데이트 지원
- 🎧 **TWS 지원**: TWS 이어폰 일대이 기능
- 🔇 **ANC**: 액티브 노이즈 캔슬링 기능
- 📡 **Auracast**: 오디오 브로드캐스트 기능

### 기술 스택

- **언어**: Objective-C, Swift
- **최소 iOS 버전**: iOS 12.0+
- **프로토콜**: RCSP (RC Serial Port Protocol)
- **의존성 관리**: CocoaPods
- **지원 칩셋**: AC693X, AC697X, AC695X 등

---

## 🛠 개발 환경 설정

### 필수 요구사항

1. **macOS**: 최신 버전 권장
2. **Xcode**: 최신 버전 (App Store에서 설치)
3. **CocoaPods**: 의존성 관리 도구

### 설정 단계

#### 1. CocoaPods 설치

터미널에서 다음 명령어를 실행하세요:

```bash
sudo gem install cocoapods
```

#### 2. 프로젝트 클론

```bash
git clone https://github.com/[repository-url]/iOS-JL_Bluetooth.git
cd iOS-JL_Bluetooth
```

#### 3. 의존성 설치

프로젝트에는 여러 개의 하위 프로젝트가 있습니다. 각각 의존성 설치가 필요합니다:

**JieLi_Home_Demo (메인 데모 앱):**
```bash
cd code/JieLi_Home_Demo
pod install
```

**SDKTestHelper (SDK 테스트 도구):**
```bash
cd code/SDKTestHelper
pod install
```

**JLAudioUnitKitDemo (오디오 코덱 데모):**
```bash
cd code/JLAudioUnitKitDemo_V1.3.0_Beta1_20250827/code/JLAudioUnitKitDemo
pod install
```

#### 4. Xcode에서 프로젝트 열기

각 프로젝트의 `.xcworkspace` 파일을 열어야 합니다:

- `code/JieLi_Home_Demo/NewJieliZhiNeng.xcworkspace`
- `code/SDKTestHelper/SDKTestHelper.xcworkspace`
- `code/JLAudioUnitKitDemo_V1.3.0_Beta1_20250827/code/JLAudioUnitKitDemo/JLAudioUnitKitDemo.xcworkspace`

⚠️ **중요**: `.xcodeproj` 파일이 아닌 `.xcworkspace` 파일을 열어야 합니다!

---

## 📁 프로젝트 구조 이해

### 디렉토리 구조

```
iOS-JL_Bluetooth/
├── 📂 libs/                    # 핵심 SDK 프레임워크
│   ├── JL_BLEKit.xcframework  # 블루투스 연결 핵심 라이브러리
│   ├── JL_OTALib.xcframework  # OTA 업그레이드 라이브러리
│   └── ...                     # 기타 유틸리티 프레임워크
│
├── 📂 code/                    # 데모 및 테스트 애플리케이션
│   ├── JieLi_Home_Demo/       # 메인 데모 앱 (Objective-C)
│   ├── SDKTestHelper/         # SDK 테스트 도구 (Swift)
│   └── JLAudioUnitKitDemo_V1.3.0_Beta1_20250827/ # 오디오 코덱 데모
│
└── 📂 docs/                    # 문서 및 API 설명
    ├── JL_OTALib.framework API 说明.md
    └── ...
```

### 핵심 프레임워크 설명

| 프레임워크 | 기능 | 사용 시점 |
|-----------|------|----------|
| **JL_BLEKit** | BLE 연결 및 통신 핵심 | 모든 블루투스 연결 |
| **JL_OTALib** | OTA 펌웨어 업그레이드 | 기기 업데이트 필요 시 |
| **JLAudioUnitKit** | 오디오 인코딩/디코딩 | 음성 통화, 녹음 등 |
| **JLDialUnit** | 워치페이스 처리 | 스마트워치 기능 |
| **JLBmpConvertKit** | 이미지 변환 | 커스텀 이미지 전송 |
| **JL_AdvParse** | 광고 데이터 파싱 | 기기 스캔 및 식별 |

---

## 🚀 첫 실행하기

### 1. SDK 테스트 도구로 시작 (추천)

SDK 테스트 도구는 SDK의 모든 기능을 테스트할 수 있는 가장 빠른 방법입니다.

**실행 방법:**

1. Xcode에서 `code/SDKTestHelper/SDKTestHelper.xcworkspace` 열기
2. 대상을 실제 iOS 기기로 선택 (시뮬레이터는 블루투스 미지원)
3. `Product > Run` (⌘+R) 실행

**테스트 도구 기능:**

- 🔍 BLE 기기 스캔
- 📱 기기 연결/해제
- 🎵 오디오 제어 테스트
- 📡 Auracast 브로드캐스트
- 🔧 개발 로그 확인

### 2. 메인 데모 앱 실행

완전한 기능을 갖춘 참조 애플리케이션입니다.

**실행 방법:**

1. Xcode에서 `code/JieLi_Home_Demo/NewJieliZhiNeng.xcworkspace` 열기
2. 실제 iOS 기기 선택
3. 코드 서명 설정 (Team 선택)
4. 실행

### 3. 권한 설정

iOS에서 블루투스를 사용하려면 `Info.plist`에 권한 설명이 필요합니다:

```xml
<key>NSBluetoothAlwaysUsageDescription</key>
<string>블루투스 기기 연결을 위해 권한이 필요합니다</string>

<key>NSBluetoothPeripheralUsageDescription</key>
<string>블루투스 주변기기와 통신하기 위해 권한이 필요합니다</string>
```

---

## 💡 핵심 개념

### 1. RCSP 프로토콜

**RCSP (RC Serial Port Protocol)**는 Jieli의 독자적인 통신 프로토콜입니다.

- BLE 연결을 통한 양방향 통신
- 명령어 기반 제어 시스템
- 기기 상태 실시간 동기화

### 2. BLE 연결 플로우

```
┌─────────────┐
│  기기 스캔   │ JL_AdvParse로 광고 데이터 파싱
└──────┬──────┘
       │
       ▼
┌─────────────┐
│  기기 연결   │ JL_BLEKit로 BLE 연결
└──────┬──────┘
       │
       ▼
┌─────────────┐
│ RCSP 핸드셰이크│ 프로토콜 버전 확인
└──────┬──────┘
       │
       ▼
┌─────────────┐
│  기능 사용   │ 음악 제어, 설정 등
└─────────────┘
```

### 3. OTA 업그레이드

**OTA (Over-The-Air)** 업그레이드는 무선으로 펌웨어를 업데이트합니다.

**기본 플로우:**

1. 기기 기능 조회 (`cmdTargetFeature`)
2. 펌웨어 파일 준비
3. OTA 시작 (`cmdOTAData:Result:`)
4. 진행률 모니터링 (`otaUpgradeResult:Progress:`)
5. 완료 또는 재연결 처리

**주요 클래스:**

- `JL_OTAManager`: OTA 프로세스 관리
- `JLOTAFile`: 펌웨어 파일 다운로드

자세한 내용은 [JL_OTALib.framework API 설명](./docs/JL_OTALib.framework%20API%20说明.md)을 참조하세요.

### 4. 오디오 코덱

**지원 코덱:**

- **Opus**: 고품질 음성/음악 코덱
- **Speex**: 음성 특화 코덱
- **AV2**: Jieli 독자 코덱

**사용 예시:**

- 실시간 음성 통신
- 녹음 및 재생
- 카라오케 기능

---

## 🔄 개발 워크플로우

### 1. 새로운 기능 개발

```bash
# 1. 새 브랜치 생성
git checkout -b feature/your-feature-name

# 2. 코드 작성 및 테스트

# 3. 변경사항 커밋
git add .
git commit -m "feat: 기능 설명"

# 4. 푸시
git push origin feature/your-feature-name
```

### 2. SDK 통합 워크플로우

새로운 앱에 SDK를 통합할 때:

**Step 1: 프레임워크 추가**

`libs/` 디렉토리의 필요한 `.xcframework` 파일을 프로젝트에 드래그합니다.

**Step 2: 의존성 설정**

`Podfile`에 필요한 의존성 추가:

```ruby
platform :ios, '12.0'

target 'YourApp' do
  use_frameworks!

  # 필요에 따라 추가
  pod 'RxSwift'
  pod 'RxCocoa'
  pod 'SnapKit'
end
```

**Step 3: 초기화**

```swift
import JL_BLEKit

class AppDelegate: UIResponder, UIApplicationDelegate {
    func application(_ application: UIApplication,
                    didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {
        // SDK 초기화
        // 자세한 내용은 데모 앱 참조
        return true
    }
}
```

### 3. 테스트 방법

**단위 테스트:**

각 프로젝트에는 테스트 타겟이 포함되어 있습니다. `⌘+U`로 실행할 수 있습니다.

**통합 테스트:**

SDKTestHelper를 사용하여 실제 기기와 통합 테스트를 수행하세요.

**체크리스트:**

- [ ] BLE 스캔 및 연결 확인
- [ ] 기본 제어 기능 테스트
- [ ] 오류 처리 확인
- [ ] 메모리 누수 체크
- [ ] 다양한 iOS 버전 테스트

---

## 🐛 문제 해결

### 자주 발생하는 문제

#### 1. "No such module" 에러

**원인**: CocoaPods 의존성이 설치되지 않았거나 `.xcworkspace`를 열지 않음

**해결:**

```bash
cd [프로젝트 디렉토리]
pod install
```

그리고 `.xcworkspace` 파일을 열어야 합니다.

#### 2. BLE 연결 실패

**원인**:
- 실제 기기가 아닌 시뮬레이터 사용
- 블루투스 권한 미설정
- 기기가 RCSP 프로토콜 미지원

**해결:**

1. 실제 iOS 기기 사용
2. `Info.plist`에 블루투스 권한 추가
3. Jieli 칩셋이 탑재된 기기인지 확인

#### 3. 코드 서명 오류

**원인**: Apple Developer 계정 미설정

**해결:**

1. Xcode > Preferences > Accounts에서 Apple ID 추가
2. Target > Signing & Capabilities에서 Team 선택

#### 4. Framework not found 에러

**원인**: 프레임워크 경로가 올바르지 않음

**해결:**

1. Build Settings > Framework Search Paths 확인
2. 프레임워크가 올바른 위치에 있는지 확인
3. Clean Build Folder (⇧⌘K) 후 재빌드

### 디버깅 팁

**로그 활성화:**

```swift
// JLLogHelper를 사용한 디버그 로그
JLLogHelper.shared.enableLog(true)
```

**BLE 통신 모니터링:**

- Xcode의 Console에서 BLE 패킷 확인
- `JL_BLEKit`의 delegate 메서드에 breakpoint 설정

**메모리 이슈:**

- Instruments의 Leaks 도구 사용
- Allocations 프로파일링

---

## 📖 추가 학습 자료

### 공식 문서

1. **SDK 접근 문서**: [온라인 문서](https://doc.zh-jieli.com/Apps/iOS/jielihome/zh-cn/master/index.html)
2. **API 참조**: `docs/` 디렉토리의 문서들
3. **발표 기록**: `docs/杰理之家SDK(iOS)发布记录.pdf`

### 코드 예제

프로젝트 내 주요 예제:

| 예제 | 위치 | 설명 |
|-----|------|------|
| **메인 앱** | `code/JieLi_Home_Demo/` | 완전한 기능 참조 구현 |
| **SDK 테스트** | `code/SDKTestHelper/` | 각 API 테스트 예제 |
| **오디오 코덱** | `code/JLAudioUnitKitDemo_V1.3.0_Beta1_20250827/` | 오디오 처리 예제 |

### 학습 순서 추천

1. **Day 1-2**: 환경 설정 및 SDKTestHelper 실행
2. **Day 3-4**: BLE 연결 흐름 이해 (`JL_BLEKit` 학습)
3. **Day 5-7**: 메인 데모 앱 코드 분석
4. **Week 2**: OTA 업그레이드 구현 학습
5. **Week 3+**: 고급 기능 (오디오 코덱, Auracast 등)

### 유용한 리소스

- 🌐 **공식 웹사이트**: [https://www.zh-jieli.com/](https://www.zh-jieli.com/)
- 📧 **기술 지원**: 공식 채널을 통해 문의
- 🔗 **커스텀 블루투스 접근**: `docs/自定义蓝牙接入方式.url`

---

## 🤝 기여하기

프로젝트에 기여하고 싶으시다면:

1. 이슈를 먼저 확인하세요
2. 새로운 브랜치를 생성하세요
3. 코드 스타일 가이드를 따르세요
4. Pull Request를 제출하세요

---

## 📝 다음 단계

이제 기본적인 온보딩을 완료했습니다! 다음 단계로:

- [ ] SDKTestHelper로 실제 기기 연결 테스트
- [ ] 메인 데모 앱의 코드 구조 분석
- [ ] 간단한 BLE 연결 앱 직접 만들어보기
- [ ] OTA 업그레이드 기능 구현해보기

질문이 있으시면 팀원에게 문의하거나 공식 문서를 참조하세요!

---

**행복한 코딩 되세요! 🎉**

*최종 업데이트: 2025-11-09*
