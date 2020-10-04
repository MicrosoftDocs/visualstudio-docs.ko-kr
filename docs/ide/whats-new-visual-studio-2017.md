---
title: Visual Studio 2017의 새로운 기능
titleSuffix: ''
description: Visual Studio 2017의 새로운 기능을 알아보세요.
ms.date: 12/18/2018
f1_keywords:
- VS.StartPage.WhatsNew
helpviewer_keywords:
- Visual Studio, what's new
- what's new [Visual Studio]
ms.assetid: 7307e180-ba28-4774-8a43-cbb980085a71
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: conceptual
ms.workload:
- multiple
monikerRange: vs-2017
ms.openlocfilehash: db777df991b48d1b6e26d40426d32c07a495efb1
ms.sourcegitcommit: 13cf7569f62c746708a6ced1187d8173eda7397c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/25/2020
ms.locfileid: "91352179"
---
# <a name="whats-new-in-visual-studio-2017"></a>Visual Studio 2017의 새로운 기능

**15.9 릴리스[용으로 업데이트됨](/visualstudio/releasenotes/vs2017-relnotes?context=visualstudio/default&contextView=vs-2017)**

Visual Studio의 이전 버전에서 업그레이드하려고 하십니까? Visual Studio 2017에서 제공할 수 있는 기능은 다음과 같습니다. 모든 개발, 앱 및 플랫폼에서 뛰어난 생산성을 제공합니다. Visual Studio 2017를 사용하여 Android, iOS, Windows, Linux, 웹 및 클라우드용 앱을 개발합니다. 빠르게 코딩하고, 간단하게 디버그 및 진단하고, 자주 테스트하며, 안심하고 릴리스하세요. 개발자 고유의 확장을 빌드하여 Visual Studio를 확장하고 사용자 지정할 수도 있습니다. 이 릴리스로 버전 제어를 사용하고, 민첩하게 대처하고, 효율적으로 공동 작업하세요.

>[!div class="button"]
>[Visual Studio 다운로드](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)

이전 버전 Visual Studio 2015부터 적용해 온 변경을 높은 수준에서 요약한 사항입니다.

* **[재정의된 기본 사항](#redefined-fundamentals)** . 새로운 설치 환경을 통해 더 빠르게 설치하고, 필요할 때 원하는 항목을 설치할 수 있습니다.
* **[성능 및 생산성](#performance-and-productivity)** . 새로운 최신 모바일, 클라우드 및 데스크톱 개발 기능에 집중했습니다. 또한 Visual Studio는 더 빨리 시작하고, 더 빨리 응답하며, 이전보다 적은 메모리를 사용합니다.
* **[Azure로 클라우드 앱 개발](#cloud-app-development-with-azure)** . 기본 제공 Azure 도구 모음을 통해 Microsoft Azure 기반의 클라우드 중심 앱을 쉽게 만들 수 있습니다. Visual Studio를 사용하면 Azure에서 직접 앱과 서비스를 쉽게 구성, 빌드, 디버그, 패키징 및 배포할 수 있습니다.
* **[Windows 앱 개발](#windows-app-development)** . Visual Studio 2017의 UWP 템플릿을 사용하여 모든 Windows 10 디바이스 &ndash; PC, 태블릿, 전화, Xbox, HoloLens, Surface Hub 등에 대한 단일 프로젝트를 만듭니다.
* **[모바일 앱 개발](#mobile-app-development)** . 하나의 핵심 코드베이스와 기술 집합으로 다중 플랫폼 모바일 요구 사항을 통합하는 Xamarin에서 혁신적인 결과를 빠르게 얻습니다.
* **[플랫폼 간 개발](#cross-platform-development)** . 모든 대상 플랫폼에 소프트웨어를 원활하게 제공할 수 있습니다. Redgate 데이터 도구를 통해 DevOps 프로세스를 SQL Server로 확장하고 Visual Studio에서 데이터베이스 배포를 안전하게 자동화할 수 있습니다. 또는 .NET Core를 사용하여 Windows, Linux 및 macOS 운영 체제에서 수정되지 않고 실행되는 앱 및 라이브러리를 작성할 수 있습니다.
* **[게임 개발](#games-development)** . VSTU(Visual Studio Tools for Unity)를 사용하면 Visual Studio를 통해 게임 및 편집기 스크립트를 C#으로 작성한 다음 강력한 디버거를 사용하여 오류를 찾고 수정할 수 있습니다.
* **[AI 개발](#ai-development)** . Visual Studio Tools for AI를 통해 Visual Studio의 생산성 기능을 사용하여 AI 혁신을 가속화할 수 있습니다. Azure Machine Learning과 원활하게 통합되는 딥 러닝/AI 솔루션을 빌드, 테스트 및 배포하여 강력한 실험 기능을 제공할 수 있습니다.

> [!NOTE]
> Visual Studio 2017의 새로운 기능에 대한 전체 목록은 [현재 릴리스 정보](/visualstudio/releasenotes/vs2017-relnotes?context=visualstudio/default&contextView=vs-2017)를 참조하세요. 향후 제공할 기능을 살펴보려면 [미리 보기 릴리스 정보](/visualstudio/releasenotes/vs2017-preview-relnotes?context=visualstudio/default&contextView=vs-2017)를 참조하세요.

Visual Studio 2017에서 가장 두드러진 개선 사항과 새로운 기능에 대한 자세한 내용은 다음과 같습니다.

## <a name="redefined-fundamentals"></a>재정의된 기본 사항

### <a name="a-new-setup-experience"></a>새로운 설치 환경

Visual Studio를 사용하면 필요할 때 필요한 기능만 쉽고 빠르게 설치할 수 있습니다. 또한 완전히 제거됩니다.

가장 중요한 변화는 Visual Studio를 설치할 때 확인할 수 있는 새로운 설치 환경입니다. **작업** 탭에는 일반 프레임워크, 언어 및 플랫폼을 나타내도록 그룹화된 설치 옵션이 표시됩니다. .NET 데스크톱 개발에서 Windows, Linux 및 iOS의 C++ 애플리케이션 개발에 이르기까지 모든 작업을 포함합니다.

필요한 작업을 선택하고, 필요할 때 변경합니다.

![Visual Studio 2017 설정 대화 상자](../install/media/install-visual-studio-enterprise.png)

또한 설치를 상세 조정하는 옵션도 있습니다.

* 작업을 사용하는 대신 사용자 고유의 구성 요소를 선택하고 싶으세요? 설치 관리자에서 **개별 구성 요소** 탭을 선택합니다.
* 또한 Windows 언어 옵션을 변경하지 않고도 언어 팩을 설치하고 싶으세요? 설치 관리자의 **언어 팩** 탭을 선택합니다.
* **15.7의 새로운 기능**: Visual Studio를 설치한 위치를 변경하려는 경우 선택 관리자의 **설치 옵션** 탭을 선택합니다.

단계별 지침을 포함하여 새로운 설치 환경에 대한 자세한 내용은 [Visual Studio 설치](../install/install-visual-studio.md) 페이지를 참조하세요.

### <a name="a-focus-on-accessibility"></a>액세스 가능성에 집중

**15.3의 새로운 기능**: Visual Studio와 고객들이 많이 사용하는 보조 기술 간의 호환성을 개선하기 위해 1,700가지가 넘는 대상 수정 사항을 적용했습니다. 화면 판독기, 고대비 테마 및 기타 보조 기술과 이전보다 더 높은 호환성을 제공하는 수십 가지 시나리오가 있습니다. 디버거, 편집기 및 셸 역시 모두 크게 향상되었습니다.

자세한 내용은 [Accessibility improvements in Visual Studio 2017 version 15.3(Visual Studio 2017 버전 15.3의 접근성 향상)](https://devblogs.microsoft.com/visualstudio/accessibility-improvements-in-visual-studio-2017-version-15-3/) 블로그 게시물을 참조하세요.

## <a name="performance-and-productivity"></a>성능 및 생산성

### <a name="sign-in-across-multiple-accounts"></a>여러 계정에 로그인

팀 탐색기, Azure 도구, Microsoft 스토어 게시 등에서 사용자 계정을 공유할 수 있는 새로운 ID 서비스를 Visual Studio에 도입했습니다.

더 오랫동안 로그인 상태를 유지할 수도 있습니다. Visual Studio에서 12시간마다 다시 로그인하라는 메시지가 표시하되 않습니다. 자세한 내용은 [Fewer Visual Studio Sign-in Prompts](https://devblogs.microsoft.com/visualstudio/fewer-visual-studio-sign-in-prompts/)(Visual Studio 로그인 프롬프트 횟수 감소) 블로그 게시물을 참조하세요.

### <a name="start-visual-studio-faster"></a>더 빨리 Visual Studio 시작

새로운 Visual Studio 성능 센터는 IDE 시작 시간을 최적화하는 데 유용합니다. 성능 센터에는 IDE 시작을 늦출 수 있는 모든 확장 및 도구 창이 나열됩니다. 성능 센터를 사용하여 확장 시작 시간 또는 시작 시 도구 창을 열지 여부를 결정하여 시작 성능을 개선할 수 있습니다.

### <a name="faster-on-demand-loading-of-extensions"></a>요청 시 더 빠르게 확장 로드

Visual Studio는 IDE 시작이 아닌 요청 시에 로드되도록 확장을 전환하고 있습니다(타사 확장과도 작업). 어떤 확장이 시작, 솔루션 로드 및 입력 성능에 영향을 주는지 궁금하세요? 이 정보는 **도움말** > **Visual Studio 성능 관리**에서 확인할 수 있습니다.

  ![옵션 대화 상자(Visual Studio 2017)](media/vs2017ide-manage-vs-perf.png)

#### <a name="manage-your-extensions-with-roaming-extensions-manager"></a>로밍 중인 확장 관리자를 사용하여 확장 관리

Visual Studio에 로그인할 때 즐겨찾는 확장으로 각 개발 환경을 더 쉽게 설정할 수 있습니다. 새로운 [로밍 중인 확장 관리자]는 클라우드에 동기화된 목록을 만들어 즐겨찾는 확장을 모두 추적합니다.

Visual Studio의 확장 목록을 보려면 **도구** > **확장 및 업데이트**를 클릭한 다음, **로밍 중인 확장 관리자**를 클릭합니다.

![Visual Studio 2017 - 확장 및 업데이트 대화 상자](media/vs2017ide-extensions-and-updates.png)

로밍 중인 확장 관리자는 설치하는 모든 확장을 추적하지만 로밍 목록에 추가할 확장을 선택할 수 있습니다.

![Visual Studio 2017 - 로밍 확장 관리자](media/vs2017ide-RoamingExtensionManager.png)

로밍 중인 확장 관리자를 사용하는 경우 3개의 아이콘 형식이 목록에 표시됩니다.

* ![로밍 아이콘](media/vs2017ide-roamedicon.png) **_로밍_**: 이 로밍 목록에 포함되어 있지만, 머신에 설치되지 않은 확장입니다.
  **다운로드** 단추를 사용하여 이러한 확장을 설치할 수 있습니다.
* ![로밍 및 설치 아이콘](media/vs2017ide-roamedinstalledicon.png) **_로밍 및 설치 아이콘_**: 로밍 목록에 포함되어 있고 개발 환경에 설치된 모든 확장입니다.
  로밍하지 않도록 결정하는 경우 **로밍 중지** 단추를 사용하여 이러한 확장을 제거할 수 있습니다.
* ![설치 아이콘](media/vs2017ide-installedicon.png) **_설치_**: 이 환경에 설치되어 있지만 로밍 목록에 포함되지 않은 모든 확장입니다.
  **로밍 시작** 단추를 사용하여 로밍 목록에 확장을 추가할 수 있습니다.

로그인되어 있는 동안 다운로드한 모든 확장은 목록에 **로밍 및 설치**로 추가됩니다. 그런 다음, 확장이 로밍 목록에 포함되고, 모든 컴퓨터에서 액세스할 수 있습니다.

### <a name="experience-live-unit-testing"></a>Live Unit Testing 환경

Visual Studio Enterprise 2017에서 라이브 유닛 테스트는 코딩하는 동안 편집기에 라이브 단위 테스트 결과와 코드 검사를 제공합니다. .NET Framework 및 .NET Core용 C# 및 Visual Basic 프로젝트에서 작동하고, MSTest, xUnit, NUnit의 세 가지 테스트 프레임워크를 지원합니다.

![Live Unit Testing](media/lut-codewindow.png)

자세한 내용은 [Live Unit Testing 소개](../test/live-unit-testing-intro.md)를 참조하세요. Visual Studio Enterprise 2017의 각 릴리스에 추가된 새로운 기능 목록은 [Live Unit Testing의 새로운 기능](../test/live-unit-testing-whats-new.md)을 참조하세요.

### <a name="set-up-a-cicd-pipeline"></a>CI/CD 파이프라인 설정

#### <a name="automated-testing"></a>자동화된 테스트

자동화된 테스트는 DevOps 파이프라인의 핵심 부분입니다. 자동화된 테스트를 통해 솔루션을 일관되고 안정적으로 테스트하고 더 짧은 주기로 릴리스할 수 있습니다. CI/CD(연속 통합 및 지속적인 업데이트) 흐름은 이 프로세스의 효율성을 더 높일 수 있습니다.

자동화된 테스트에 대한 자세한 내용은 [CI/CD pipeline for automated tests in DevOps(DevOps에서 자동화된 테스트에 대한 CI/CD 파이프라인)](/archive/blogs/visualstudioalmrangers/set-up-a-cicd-pipeline-to-run-automated-tests-efficiently) 블로그 게시물을 참조하세요.

또한 [Visual Studio의 지속적인 업데이트 도구](https://marketplace.visualstudio.com/items?itemName=VSIDEDevOpsMSFT.ContinuousDeliveryToolsforVisualStudio) DevLabs 확장의 새로운 기능에 대한 자세한 내용은 [정확하게 커밋: 커밋 타임 코드 품질](https://devblogs.microsoft.com/visualstudio/committing-with-confidence-getting-code-quality-information-at-commit-time/) 블로그 게시물을 참조하세요.

### <a name="visual-studio-ide-enhancements"></a>Visual Studio IDE 향상

#### <a name="multi-caret-editing"></a>다중 캐럿 편집

**15.8의 새로운 기능**: 이제 동시에 파일의 여러 위치를 쉽게 편집할 수 있습니다. 파일의 여러 위치에서 삽입 지점 및 선택 영역을 만들어 시작합니다. 그런 다음, 다중 캐럿 편집 기능을 사용하여 동시에 둘 이상의 위치에서 동일하게 편집합니다.

자세한 내용은 [텍스트 찾기 및 바꾸기](finding-and-replacing-text.md) 페이지의 [다중 캐럿 선택 영역](finding-and-replacing-text.md#multi-caret-selection) 섹션을 참조하세요.

#### <a name="keep-keybinding-profiles-consistent"></a>키 바인딩 프로필을 일관되게 유지

**15.8의 새로운 기능**: 이제 새로운 두 키보드 프로필을 포함한 도구에서 키 바인딩을 일관적으로 유지할 수 있습니다. Visual Studio Code 및 ReSharper(Visual Studio). 이러한 스키마는 **도구** > **옵션** > **일반** > **키보드** 및 위쪽 드롭다운 메뉴에서 찾을 수 있습니다.

  ![Visual Studio Code 및 ReSharper에 대한 새 키 바인딩 프로필](media/vs-keyboard-mappings-code-resharper.png)

#### <a name="use-new-refactorings"></a>새 리팩터링 사용

리팩터링은 코드를 작성한 후에 개선하는 프로세스입니다. 리팩터링은 코드의 동작을 변경하지 않고 코드의 내부 구조를 변경합니다. 새로운 리펙터링은 자주 추가되며, 다음은 몇 가지 예입니다.

* 매개 변수 추가(호출 사이트에서)
* 재정의 생성
* 명명된 인수 추가
* 매개 변수에 대한 null 검사 추가
* 자릿수 구분 기호를 리터럴로 삽입
* 숫자 리터럴에 대한 기본 변경(예: 16진수에서 2진수로)
* if-to-switch 변환
* 사용하지 않는 변수 제거

자세한 내용은 [빠른 작업](common-quick-actions.md)을 참조하세요.

#### <a name="interact-with-git"></a>Git과 상호 작용

Visual Studio에서 프로젝트를 작업할 때 코드를 설정하고 빠르게 커밋하여 Git 서비스에 게시할 수 있습니다. 또한 IDE의 오른쪽 아래 모서리에 있는 단추의 메뉴 클릭을 사용하여 Git 리포지토리를 관리할 수도 있습니다.

![Git 대화 상자와 상호 작용하는 Visual Studio 2017](media/vsIDE-GitInteraction.png)

#### <a name="experience-improved-navigation-controls"></a>향상된 컨트롤 탐색 환경

A에서 B로 이동하는 데 도움이 되는 탐색 환경을 새로 고쳐 자신감 있게 더욱 집중할 수 있게 했습니다.

* **15.4의 새로운 기능**: **정의로 이동**(**Ctrl**+**클릭** 또는 **F12**)&ndash; 마우스 사용자는 **Ctrl**를 누른 다음, 해당 멤버를 클릭하여 멤버 정의로 이동할 수 있는 더 쉬운 방법이 있습니다. **Ctrl** 키를 누르고 코드 기호에 마우스를 올려 놓으면 밑줄이 쳐지고 링크로 바뀝니다. 자세한 내용은 [정의로 이동 및 정의 피킹(Peeking)](go-to-and-peek-definition.md)을 참조하세요.

* **구현으로 이동** (**Ctrl**+**F12**)&ndash; 모든 베이스 형식 또는 멤버에서 다양한 구현으로 이동합니다.

* **전체로 이동**(**Ctrl**+**T** 또는 **Ctrl**+ **,** ) &ndash;모든 파일/형식/멤버/기호 선언으로 직접 이동합니다. 결과 목록을 필터링하거나 쿼리 구문을 사용할 수 있습니다(예: 파일의 경우 “f searchTerm”, 형식의 경우 “t searchTerm”).

  ![전체로 이동 기능 향상](media/vs2017ide-navigation-go-to.png)

* **모든 참조 찾기(Shift+F12)** (**Shift**+**F12**) &ndash; 구문 색 지정을 사용하면 프로젝트, 정의 및 경로의 조합에 따라 [모든 참조 찾기] 결과를 그룹화할 수 있습니다. 또한 결과를 “잠그면” 원래 결과를 잃지 않고 다른 참조를 계속 찾을 수 있습니다.

  ![새로운 모든 참조 찾기 도구](media/vs2017ide-find-all-references.png)

* **구조체 시각화 도우미** &ndash; 회색 세로 점선(들여쓰기 가이드)은 코드에서 랜드마크로 작용하여 보기의 프레임 내에서 컨텍스트를 제공합니다. 이러한 기능은 인기 있는 생산성 파워 도구에서 확인할 수 있습니다. 이 안내선을 사용하면 언제든지 스크롤하지 않고도 작업 중인 코드 블록을 시각화하고 검색할 수 있습니다. 선 위로 마우스를 가리키면 해당 블록과 그 부모를 열어서 볼 수 있는 도구 설명이 표시됩니다. TextMate 문법 검사뿐만 아니라 C#, Visual Basic 및 XAML을 통해 지원되는 모든 언어에서 사용할 수 있습니다.

  ![Visual Studio 2017 구조체 시각화 도우미](media/vsIDE-StructureVisualizer.png)

새로운 생산성 기능에 대한 자세한 내용은 [Visual Studio 2017: Productivity, Performance, and Partners](https://devblogs.microsoft.com/visualstudio/visual-studio-2017-productivity-performance-and-partners/)(Visual Studio 2017: 생산성, 성과 및 파트너) 블로그 게시물을 참조하세요.

### <a name="visual-c"></a>Visual C++

Visual Studio에서 C++ 핵심 지침을 배포하고, C++11 및 C++ 기능에 대한 향상된 지원을 추가하여 컴파일러를 업데이트하고, C++ 라이브러리에서 기능을 추가 및 업데이트하는 등 Visual Studio에서 향상된 몇 가지 기능을 확인할 수 있습니다. C++ IDE, 설치 작업 등의 성능도 향상되었습니다.

또한 많은 고객이 [C++ 개발자 커뮤니티](https://developercommunity.visualstudio.com/spaces/62/index.html "C++ 개발자 커뮤니티")를 통해 제출한 컴파일러와 도구에서 발생된 250개 이상의 버그와 보고된 문제를 해결했습니다.

자세한 내용은 [Visual 2017의 Visual C++에 대한 새로운 기능](/cpp/top/what-s-new-for-visual-cpp-in-visual-studio) 페이지를 참조하세요.

### <a name="debugging-and-diagnostics"></a>디버깅 및 진단

#### <a name="run-to-click"></a>실행하려면 클릭

이제 원하는 줄에서 중지하도록 중단점을 설정하지 않고도 디버깅 중에 더 쉽게 건너뛸 수 있습니다. 디버거에서 멈췄을 때 코드 줄 옆에 나타나는 아이콘을 클릭하면 됩니다. 코드가 실행되어 다음에 코드 경로에서 이 줄에 도달하면 해당 줄에서 중지됩니다.

![Visual Studio 2017 디버그 - 실행하려면 클릭](media/vs2017ide-RunToClick.png)

#### <a name="the-new-exception-helper"></a>새 예외 도우미

새 예외 도우미를 사용하면 예외 정보를 한눈에 볼 수 있습니다. 정보는 내부 예외에 즉시 액세스할 수 있는 간결한 양식으로 제공됩니다. NullReferenceException을 진단할 때 예외 도우미 내부에서 null인 항목을 빠르게 확인할 수 있습니다.

![Visual Studio의 새 예외 도우미 대화 상자](media/vs2017ide-ExceptionHelper.png)

자세한 내용은 [Using the New Exception Helper in Visual Studio](https://devblogs.microsoft.com/devops/using-the-new-exception-helper-in-visual-studio-15-preview/)(Visual Studio에서 새 예외 도우미 사용) 블로그 게시물을 참조하세요.

#### <a name="snapshots-and-intellitrace-step-back"></a>스냅샷 및 IntelliTrace 뒤로 이동

**15.5의 새로운 기능**: IntelliTrace 뒤로 이동은 모든 중단점 및 디버거 단계 이벤트에서 애플리케이션의 스냅샷을 자동으로 생성합니다. 기록된 스냅샷을 통해 이전 중단점 또는 단계로 돌아가서 애플리케이션의 과거 상태를 볼 수 있습니다. IntelliTrace 뒤로 이동을 사용하면 이전 애플리케이션 상태를 보고 싶지만 디버깅을 다시 시작하거나 원하는 앱 상태를 다시 만들지 않으려는 경우에 시간을 절약할 수 있습니다.

**디버그** 도구 모음의 **뒤로 가기**와 **앞으로 가기** 단추를 사용하여 이동하고 스냅샷을 볼 수 있습니다. 이 단추를 사용하여 **진단 도구** 창의 **이벤트** 탭에 나타나는 이벤트를 탐색할 수 있습니다. 이벤트의 앞이나 뒤로 이동하면 선택한 이벤트에 대한 기록 디버깅이 자동으로 활성화됩니다.

![Visual Studio의 IntelliTrace 단계 뒤로 실행 예제](../debugger/media/intellitrace-step-back-icons-description.png  "뒤로 이동 및 앞으로 이동 단추")

자세한 내용은 [IntelliTrace 뒤로 이동을 사용하여 스냅샷 보기](../debugger/view-historical-application-state.md) 페이지를 참조하세요.

### <a name="containerization"></a>컨테이너화

컨테이너는 향상된 생산성 및 DevOps 민첩성과 더불어 향상된 앱 밀도와 낮은 배포 비용을 제공합니다.

#### <a name="docker-container-tooling"></a>Docker 컨테이너 도구

**15.5의 새로운 기능**:

* Visual Studio에 이제 다단계 Dockerfile을 지원하는 Docker 컨테이너용 도구가 포함되어 최적화된 컨테이너 이미지 만들기가 간소화됩니다.
* 기본적으로 Visual Studio는 Docker 지원이 포함된 프로젝트를 열 때 백그라운드에서 필요한 컨테이너 이미지를 자동으로 끌어오고, 빌드하고 실행합니다. Visual Studio에서 **백그라운드에서 컨테이너를 자동으로 시작** 설정을 통해 비활성화할 수 있습니다.

## <a name="cloud-app-development-with-azure"></a>Azure로 클라우드 앱 개발

### <a name="azure-functions-tools"></a>Azure Functions 도구

미리 컴파일된 C# 클래스 라이브러리를 사용하여 Azure Functions를 개발하는 데 도움이 되는 도구를 “Azure 개발” 워크로드의 일부로 포함했습니다. 이제 로컬 개발 컴퓨터에서 빌드, 실행 및 디버그한 다음 Visual Studio에서 Azure에 직접 게시할 수 있습니다.

자세한 내용은 [Visual Studio용 Azure Functions 도구](/azure/azure-functions/functions-develop-vs) 페이지를 참조하세요.

### <a name="debug-live-aspnet-apps-using-snappoints-and-logpoints-in-live-azure-applications"></a>라이브 Azure 애플리케이션에서 snappoint와 logpoint를 사용하여 라이브 ASP.NET 앱 디버그

**15.5의 새로운 기능**: 스냅샷 디버거는 관심이 있는 코드가 실행될 때 프로덕션 상태 앱의 스냅샷을 생성합니다. 디버거가 스냅샷을 생성하도록 명령하려면 코드에서 snappoint와 logpoint를 설정합니다. 디버거를 통해 프로덕션 애플리케이션의 트래픽에 영향을 미치지 않으면서 정확히 무엇이 잘못되었는지를 볼 수 있습니다. 스냅샷 디버거를 사용하면 프로덕션 환경에서 발생하는 문제를 해결하는 데 걸리는 시간을 상당히 줄일 수 있습니다.

스냅샷 컬렉션은 Azure App Service에서 실행되는 다음 웹앱에서 사용할 수 있습니다.

* .NET Framework 4.6.1 이상에서 실행되는 ASP.NET 애플리케이션
* Windows의 .NET Core 2.0 이상에서 실행되는 ASP.NET Core 애플리케이션

자세한 내용은 [snappoint와 logpoint를 사용하여 라이브 ASP.NET 앱 디버그](../debugger/debug-live-azure-applications.md)를 참조하세요.

## <a name="windows-app-development"></a>Windows 앱 개발

### <a name="universal-windows-platform"></a>UWP

UWP(Universal Windows Platform)는 Windows 10용 앱 플랫폼입니다. API 집합 하나, 앱 패키지 하나 및 스토어 하나만으로 UWP용 앱을 개발하여 모든 Windows 10 디바이스 &ndash; PC, 태블릿, 전화, Xbox, HoloLens, Surface Hub 등에 연결할 수 있습니다. UWP는 다양한 화면 크기와 터치, 마우스와 키보드, 게임 컨트롤러 또는 펜을 비롯한 다양한 인터랙션 모델을 지원합니다. UWP 앱의 핵심은 작업 환경이 사용자의 모든 디바이스에서 이동이 가능하여 현재 진행 중인 작업에 가장 편리하거나 생산적인 디바이스를 사용하기를 바란다는 점입니다.

![UWP](../cross-platform/media/uwp_coreextensions.png)

&mdash;C#, Visual Basic, C++ 또는 JavaScript&mdash; 중에서 원하는 개발 언어를 선택하여 Windows 10 디바이스용 유니버설 Windows 플랫폼 앱을 만듭니다. Visual Studio 2017은 모든 디바이스에 대해 단일 프로젝트를 만들 수 있도록 각 언어에 UWP 앱 템플릿을 제공합니다. 작업을 마치면 Visual Studio 내에서 앱 패키지를 생성하고 Microsoft Store에 제출하여 Windows 10 디바이스를 사용하는 고객에게 앱을 제공할 수 있습니다.

**15.5의 새로운 기능**: Visual Studio 2017 버전 15.5는 Windows 10 Fall Creators Update SDK(10.0.16299.0)를 가장 잘 지원합니다. Windows 10 Fall Creators Update는 UWP 개발자를 위해 많은 사항이 개선되었습니다. 다음은 큰 변화 중 일부입니다. 

* **.NET Standard 2.0에 대한 지원**<br/>간소화된 앱 배포 외에, Windows 10 Fall Creators Update는 .NET Standard 2.0 지원을 제공하는 첫 번째 Windows 10 릴리스입니다. 사실상, [.NET Standard](https://devblogs.microsoft.com/dotnet/introducing-net-standard/)는 모든 .NET 플랫폼에서 구현할 수 있는 기본 클래스 라이브러리의 참조 구현입니다. .NET Standard의 목표는 .NET 개발자가 작업하는 모든 .NET 플랫폼 전반에서 코드를 최대한 쉽게 공유할 수 있도록 하는 것입니다.
* **UWP와 Win32의 장점**<br/>Windows 10 플랫폼은 [데스크톱 브리지](/windows/uwp/porting/desktop-to-uwp-root)를 통해 개발자가 중점을 두는 것이 UWP, WPF, Windows Forms 또는 Xamarin 중 무엇이든 모든 .NET 개발자가 Windows 10을 더 잘 활용할 수 있도록 향상되었습니다. Visual Studio 2017 버전 15.5의 새로운 앱 패키징 프로젝트 형식을 사용하면 UWP 프로젝트에서 하듯이 WPF 또는 Windows Forms 프로젝트용 Windows 앱 패키지를 만들 수 있습니다. 앱을 패키지하면 Windows 10 앱 배포의 모든 이점과 Microsoft Store(소비자 앱) 또는 비즈니스 및 교육용 Microsoft Store를 통해 배포할 수 있는 옵션이 제공됩니다. 패키지된 앱은 데스크톱의 전체 UWP API 표면과 Win32 API 모두에 액세스할 수 있기 때문에 UWP API 및 Windows 10 기능을 사용하여 WPF 및 Windows Forms 애플리케이션을 점진적으로 현대화할 수 있습니다. 또한 모든 Win32 기능을 갖춘 데스크톱에서 실행되는 UWP 애플리케이션에 Win32 구성 요소를 포함할 수 있습니다.

UWP에 대한 자세한 내용은 [UWP(유니버설 Windows 플랫폼)용 앱 개발](../cross-platform/develop-apps-for-the-universal-windows-platform-uwp.md) 페이지를 참조하세요.

## <a name="mobile-app-development"></a>모바일 앱 개발

### <a name="xamarin"></a>Xamarin

“.NET을 사용한 모바일 개발” 워크로드의 일부로, C#, .NET 및 Visual Studio에 친숙한 개발자는 Xamarin을 사용하여 네이티브 Android, iOS 및 Windows 앱을 제공할 수 있습니다. 개발자는 모바일 앱용 Xamarin을 사용할 때 Objective-C 또는 Java 같은 네이티브 코딩 언어를 배울 필요 없이 Android, iOS 및 Windows 디바이스의 원격 디버깅을 비롯한 동일한 기능을 사용하여 생산성을 얻을 수 있습니다.

자세한 내용은 [Visual Studio 및 Xamarin](/xamarin/) 페이지를 참조하세요.

### <a name="entitlements-editor"></a>자격 편집기

**15.3의 새로운 기능**: iOS 개발 요구 사항을 해결하기 위해 독립 실행형 자격 편집기를 추가했습니다. 이 편집기에는 쉽게 검색할 수 있는 사용자에게 친숙한 UI가 포함되어 있습니다. 시작하려면 *entitlements.plist* 파일을 두 번 클릭합니다.

![Xamarin에 대한 권한 편집기](media/xamarin-entitlements-editor.png)

### <a name="visual-studio-tools-for-xamarin"></a>Visual Studio Tools for Xamarin

**15.4의 새로운 기능**: Xamarin Live를 사용하여 개발자는 iOS 및 Android 디바이스에서 직접 자신의 앱을 계속해서 배포, 테스트 및 디버그할 수 있습니다. &mdash;앱 스토어 또는 Google Play에서 사용할 수 있는&mdash; Xamarin Live Player를 다운로드한 후 디바이스를 Visual Studio와 연결하고 모바일 앱을 빌드하는 방법을 혁신적으로 개선할 수 있습니다. 이 기능은 이제 Visual Studio에 포함되었으며 **도구** > **옵션** > **Xamarin** > **기타** > **Xamarin Live Player 사용**으로 이동하여 사용하도록 설정할 수 있습니다.

![Xamarin Live Player 쌍, 배포 및 라이브 편집 모드의 애니메이션](media/xamarinliveplayer.gif)

### <a name="support-for-google-android-emulator"></a>Google Android Emulator에 대한 지원

**15.8의 새로운 기능**: Hyper-V를 사용하는 경우 Google의 Android Emulator를 Hyper-V 가상 머신, Docker 도구, HoloLens 에뮬레이터 등 Hyper-V에 기반한 다른 기술과 함께 병렬로 사용할 수 있습니다. (이 기능을 사용하려면 Windows 10 2018년 4월 업데이트 이상이 필요합니다.)

![Hyper-V 기술에서 Google Android Emulator](media/xamarin-hyperv-android-emulator.png)

#### <a name="xamarinandroid-designer-split-view-editor"></a>Xamarin.Android Designer 분할 보기 편집기

또한 **15.8의 새로운 기능**: Xamarin.Android의 디자이너 환경이 대폭 개선되었습니다. 핵심은 동시에 레이아웃을 만들고, 편집하고, 미리 볼 수 있는 분할 보기 편집기입니다.

![Xamarin.Android Designer 분할 보기 편집기](media/android-designer-split-view.png)

자세한 내용은 [에뮬레이터 성능에 대한 하드웨어 가속](/xamarin/android/get-started/installation/android-emulator/hardware-acceleration?tabs=vswin)을 참조하세요.

### <a name="visual-studio-app-center"></a>Visual Studio 앱 센터

**15.5의 새로운 기능**: Visual Studio App Center&mdash;이제 Android, iOS, macOS 및 Windows 앱용으로 일반 공급됨&mdash;에는 자동화된 빌드, 클라우드의 실제 디바이스에서 테스트, 베타 테스터 및 앱 스토어 배포, 충돌 및 분석 데이터를 통한 실제 사용 모니터링을 비롯하여 앱의 수명 주기를 관리하는 데 필요한 모든 것이 있습니다. Objective-C, Swift, Java, C#, Xamarin, React Native로 작성된 앱이 모든 기능에서 지원됩니다.

  ![Visual Studio App Center 테스트 환경](media/app-center-test-env.png)

자세한 내용은 [App Center 소개: 클라우드에서 앱 빌드, 테스트, 배포 및 모니터링](https://blogs.msdn.microsoft.com/vsappcenter/introducing-visual-studio-app-center/) 블로그 게시물을 참조하세요.

## <a name="cross-platform-development"></a>플랫폼 간 개발

### <a name="redgate-data-tools"></a>Redgate 데이터 도구

DevOps 기능을 SQL Server 데이터베이스 개발로 확장하기 위해 Visual Studio에서 현재 Redgate 데이터 도구를 사용할 수 있습니다.

Visual Studio 2017 Enterprise에는 다음이 포함되어 있습니다.

* [Redgate ReadyRoll Core](https://www.red-gate.com/products/sql-development/sql-change-automation/?utm_source=microsoft&utm_medium=link&utm_campaign=readyroll&utm_term=docs-newinvs)는 마이그레이션 스크립트를 개발하고, 소스 제어를 사용하여 데이터베이스 변경 내용을 관리하고, SQL Server 데이터베이스 변경 내용을 애플리케이션 변경 내용과 함께 자동으로 안전하게 배포하는 데 도움이 됩니다.
* [Redgate SQL Prompt 코어](https://www.red-gate.com/products/sql-development/sql-prompt/?utm_source=microsoft&utm_medium=link&utm_campaign=sqlprompt&utm_term=docs-newinvs)는 지능형 코드 완성 기능을 통해 SQL을 더 빠르고 정확하게 작성하는 데 도움이 됩니다. SQL 프롬프트는 데이터베이스 및 시스템 개체, 키워드를 자동으로 완성하고 입력 시 열을 제안합니다. 모든 열 이름이나 별칭을 기억할 필요가 없으므로 코드가 더 깔끔해지고 오류가 줄어듭니다.

Visual Studio 2017의 모든 버전에는 다음이 포함되어 있습니다.

* [Redgate SQL 검색](https://www.red-gate.com/products/sql-development/sql-search/?utm_source=microsoft&utm_medium=link&utm_campaign=sqlsearch&utm_term=docs-newinvs)은 여러 데이터베이스에서 SQL 조각 및 개체를 빠르게 찾을 수 있도록 하여 생산성을 높입니다.

자세히 알아보려면 [Visual Studio 2017의 Redgate 데이터 도구](https://devblogs.microsoft.com/visualstudio/redgate-data-tools-in-visual-studio-2017/)(영문) 블로그 게시물을 참조하세요.

### <a name="net-core"></a>.NET Core

.NET Core는 .NET Standard의 일반적인 용도를 위한 모듈식 플랫폼 간 오픈 소스 구현이며 .NET Framework와 동일한 API를 다수 포함합니다.

.NET Core 플랫폼은 관리되는 컴파일러, 런타임, 기본 클래스 라이브러리 및 ASP.NET Core와 같은 다양한 애플리케이션 모델을 포함하는 여러 요소로 구성됩니다. .NET Core는 세 개의 주요 운영 체제를 지원합니다. Windows, Linux 및 macOS. 디바이스, 클라우드 및 포함/IoT 시나리오에 .NET Core를 사용할 수 있습니다.

그리고 이제 Docker 지원도 포함합니다.

**15.3의 새로운 기능**: Visual Studio 2017 버전 15.3은 .NET Core 2.0 개발을 지원합니다. .NET Core 2.0을 사용하려면 .NET Core 2.0 SDK를 별도로 다운로드하여 설치해야 합니다.

자세한 내용은 [.NET Core 가이드](/dotnet/core/index) 페이지를 참조하세요.

## <a name="games-development"></a>게임 개발

### <a name="visual-studio-tools-for-unity"></a>Visual Studio Tools for Unity

“Unity용 게임 개발” 워크로드의 일부로, 플랫폼 간 개발을 통해 2D 및 3D 게임과 대화형 콘텐츠를 만드는 데 도움이 되는 도구를 포함했습니다. Visual Studio 2017과 Unity 5.6을 사용하여 게임을 한 번 만들면 모든 모바일 플랫폼과 WebGL, Mac, PC, Linux 데스크톱, 웹 또는 콘솔을 포함한 21개 플랫폼에 게시할 수 있습니다.

자세한 내용은 [Visual Studio Tools for Unity](../cross-platform/visual-studio-tools-for-unity.md) 페이지를 참조하세요.

## <a name="ai-development"></a>AI 개발

### <a name="visual-studio-tools-for-ai"></a>Visual Studio Tools for AI

**15.5의 새로운 기능**: Visual Studio의 생산성 기능을 사용하여 현재의 AI 혁신을 가속화합니다. 구문 강조 표시, IntelliSense 및 텍스트 자동 서식 지정과 같이 기본 제공되는 코드 편집기 기능을 사용하세요. 지역 변수 및 모델에 대한 단계별 디버깅을 사용하여 로컬 환경에서 딥 러닝 애플리케이션을 대화형으로 테스트할 수 있습니다.

  ![딥 러닝 IDE](../ai/media/about/ide.png)

자세한 내용은 [Visual Studio Tools for AI](../ai/about-ai-tools.md) 페이지를 참조하세요.

## <a name="whats-next"></a>새로운 기능

Visual Studio 2017은 개발 환경을 훨씬 더 좋게 만들어 줄 수 있는 새 기능으로 자주 업데이트됩니다. 실험적 미리 보기에 있는 가장 주목할 만한 업데이트 몇 가지를 요약하면 다음과 같습니다.

* **[실시간 공유](https://visualstudio.microsoft.com/services/live-share/)** - Visual Studio 내에서 바로 코드베이스와 컨텍스트를 팀원과 공유하고 즉각적인 양방향 협업을 수행할 수 있는 새로운 도구입니다. 실시간 공유를 사용하면 귀하가 공유한 프로젝트를 팀원이 원활하고 안전하게 읽고, 탐색하고, 편집하고, 디버깅할 수 있습니다.<br><br>자세한 내용은 [실시간 공유 FAQ](/visualstudio/liveshare/faq)를 참조하세요.<br><br>
* **[IntelliCode](https://visualstudio.microsoft.com/services/intellicode/)** - AI를 사용하여 더 나은 컨텍스트 인식 코드 완성 기능을 제공하고, 개발자에게 팀의 패턴과 스타일에 맞게 코딩하도록 안내하고, 찾기 어려운 코드 문제를 발견하고, 코드 검토를 정말로 중요한 영역에 집중시켜서 소프트웨어 개발을 개선하는 새로운 기능입니다. <br><br>자세한 내용은 [IntelliCode FAQ](/visualstudio/intellicode/faq)를 참조하세요.

Visual Studio 2017에서 진행 중인 다른 기능에 대해 더 알고 싶은가요? [Visual Studio 로드맵](/visualstudio/productinfo/vs2018-roadmap) 페이지를 참조하세요.

또한 최신 버전인 [Visual Studio 2019](whats-new-visual-studio-2019.md)를 확인해야 합니다.

## <a name="contact-us"></a>문의처

피드백을 보낼 때는 Visual Studio 팀에 피드백을 보내는 이유도 함께 알려 주세요. Microsoft는 고객 여러분의 피드백을 소중하게 생각하며, Microsoft에서 추진하는 업무에 큰 역할을 합니다.

Visual Studio를 개선하는 방법을 제안하거나 제품 지원 옵션에 대해 자세히 알아보려면 [의견 보내기](feedback-options.md) 페이지를 참조하세요.

### <a name="report-a-problem"></a>문제 보고

발생한 문제의 전반적인 영향을 메시지만으로 전달할 수 없는 경우도 있습니다. Visual Studio가 응답을 중지하거나 크래시가 발생하는 문제 또는 기타 성능 문제가 발생하는 경우 **문제 신고** 도구를 사용하여 쉽게 재현 단계 및 지원 파일(예: 스크린샷, 추적 및 힙 덤프 파일)을 공유할 수 있습니다. 이 도구를 사용하는 방법에 대한 자세한 내용은 [문제를 보고하는 방법](how-to-report-a-problem-with-visual-studio.md) 페이지를 참조하세요.

## <a name="see-also"></a>참조

* [Visual Studio 2017 릴리스 정보](/visualstudio/releasenotes/vs2017-relnotes)
* [Visual Studio 2017 SDK의 새로운 기능](../extensibility/what-s-new-in-the-visual-studio-2017-sdk.md)
* [Visual C++의 새로운 기능](/cpp/top/what-s-new-for-visual-cpp-in-visual-studio)
* [C#의 새로운 기능](/dotnet/csharp/whats-new)
* [Team Foundation Server의 새로운 기능](/azure/devops/server/whats-new)
* [Mac용 Visual Studio의 새로운 기능](https://visualstudio.microsoft.com/vs/visual-studio-mac/)
* [Visual Studio 2019의 새로운 기능](whats-new-visual-studio-2019.md)