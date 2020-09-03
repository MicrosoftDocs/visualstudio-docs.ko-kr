---
title: Mac용 Visual Studio 둘러보기
description: Mac용 Visual Studio에서는 iOS, Android, Mac, Xamarin.Forms용 Xamarin 프로젝트와 ASP.NET Core 웹 사이트를 비롯하여 macOS에서 .NET 애플리케이션을 빌드하기 위한 통합 개발 환경을 제공합니다.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 02/07/2019
ms.assetid: 7DC64A52-AA41-4F3A-A8A1-8A20BCD81CC7
ms.custom: video
ms.openlocfilehash: 3d25fced1e9c9dd6431f4056b5b561f476eecb28
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74984977"
---
# <a name="visual-studio-2017-for-mac-tour"></a>Mac용 Visual Studio 2017 둘러보기

> [!NOTE]
> Mac용 Visual Studio 2019는 [현재 사용 가능](installation.md)합니다.

Mac용 Visual Studio는 코드를 편집, 디버그 및 빌드한 다음, 앱을 게시하는 데 사용할 수 있는 Mac의 .NET _통합 개발 환경_입니다. Mac용 Visual Studio는 표준 편집기 및 디버거와 같은 예상 기능 외에도 컴파일러, 코드 완성 도구, 그래픽 디자이너 및 소프트웨어 개발 프로세스를 위한 소스 제어를 포함하고 있습니다.

Mac용 Visual Studio는 `.csproj`, `.fsproj` 또는 `.sln` 파일과 같은 Windows 카운터파트와 동일한 여러 파일 형식을 지원하고 EditorConfig와 같은 기능을 지원합니다. 이는 가장 적합한 IDE를 사용할 수 있음을 의미합니다.
앱을 만들고 열고 개발하는 작업은 이전에 Windows에서 Visual Studio를 사용한 적이 있는 모든 사용자에게 익숙한 경험일 것입니다. 또한 Mac용 Visual Studio에서는 해당하는 Windows 제품을 효과적인 IDE로 만드는 여러 가지 효과적인 도구를 활용합니다. Roslyn 컴파일러 플랫폼은 리팩터링 및 IntelliSense에 사용됩니다. 해당 프로젝트 시스템과 빌드 엔진은 MSBuild를 사용하고, 해당 소스 편집기는 TextMate 번들을 지원합니다. Xamarin 및 .NET Core 앱에 대해 동일한 디버거 엔진을 사용하고, Xamarin.iOS 및 Xamarin.Android에 대해 동일한 디자이너를 사용합니다.

## <a name="what-can-i-do-in-visual-studio-for-mac"></a>Mac용 Visual Studio에서 무엇을 할 수 있나요?

Mac용 Visual Studio는 다음과 같은 개발 유형을 지원합니다.

- Razor 페이지, JavaScript 및 TypeScript를 위한 C#, F# 및 지원 기능이 있는 ASP.NET Core 웹 애플리케이션
- C# 또는 F#이 있는 .NET Core 콘솔 애플리케이션
- C#이 있는 플랫폼 간 Unity 게임 및 애플리케이션
- C# 또는 F# 및 XAML이 있는 Xamarin의 Android, iOS, tvOS 및 watchOS 애플리케이션
- C# 또는 F#의 Cocoa 데스크톱 앱

이 문서에서는 Mac용 Visual Studio의 다양한 섹션을 살펴보고, 이러한 애플리케이션을 만들기 위한 효과적인 도구를 구성하는 몇 가지 기능을 설명합니다.

## <a name="ide-tour"></a>IDE 둘러보기

Mac용 Visual Studio는 애플리케이션 파일 및 설정 관리, 애플리케이션 코드 작성, 디버깅을 위한 여러 섹션으로 구성되어 있습니다.

## <a name="welcome-screen"></a>시작 화면

Mac용 Visual Studio를 시작하면 ‘시작 화면’이 표시됩니다.**

![시작 화면](media/ide-tour-image1.png)

시작 화면에는 다음 섹션이 포함되어 있습니다.

- **도구 모음** - 검색 창에 빠르게 액세스할 수 있습니다. 솔루션이 로드되면 이 도구 모음을 사용하여 앱 구성을 설정하고, 디버그하고, 오류를 표시합니다.
- **시작** - Mac용 Visual Studio를 시작하는 개발자를 위한 유용한 항목에 빠르게 액세스할 수 있습니다.
- **최근 솔루션** - 최근에 열어 본 솔루션에 빠르게 액세스할 수 있을 뿐 아니라 프로젝트를 열거나 만들 수 있는 편리한 단추가 제공됩니다.
- **개발자 뉴스** - 최신 Microsoft 개발자 정보에 대해 알리는 뉴스 피드입니다.

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

앱에서 사용되는 모든 외부 종속성은 .NET Core 또는 Xamarin.iOS/Xamarin.Android 프로젝트를 사용 중인지에 따라 종속성 또는 패키지 폴더에 저장됩니다. 일반적으로 NuGet의 형태로 제공됩니다.

NuGet은 가장 인기 있는 .NET 개발용 패키지 관리자입니다. Visual Studio의 NuGet 지원을 통해 쉽게 패키지를 검색하고 프로젝트 또는 애플리케이션에 추가할 수 있습니다.

애플리케이션에 종속성을 추가하려면 종속성/패키지 폴더를 마우스 오른쪽 단추로 클릭하고 **패키지 추가**를 선택합니다.

![NuGet 패키지 추가](media/ide-tour-image21.png)

애플리케이션에서 NuGet 패키지를 사용하는 방법에 대한 자세한 내용은 [사용자 프로젝트에 NuGet 프로젝트 포함](/visualstudio/mac/nuget-walkthrough) 문서를 참조하세요.

## <a name="refactoring"></a>리팩터링

Mac용 Visual Studio에서는 코드를 리팩터링하는 두 가지 유용한 방법인 컨텍스트 작업과 소스 분석 기능을 제공합니다. 자세한 내용은 [리팩터링](/visualstudio/mac/refactoring) 문서를 참조하세요.

## <a name="debugging"></a>디버깅

Mac용 Visual Studio에 포함된 네이티브 디버거는 Xamarin.iOS, Xamarin.Mac, Xamarin.Android 애플리케이션에 대한 디버깅을 지원합니다. Mac용 Visual Studio에서는 Mono 소프트 디버거를 사용합니다. 이 디버거는 Mono 런타임에 구현되어, IDE에서 모든 플랫폼의 관리 코드를 디버그할 수 있게 해줍니다. 디버깅에 대한 자세한 내용은 [디버깅](/visualstudio/mac/debugging) 문서를 참조하세요.

디버거에는 문자열, 색, URL, 크기, 좌표, 베지어 곡선 등의 특수 형식에 대한 풍부한 시각화 도우미가 포함되어 있습니다.

디버거의 데이터 시각화에 대한 자세한 내용은 [데이터 시각화](/visualstudio/mac/data-visualizations) 문서를 참조하세요.

## <a name="version-control"></a>버전 제어

Mac용 Visual Studio는 Git 및 Subversion 소스 제어 시스템과 통합됩니다. 소스 제어가 적용되는 프로젝트는 솔루션 이름 옆에 분기가 표시됩니다.

![소스 제어가 적용되는 프로젝트를 나타내는 분기 이름](media/ide-tour-image22.png)

커밋되지 않은 변경 내용이 있는 파일은 다음 이미지와 같이 솔루션 창에서 해당 아이콘에 주석이 있습니다.

![Solution Pad의 커밋되지 않은 파일](media/ide-tour-image23.png)

Visual Studio에서 버전 제어를 사용하는 방법에 대한 자세한 내용은 [버전 제어](/visualstudio/mac/version-control) 문서를 참조하세요.

## <a name="related-video"></a>관련 동영상

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Overview/player]

## <a name="see-also"></a>참조

- [Windows의 Visual Studio IDE](/visualstudio/ide/visual-studio-ide)
