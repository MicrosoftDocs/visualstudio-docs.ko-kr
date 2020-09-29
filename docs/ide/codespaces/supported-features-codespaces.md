---
title: 지원되는 Visual Studio 기능(미리 보기)
description: GitHub Codespaces를 사용할 때 제공되는 Visual Studio IDE 기능에 관해 알아봅니다.
ms.topic: how-to
ms.date: 09/21/2020
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.workload:
- multiple
monikerRange: vs-2019
ms.openlocfilehash: c86fc99fe6bd2ae17b6ce222b04549db07d7687e
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90862490"
---
# <a name="supported-visual-studio-features-preview"></a>지원되는 Visual Studio 기능(미리 보기)

Visual Studio는 codespace에 연결할 때 풍부한 개발 환경을 제공합니다. 프로젝트 템플릿, 풍부한 코드 탐색 및 IntelliSense와 같은 생산성 기능뿐만 아니라 소스 코드를 편집, 디버그, 테스트 및 버전 관리하기 위해 잘 알고 있는 Visual Studio 내부 루프 도구를 사용할 수 있습니다.

현재 GitHub Codespaces [퍼블릭 베타](https://github.com/features/codespaces)에서 일부 Visual Studio 기능은 완전히 지원되지 않거나 처음에 없을 수 있습니다. 다음 섹션에서는 Visual Studio 및 GitHub Codespaces 베타에서 기대할 수 있는 항목과 나중에 기대할 수 있는 항목을 간략하게 설명합니다. 

이는 **완전한 목록이 아니라** codespace에 연결될 때 Visual Studio의 일반 기능을 설명하는 것입니다.

> [!NOTE]
> Visual Studio에서 codespace를 사용하는 동안 누락된 기능이 있는 경우 https://developercommunity.visualstudio.com/ 에서 이슈를 열어서 알려 주세요. 이를 통해 Microsoft에서는 가장 필요한 기능의 우선 순위를 지정할 수 있습니다.

> [!NOTE]
> 아래 설명된 기능은 Visual Studio에 해당하며 다른 두 GitHub Codespaces 클라이언트인 Visual Studio Code 및 브라우저 내 편집기와는 관련이 없습니다.

## <a name="edit-and-navigation"></a>편집 및 탐색

IntelliSense, 코드 탐색, 진단 및 제안과 같은 스마트 언어 기능을 사용할 수 있으므로 codespace에서 소스 코드를 편집하는 과정이 약간 다를 수 있습니다.

* IntelliSense*
* 코드 탐색*
* 문서 서식을 사용한 코드 서식 지정
* 구문 강조
* 요약 정보*
* HTML, CSS, Razor 편집기* - 부분적으로 지원됩니다.
* JavaScript 편집기* - 부분적으로 지원됩니다.

아직 사용할 수 없음:

* IntelliSense* - 자동 완성/멤버 목록 필터 중 일부를 사용할 수 없습니다. 조사식 창에서 가져오지 않은 형식 및 IntelliSense의 완성은 아직 사용할 수 없습니다.
* 코드 탐색* - 대부분의 명령은 지원되지만, 구체적으로 경로 지정을 사용하는 파일에서 찾기 및 기본으로 이동은 아직 지원되지 않습니다.
* 요약 정보* - 요약 정보에서 색 지정은 지원되지 않습니다.
* HTML, CSS, Razor 편집기* - 진단, IntelliSense 완성, 요약 정보, 스마트 들여쓰기. 현재 의미 체계 색 지정, 탐색 명령 등은 지원되지 않습니다.
* JavaScript 편집기* - 스크립트 블록(예: HTML 및 CSHTML 파일의 JavaScript 콘텐츠) 및 의미 체계 강조 표시는 아직 지원되지 않습니다. 전구 기능 및 린팅의 알려진 문제입니다.
* CMake 대상 뷰
* CMake 프로젝트 설정 편집기
* Ctrl+F7(파일 컴파일)
* CodeLens
* 코드 조각
* IntelliCode

## <a name="application-types-and-configuration"></a>애플리케이션 형식 및 구성

대부분의 애플리케이션 형식 및 프로젝트 구성은 지원되지만 비주얼 디자이너를 사용하지 않는 경우에는 프로젝트 코드를 직접 편집해야 합니다. 자세한 구성 지침은 [codespace를 사용자 지정하는 방법](customize-codespaces.md)을 참조하세요.

* 프로젝트 및 항목 템플릿
* .NET Core 및 ASP.NET Core 프로젝트
* C++ 콘솔 앱 - CMake 및 vcxproj가 지원됩니다.
* Linux를 대상으로 하는 C++ 앱 - GUI 이외 항목에서 대부분 지원됩니다. WSL, 플랫폼별 IntelliSense 및 빌드를 설치하고 프로비저닝하는 기능
* 프로젝트 파일 편집 - 대부분 지원됩니다. 일부 완성, 구문 강조 및 고급 편집 기능이 없습니다.
* GitHub 계정 - Codespaces를 만들고 연결하며 GitHub의 계정에 제공되는 리소스에 액세스하는 데 사용할 수 있습니다.
* Azure CLI - 로그인한 Visual Studio ID 또는 키 집합 계정을 공유하지 않습니다. 브라우저 기반 로그인은 지원되지 않지만 `az login --use-device-code`를 사용하여 통합 터미널 내에서 인증할 수 있습니다.

아직 사용할 수 없음:

* UI 디자이너 - WinForms 및 WPF 디자이너
* Visual Basic 및 F# 프로젝트
* .NET Framework 대상 프로젝트
* Docker Compose 프로젝트
* 프로젝트 속성 페이지
* ASP.NET Core 템플릿의 인증 옵션
* 설치하는 데 GUI가 필요한 앱 - 터미널을 통해 설치할 수 있는 모든 앱이 지원되지만(chocolatey 설치 관리자 포함) 실제 GUI는 즉시 사용할 수 없습니다. 현재 해결 방법은 전체 화면 Live Share가 GUI에 액세스할 수 있도록 설정하는 것입니다. 관리 콘솔에 액세스할 수 없습니다. 설치하려면 다시 부팅해야 하는 앱은 지원되지 않습니다.
* Visual Studio의 Azure 리소스에 대한 관리 ID
* 인트라넷 리소스(프라이빗 네트워크) - 현재는 codespace가 VPN이 필요한 리소스에 연결할 수 없습니다.
* 확장 - Visual Studio에서 Codespaces를 사용하는 경우 확장이 지원되지 않습니다.

## <a name="debugging"></a>디버깅

중단점 설정, 기본적인 한 단계씩 코드 실행, 변수 검사 및 로컬, 자동 및 조사식 창을 포함한 필수 내부 루프 디버깅이 지원됩니다. 일부 추가 창, 사용자 지정 및 시각화 도우미는 지원되지 않습니다.

* 중단점*
* 기본적인 한 단계 실행
* 로컬, 자동, 조사식 창* - 부분적으로 지원됩니다.
* 기호 서버, 소스 서버 및 데이터 가져오기/내보내기 팁이 모두 부분적으로 지원됩니다.

아직 사용할 수 없음:

* 중단점* - 중단점 레이블, 데이터 중단점 및 디스어셈블리 창에서 중단점 설정이 진행 중입니다. 중단점 가져오기 및 내보내기는 부분적으로 지원됩니다.
* 로컬, 자동, 조사식 창* - 검색 상자의 문 완성 및 검색 상자 탐색과 같은 일부 기능
* UI 사용자 지정 - 고정 가능한 속성 및 템플릿 매개 변수 숨기기는 지원되지 않습니다.
* 시각화 도우미 - C++ natvis에서 부분적으로 지원됩니다. 디스어셈블리 창, XAML 시각적 진단, 사용자 지정 .NET 시각화 도우미 및 데이터 세트 시각화 도우미는 지원되지 않습니다.
* 추가 디버거 창 - 프로세스 창이 부분적으로 지원됩니다. 병렬 스택 창 - 작업 보기, 진단 허브 및 소스/기호 찾기 대화 상자는 지원되지 않습니다.
* 일부 디버거 워크플로 - 프로세스에 연결, JIT(Just-In-Time) 디버거, 덤프 디버깅, 프로파일링 및 IntelliTrace는 지원되지 않습니다. C++ 내 코드만 한 단계 실행은 부분적으로 지원됩니다.
* 편집하며 계속하기 - 관리 코드와 네이티브 코드에서 둘 다 지원되지 않습니다.
* 스레딩 기능 - 스레드 동결/재개, 스레드 이름 바꾸기 및 소스에 스레드 표시는 지원되지 않습니다.
* 추가적인 한 단계 실행 기능 - 속성 및 연산자 자동 건너뛰기(.NET Core) 및 한 단계씩 특정 코드 실행은 지원되지 않습니다. 

## <a name="features"></a>기능

codespace에 연결된 Visual Studio를 사용하는 경우 로컬로 작업할 때와 동일한 접근성 기능을 사용할 수 있습니다.

* 소스 제어 - 새 [Git 창](https://devblogs.microsoft.com/visualstudio/improved-git-experience-in-visual-studio-2019/)을 통해 전체 Git을 지원합니다.
* 접근성 - 디버그된 앱의 appcasting에 액세스할 수 없는 보조 기술의 한 가지 알려진 문제가 있습니다. 해당 제한 사항 외에 로컬 Visual Studio 환경에 아직 존재하지 않는 다른 호환성 문제가 있다고 생각하지 않습니다. 버그를 발견하면 [Developer Community](https://developercommunity.visualstudio.com/)에서 이슈를 제출하여 알려 주세요.
* 게시 - GitHub Actions를 통한 Azure로의 게시는 지원됩니다.
* 연결된 서비스 - App Insights, KeyVault, Storage, SQL, Redis, Cosmos, openAPI 및 gRPC는 부분적으로 지원됩니다.
* 테스트 탐색기* - 대부분 지원됩니다.

아직 사용할 수 없음:

* 테스트 탐색기* - 기본 아키텍처 선택, 병렬 테스트 실행, 재생 목록 등의 몇 가지 기능. 단위 테스트 디버깅, 실행 설정 및 일부 추가적인 엔터프라이즈 기능에 관한 알려진 문제. 단위 테스트 프로파일링은 지원되지 않습니다.
* NuGet 패키지 관리자 UI - NuGet 명령줄은 지원됩니다.
* 엔터프라이즈 테스트 기능 - Live Unit Testing, Microsoft Fakes, 코드 검사 및 IntelliTest는 지원되지 않습니다.
* 고급 게시 시나리오 - 선택적 게시, FTP 게시, 변경 내용 미리 보기, 빠른 게시 도구 모음 등

## <a name="see-also"></a>추가 정보

* [GitHub Codespaces란?](codespaces-overview.md)
* [codespace와 함께 Visual Studio를 사용하는 방법](use-visual-studio-with-codespaces.md)
* [codespace를 사용자 지정하는 방법](customize-codespaces.md)
