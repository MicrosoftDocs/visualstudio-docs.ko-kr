---
title: Mac용 Visual Studio 둘러보기
description: Mac용 Visual Studio에서는 iOS, Android, Mac, Xamarin.Forms용 Xamarin 프로젝트와 ASP.NET Core 웹 사이트를 비롯하여 macOS에서 .NET 애플리케이션을 빌드하기 위한 통합 개발 환경을 제공합니다.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 07/03/2020
ms.assetid: 7DC64A52-AA41-4F3A-A8A1-8A20BCD81CC7
ms.custom: video
ms.openlocfilehash: 56af8f7cd30ec8e41ece2772dc63d67a2dbf3976
ms.sourcegitcommit: 703c68667261df5985a73282c1cbb0541118989c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "89402615"
---
# <a name="visual-studio-2019-for-mac-tour"></a>Mac용 Visual Studio 2019 둘러보기

Mac용 Visual Studio는 코드를 편집, 디버그 및 빌드한 다음, 앱을 게시하는 데 사용할 수 있는 Mac의 .NET _통합 개발 환경_입니다. Mac용 Visual Studio에는 코드 편집기 및 디버거 외에도 컴파일러, 코드 완성 도구, 그래픽 디자이너, 소스 제어 기능이 포함되어 있어 소프트웨어 개발 프로세스가 쉽습니다.

Mac용 Visual Studio는 `.csproj`, `.fsproj` 또는 `.sln` 파일과 같은 Windows 카운터파트와 동일한 여러 파일 형식을 지원하고 EditorConfig와 같은 기능을 지원합니다. 이는 가장 적합한 IDE를 사용할 수 있음을 의미합니다.
앱을 만들고 열고 개발하는 작업은 이전에 Windows에서 Visual Studio를 사용한 적이 있는 모든 사용자에게 익숙한 경험일 것입니다. 또한 Mac용 Visual Studio에서는 해당하는 Windows 제품을 효과적인 IDE로 만드는 여러 가지 효과적인 도구를 활용합니다. Roslyn 컴파일러 플랫폼은 리팩터링 및 IntelliSense에 사용됩니다. 해당 프로젝트 시스템과 빌드 엔진은 MSBuild를 사용하고, 해당 소스 편집기는 Windows의 Visual Studio와 동일한 기반을 사용합니다. Xamarin 및 .NET Core 앱에 대해 동일한 디버거 엔진을 사용하고, Xamarin.iOS 및 Xamarin.Android에 대해 동일한 디자이너를 사용합니다.

## <a name="what-can-i-do-in-visual-studio-for-mac"></a>Mac용 Visual Studio에서 무엇을 할 수 있나요?

Mac용 Visual Studio는 다음과 같은 개발 유형을 지원합니다.

- Razor Pages, JavaScript, TypeScrip 지원, C#, F#을 사용한 ASP.NET Core 웹 애플리케이션
- C# 또는 F#이 있는 .NET Core 콘솔 애플리케이션
- C#이 있는 플랫폼 간 Unity 게임 및 애플리케이션
- C# 또는 F# 및 XAML이 있는 Xamarin의 Android, iOS, tvOS 및 watchOS 애플리케이션
- C# 또는 F#의 Cocoa 데스크톱 앱

이 문서에서는 Mac용 Visual Studio의 다양한 섹션을 살펴보고, 이러한 애플리케이션을 만들기 위한 효과적인 도구를 구성하는 몇 가지 기능을 설명합니다.

## <a name="ide-tour"></a>IDE 둘러보기

Mac용 Visual Studio는 애플리케이션 파일 및 설정 관리, 애플리케이션 코드 작성, 디버깅을 위한 여러 섹션으로 구성되어 있습니다.

## <a name="getting-started"></a>시작

Mac용 Visual Studio 2019를 처음 시작하는 새 사용자에게는 로그인 창이 표시됩니다. Microsoft 계정으로 로그인하여 유료 라이선스를 활성화하거나(갖고 있는 경우) Azure 구독에 연결합니다. **나중에 하겠습니다.** 를 누른 다음, 나중에 **Visual Studio > 로그인** 메뉴 항목에서 로그인해도 됩니다.

![Microsoft 계정으로 로그인](media/ide-tour-2019-start-signin.png)

그러면 원하는 바로 가기 키를 선택하여 IDE를 사용자 지정하는 옵션이 제공됩니다. Mac용 Visual Studio, Visual Studio, Visual Studio Code 또는 Xcode:

![원하는 바로 가기 키 선택](media/ide-tour-2019-keyboard-shortcut.png)

이 초기 설정 후에는 Mac용 Visual Studio 2019를 열 때마다 최근 프로젝트 목록과 기존 프로젝트를 열거나 새 프로젝트를 만들 수 있는 단추가 표시되는 _시작 창_이 표시됩니다.

![최근에 사용한 프로젝트 중에서 선택하거나 새로 만들기](media/ide-tour-2019-start-projects.png)

## <a name="solutions-and-projects"></a>솔루션 및 프로젝트

다음 이미지는 애플리케이션이 로드된 Mac용 Visual Studio를 보여줍니다.

![애플리케이션이 로드된 Mac용 Visual Studio](media/ide-tour-image17.png)

다음 섹션에서는 Mac용 Visual Studio의 주요 영역에 대한 개요를 제공합니다.

## <a name="solution-pad"></a>Solution Pad

Solution Pad는 솔루션의 프로젝트를 구성합니다.

![Solution Pad에 구성된 프로젝트](media/ide-tour-image18.png)

여기서 소스 코드, 리소스, 사용자 인터페이스, 종속성에 대한 파일이 플랫폼별 프로젝트에 구성됩니다.

Mac용 Visual Studio에서 프로젝트와 솔루션을 사용하는 방법에 대한 자세한 내용은 [프로젝트 및 솔루션](/visualstudio/mac/projects-and-solutions) 문서를 참조하세요.

## <a name="assembly-references"></a>어셈블리 참조

각 프로젝트에 대한 어셈블리 참조는 참조 폴더 아래에서 확인할 수 있습니다.

![Solution Pad의 참조 폴더](media/ide-tour-image19.png)

**참조 편집** 대화 상자를 사용하여 참조를 더 추가합니다. 이 대화 상자는 참조 폴더를 두 번 클릭하거나 상황에 맞는 메뉴 작업에서 **참조 편집**을 선택하면 표시됩니다.

![참조 편집 대화 상자](media/ide-tour-image20.png)

Mac용 Visual Studio에서 참조를 사용하는 방법에 대한 자세한 내용은 [프로젝트의 참조 관리](/visualstudio/mac/managing-references-in-a-project) 문서를 참조하세요.

## <a name="dependencies--packages"></a>종속성/패키지

앱에서 사용되는 모든 외부 종속성은 .NET Core와 Xamarin.iOS/Xamarin.Android 중 어떤 프로젝트를 사용 중인지에 따라 종속성 또는 패키지 폴더에 저장됩니다. 일반적으로 NuGet의 형태로 제공됩니다.

NuGet은 가장 인기 있는 .NET 개발용 패키지 관리자입니다. Visual Studio의 NuGet 지원을 통해 쉽게 패키지를 검색하고 프로젝트 또는 애플리케이션에 추가할 수 있습니다.

애플리케이션에 종속성을 추가하려면 종속성/패키지 폴더를 마우스 오른쪽 단추로 클릭하고 **패키지 추가**를 선택합니다.

![NuGet 패키지 추가](media/ide-tour-image21.png)

애플리케이션에서 NuGet 패키지를 사용하는 방법에 대한 자세한 내용은 [사용자 프로젝트에 NuGet 프로젝트 포함](/visualstudio/mac/nuget-walkthrough) 문서를 참조하세요.

## <a name="source-editor"></a>소스 편집기

C#, XAML, JavaScript 중 어떤 언어로 작성하든 코드 편집기는 완전한 네이티브 사용자 인터페이스를 사용하여 Windows에서 동일한 핵심 구성 요소를 Visual Studio와 공유합니다.

따라서 다음과 같은 기능이 제공됩니다.

* 네이티브 macOS(Cocoa 기반) 사용자 인터페이스(도구 설명, 편집기 화면, 여백 장식, 텍스트 렌더링 IntelliSense)
* IntelliSense 형식 필터링 및 “가져오기 항목 표시”
* 네이티브 텍스트 입력 지원
* RTL/BiDi 언어 지원
* Roslyn 3
* 다중 캐럿 지원
* 단어 줄 바꿈
* 업데이트된 IntelliSense UI
* 향상된 찾기/바꾸기
* 코드 조각 지원 
* 선택 영역 서식
* 인라인 전구

Mac용 Visual Studio에서 소스 편집기를 사용하는 방법에 대한 자세한 내용은 [소스 편집기](/visualstudio/mac/source-editor) 설명서를 참조하세요.

항상 탭이 표시되도록 하려면 탭을 고정할 수 있습니다. 이렇게 하면 프로젝트를 시작할 때마다 필요한 탭이 항상 표시됩니다. 탭을 고정하려면 탭을 마우스로 가리키고 _고정_ 아이콘을 클릭합니다.

![탭 고정](media/ide-tour-tabpin.png)

## <a name="refactoring"></a>리팩터링

Mac용 Visual Studio에서는 코드를 리팩터링하는 두 가지 유용한 방법인 컨텍스트 작업과 소스 분석 기능을 제공합니다. 자세한 내용은 [리팩터링](/visualstudio/mac/refactoring) 문서를 참조하세요.

## <a name="debugging"></a>디버깅

Mac용 Visual Studio에는 .NET Core, .NET Framework, Unity 및 Xamarin 프로젝트를 지원하는 디버거가 있습니다. Mac용 Visual Studio는 .NET Core 디버거 및 Mono Soft 디버거를 사용하므로 IDE가 모든 플랫폼에서 관리 코드를 디버그할 수 있습니다. 디버깅에 대한 자세한 내용은 [디버깅](/visualstudio/mac/debugging) 문서를 참조하세요.

디버거에는 문자열, 색, URL, 크기, 좌표, 베지어 곡선 등의 특수 형식에 대한 다양한 시각화 도우미가 포함되어 있습니다.

디버거의 데이터 시각화에 대한 자세한 내용은 [데이터 시각화](/visualstudio/mac/data-visualizations) 문서를 참조하세요.

## <a name="version-control"></a>버전 제어

Mac용 Visual Studio는 Git 및 Subversion 소스 제어 시스템과 통합됩니다. 소스 제어가 적용되는 프로젝트는 솔루션 이름 옆에 분기가 표시됩니다.

![소스 제어가 적용되는 프로젝트를 나타내는 분기 이름](media/ide-tour-image22.png)

커밋되지 않은 변경 내용이 있는 파일은 다음 이미지와 같이 솔루션 창에서 해당 아이콘에 주석이 있습니다.

![Solution Pad의 커밋되지 않은 파일](media/ide-tour-image23.png)

Visual Studio에서 버전 제어를 사용하는 방법에 대한 자세한 내용은 [버전 제어](/visualstudio/mac/version-control) 문서를 참조하세요.

## <a name="next-steps"></a>다음 단계

- [Mac용 Visual Studio 설치](installation.md)
- [사용 가능한 워크로드 검토](workloads.md)

## <a name="related-video"></a>관련 동영상

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Overview/player]

## <a name="see-also"></a>참조

- [Windows의 Visual Studio IDE](/visualstudio/ide/visual-studio-ide)
