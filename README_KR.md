# iOS-JL_Bluetooth

> 📖 **언어 / Language / 语言版本**: [한국어](./README_KR.md) | [English](./README_EN.md) | [中文](./README.md)

<div align="center">

![iOS](https://img.shields.io/badge/iOS-12.0+-blue.svg)
![Xcode](https://img.shields.io/badge/Xcode-Latest-orange.svg)
![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)

**JieLi 블루투스 스피커 iOS SDK**

*전문 블루투스 스피커 및 헤드폰 제어 개발 플랫폼*

</div>

---

## 📖 개요

JieLi 블루투스 스피커 SDK는 **주하이 JieLi 테크놀로지 주식회사**에서 개발한 전문 블루투스 제어 개발 플랫폼으로, JieLi 스피커 및 헤드폰 제품을 위한 완전한 iOS 측 제어 솔루션을 제공합니다.

### ✨ 주요 특징

- 🎵 스피커, 헤드폰 등 다양한 기기 유형 지원
- 🔊 완전한 오디오 제어 기능
- 🎤 전문 오디오 코덱 라이브러리 (Opus, Speex)
- 🖼️ 이미지 변환 및 시계 문자판 처리 기능
- 📱 네이티브 iOS 개발 경험
- 🔗 RCSP 프로토콜 기반의 안정적인 연결
- 🎧 TWS 이어폰 일대이 기능 지원
- 🔇 ANC 액티브 노이즈 캔슬링 지원
- 🧪 개발 디버깅을 위한 SDK 테스트 헬퍼 도구 제공
- 📡 Auracast 오디오 브로드캐스트 기능 지원

---

## 🛠 실행 환경

| 카테고리 | 요구사항 | 설명 |
|---------|---------|------|
| **iOS 시스템** | iOS 12.0+ | BLE 기능 지원 |
| **하드웨어 요구사항** | RCSP 프로토콜 지원 펌웨어 | AC693X, AC697X, AC695X 등 SDK |
| **개발 플랫폼** | Xcode | 최신 버전 권장 |
| **언어 지원** | Objective-C / Swift | 완전한 API 지원 |

---

## 🚀 빠른 시작

### 📚 문서 리소스

JieLi Home SDK를 빠르게 통합할 수 있도록 개발 전에 다음을 자세히 읽어주세요:

- 🎓 **[온보딩 가이드](./ONBOARDING_KR.md)** - 완전한 초보자 튜토리얼 (먼저 읽기를 권장합니다!)
- 📖 [SDK 통합 문서](https://doc.zh-jieli.com/Apps/iOS/jielihome/zh-cn/master/index.html)
- 📄 [개발 문서](./docs/)
- 🔧 [API 참조 매뉴얼](./docs/JieLiBluetoothControlSDKDevelopmentInstructions(iOS)/)

### 💻 통합 단계

1. **SDK 다운로드** - 이 저장소에서 최신 버전 가져오기
2. **프레임워크 가져오기** - libs 디렉토리의 프레임워크를 프로젝트에 추가
3. **권한 구성** - 블루투스 관련 권한 추가
4. **SDK 초기화** - 초기화를 위한 예제 코드 참조
5. **개발 시작** - 기능 개발을 위한 API 사용

### 🧪 SDK 테스트 헬퍼 도구

**SDKTestHelper**는 개발자를 위해 특별히 설계된 Swift 테스트 도구로 다음 기능을 제공합니다:

- 🔍 **SDK 기능 테스트** - 완전한 SDK API 테스트 인터페이스
- 📱 **기기 연결 디버깅** - 블루투스 기기 스캔, 연결 및 연결 해제 테스트
- 🎵 **오디오 기능 검증** - 오디오 코덱 및 재생 제어 테스트
- 📡 **Auracast 브로드캐스팅** - 오디오 브로드캐스트 기능 테스트 및 디버깅
- 🔧 **개발 지원** - 로그 보기, 데이터 분석, 문제 진단
- 📊 **성능 모니터링** - 연결 상태 및 오디오 품질 실시간 모니터링

**사용 방법:**
1. `code/SDKTestHelper/SDKTestHelper.xcworkspace` 열기
2. iOS 기기에서 프로젝트 실행
3. 다양한 테스트 기능을 사용하여 SDK 통합 효과 확인

---

## 📁 프로젝트 구조

```
iOS-JL_Bluetooth/
├── 📂 code/                          # 데모 프로그램 소스 코드
│   ├── 📦 Example of audio encoding and decoding V1.1.0.zip
│   ├── 📂 JLAudioUnitKitDemo_V1.3.0_Beta1_20250827/ # 오디오 코덱 데모 프로젝트 (최신 버전)
│   │   ├── 📂 code/JLAudioUnitKitDemo/
│   │   │   ├── 🏗️ JLAudioUnitKitDemo.xcworkspace
│   │   │   ├── 📱 JLAudioUnitKitDemo/    # Swift 데모 애플리케이션
│   │   │   ├── 🎵 JLAudioUnitKit.xcframework # 오디오 처리 프레임워크
│   │   │   ├── 📝 JLLogHelper.xcframework # 로그 헬퍼 프레임워크
│   │   │   └── 🔧 Pods/                  # 의존성
│   │   ├── 📂 docs/                      # 개발 문서
│   │   ├── 📂 libs/                      # 프레임워크 라이브러리
│   │   └── 📄 readme.md                  # 프로젝트 설명
│   └── 📂 JieLi_Home_Demo/           # JieLi Home 메인 애플리케이션 데모
│       ├── 🏗️ NewJieliZhiNeng.xcworkspace # 메인 워크스페이스
│       ├── 📱 NewJieliZhiNeng/       # iOS 애플리케이션 소스 코드
│       │   ├── 🎯 앱 설정/            # 앱 설정 모듈
│       │   ├── 🌐 Http 인터페이스/   # 네트워크 인터페이스
│       │   ├── 🎵 멀티미디어/        # 멀티미디어 기능
│       │   ├── 🎤 노래방/            # 노래방 기능
│       │   ├── 📱 기기/              # 기기 관리
│       │   └── 🎛️ 오디오 효과/       # 오디오 효과
│       ├── 🔧 Frameworks/            # 내장 프레임워크 라이브러리
│       ├── 📚 Sources/               # 리소스 파일
│       ├── 🌍 Languages/             # 다국어 지원
│       └── 🔧 Pods/                  # CocoaPods 의존성
│   └── 📂 SDKTestHelper/             # SDK 테스트 헬퍼 도구 (Swift 프로젝트)
│       ├── 🏗️ SDKTestHelper.xcworkspace # 테스트 도구 워크스페이스
│       ├── 📱 SDKTestHelper/         # Swift 테스트 애플리케이션 소스 코드
│       │   ├── 🎯 Controllers/       # 컨트롤러 모듈
│       │   ├── 🔧 Tools/             # 유틸리티 클래스
│       │   ├── 📊 Models/            # 데이터 모델
│       │   ├── 🎨 Views/             # 뷰 컴포넌트
│       │   ├── 🔗 Bluetooth/         # 블루투스 연결 모듈
│       │   └── 💾 DataBase/          # 데이터베이스 관리
│       ├── 🎵 JLAudioUnitKit.framework # 오디오 코덱 프레임워크
│       ├── 🎬 JLAV2Lib.framework    # AV2 오디오 코덱 라이브러리
│       ├── 📡 JLAuracastKit.xcframework # Auracast 브로드캐스트 프레임워크
│       ├── 🔧 SpeexKit.framework    # Speex 음성 코덱
│       └── 🔧 Pods/                  # 타사 의존성
├── 📂 docs/                          # 문서 리소스
│   ├── 📖 JL_OTALib.framework API 문서.md
│   ├── 📄 html/                      # HTML 형식 문서
│   │   ├── 🏠 index.html             # 문서 홈페이지
│   │   ├── 📁 Development/           # 개발 가이드
│   │   ├── 📁 Framework/             # 프레임워크 문서
│   │   └── 📁 Other/                 # 기타 문서
│   ├── 📋 JieLi Home SDK(iOS) 릴리스 기록.pdf
│   ├── 📄 JieLi 오픈 플랫폼 통합 가이드_V1.0.3.pdf
│   └── 📦 기기 사양 문서/            # 기기 사용 사양
└── 📂 libs/                          # 핵심 SDK 라이브러리 (XCFramework 형식)
    ├── 🔗 JL_BLEKit.xcframework      # 블루투스 연결 핵심 라이브러리
    ├── 🔧 JL_OTALib.xcframework      # OTA 업그레이드 라이브러리
    ├── 🎵 JLDialUnit.xcframework     # 시계 문자판 처리 라이브러리
    ├── 🖼️ JLBmpConvertKit.xcframework # 이미지 변환 라이브러리
    ├── 📝 JLLogHelper.xcframework    # 로그 헬퍼 라이브러리
    ├── 📦 JLPackageResKit.xcframework # 리소스 패키지 처리 라이브러리
    ├── 🔍 JL_AdvParse.xcframework    # 광고 파싱 라이브러리
    └── 🔐 JL_HashPair.xcframework    # 해시 페어링 라이브러리
```

---

## 📋 버전 히스토리

| 버전 | 릴리스 날짜 | 편집자 | 주요 업데이트 |
|------|------------|--------|--------------|
| **v1.13.0** | 2025/07/18 | EzioChen | • 컬러 스크린 케이스 기능 지원 추가<br/>• 화면 밝기 제어 추가<br/>• 화면 보호기 프로그램 제어 추가<br/>• 날씨 정보 동기화 추가 |
| **v1.12.0** | 2024/11/22 | EzioChen | • AC707N 호환 커스텀 시계 문자판 이미지 변환 추가<br/>• 이미지 변환 도구를 독립 모듈 라이브러리로 분리 |
| **v1.11.0** | 2024/03/15 | EzioChen | • 시계 문자판 확장 매개변수 추가 및 AI 시계 문자판 프로세스 보완<br/>• 4G 모듈 OTA 기능 추가<br/>• 알려진 문제 수정 |
| **v1.10.0** | 2023/11/23 | EzioChen | • TWS 이어폰 일대이 기능 및 인터페이스 추가<br/>• 칩 JL701N v1.0.0_patch_06 지원<br/>• 알려진 문제 수정 |
| **v1.6.4** | 2022/08/12 | EzioChen | • 보청 이어폰 피팅 기능 추가 |
| **v1.6.3** | 2022/07/20 | EzioChen | • 넥밴드 이어폰 UI 지원 추가 |
| **v1.5.0** | 2021/08/12 | 冯洪鹏 | • 스피커 SDK 알람 시계 스누즈 모드 추가<br/>• 벨소리 지속 시간 및 재울림 간격 설정 지원<br/>• 이어폰 SDK ANC 액티브 노이즈 캔슬링 추가<br/>• 노이즈 감소 및 투명 모드 전환 지원 |

---

## 📞 기술 지원

- 🌐 **공식 웹사이트**: [JieLi Technology](https://www.zh-jieli.com/)
- 📧 **기술 지원**: 공식 채널을 통해 문의해 주세요
- 📖 **온라인 문서**: [SDK 개발 문서](https://doc.zh-jieli.com/)
- 🔗 **커스텀 통합**: [블루투스 통합 방법](./docs/自定义蓝牙接入方式.url)

---

## 📄 라이선스

이 프로젝트는 [Apache License 2.0](./LICENSE)에 따라 라이선스가 부여됩니다.

```
Copyright 2024 珠海市杰理科技股份有限公司

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
```

---

<div align="center">

**© 2024 珠海市杰理科技股份有限公司 | Licensed under Apache License 2.0**

</div>
