---
title: Visual Studio Desktop Express 워크로드 및 구성 요소 ID
titleSuffix: ''
description: 작업 및 구성 요소 ID를 사용하여 명령줄로 Visual Studio를 설치하거나 VSIX 매니페스트에서 종속성으로 지정합니다.
keywords: ''
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.date: 11/13/2018
ms.topic: reference
helpviewer_keywords:
- workload ID, Visual Studio
- component ID, Visual Studio
- install Visual Studio, administrator guide
ms.assetid: a3c0cc76-e3ce-435c-a1af-a6318b5a4dbe
ms.prod: visual-studio-windows
ms.technology: vs-installation
monikerRange: vs-2017
ms.openlocfilehash: 3db18da6e09b3206d81f5600d54700f912a411e8
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76113912"
---
# <a name="visual-studio-desktop-express-component-directory"></a>Visual Studio Desktop Express 구성 요소 디렉터리

이 페이지의 표에는 명령줄을 사용하여 Visual Studio를 설치하는 데 사용할 수 있는 ID 또는 VSIX 매니페스트에서 종속성으로 지정할 수 있는 ID가 나열되어 있습니다. Visual Studio에 대한 업데이트를 릴리스할 때 추가 구성 요소가 추가될 것입니다.

또한 이 페이지에 대해 다음 사항에 유의하세요.

* 각 작업에는 고유한 섹션 및 작업 ID와 해당 작업에 사용할 수 있는 구성 요소 표가 있습니다.
* 기본적으로 **필수** 구성 요소는 작업을 설치할 때 설치됩니다.
* 원하는 경우 **권장** 및 **선택적** 구성 요소를 설치할 수도 있습니다.
* 작업과 관련이 없는 추가 구성 요소를 나열하는 섹션도 추가했습니다.

VSIX 매니페스트에 종속성을 설정하는 경우 구성 요소 ID만 지정해야 합니다. 이 페이지의 표를 사용하여 최소 구성 요소 종속성을 확인합니다. 일부 시나리오에서는 작업에서 하나의 구성 요소만 지정한다고 의미할 수 있습니다. 다른 시나리오에서는 단일 작업에서 여러 구성 요소를 지정하거나 여러 작업에서 여러 구성 요소를 지정한다고 의미할 수 있습니다. 자세한 내용은 [방법: 확장성 프로젝트를 Visual Studio 2017로 마이그레이션](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md) 페이지를 참조하세요.

이러한 ID를 사용하는 방법에 대한 자세한 내용은 [명령줄 매개 변수를 사용하여 Visual Studio 2017 설치](use-command-line-parameters-to-install-visual-studio.md) 페이지를 참조하세요. 다른 제품의 작업 및 구성 요소 ID 목록은 [Visual Studio 2017 작업 및 구성 요소 ID](workload-and-component-ids.md) 페이지를 참조하세요.

## <a name="express-for-windows-desktop"></a>Express for Windows Desktop

**ID:** Microsoft.VisualStudio.Workload.WDExpress

**설명:** 구문 인식 코드 편집, 소스 코드 제어, 작업 항목 관리로 WPF, WinForms, Win32 같은 네이티브 및 관리 애플리케이션을 빌드합니다. C#, Visual Basic, Visual C++에 대한 지원이 포함됩니다.

### <a name="components-included-by-this-workload"></a>이 작업에 포함되는 구성 요소

구성 요소 ID | 속성 | 버전 | 종속성 유형
--- | --- | --- | ---
Microsoft.Component.ClickOnce | ClickOnce 게시 도구 | 15.8.27825.0 | 필수
Microsoft.Component.HelpViewer | 도움말 뷰어 | 15.6.27323.2 | 필수
Microsoft.Component.MSBuild | MSBuild | 15.7.27520.0 | 필수
Microsoft.Component.VC.Runtime.OSSupport | UWP용 Visual C++ 런타임 | 15.6.27406.0 | 필수
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 타기팅 팩 | 15.6.27406.0 | 필수
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 타기팅 팩 | 15.6.27406.0 | 필수
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 타기팅 팩 | 15.6.27406.0 | 필수
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.6.27406.0 | 필수
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 타기팅 팩 | 15.6.27406.0 | 필수
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 타기팅 팩 | 15.6.27406.0 | 필수
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 타기팅 팩 | 15.6.27406.0 | 필수
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | .NET Framework 4.6.1 개발 도구 | 15.8.27825.0 | 필수
Microsoft.Net.ComponentGroup.TargetingPacks.Common | .NET Framework 4 – 4.6 개발 도구 | 15.6.27406.0 | 필수
Microsoft.VisualStudio.Component.Common.Azure.Tools | 연결 및 게시 도구 | 15.9.28107.0 | 필수
Microsoft.VisualStudio.Component.CoreEditor | Visual Studio 핵심 편집기 | 15.8.27729.1 | 필수
Microsoft.VisualStudio.Component.EntityFramework | Entity Framework 6 도구 | 15.6.27406.0 | 필수
Microsoft.VisualStudio.Component.NuGet | NuGet 패키지 관리자 | 15.9.28016.0 | 필수
Microsoft.VisualStudio.Component.Roslyn.Compiler | C# 및 Visual Basic Roslyn 컴파일러 | 15.6.27309.0 | 필수
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# 및 Visual Basic | 15.8.27729.1 | 필수
Microsoft.VisualStudio.Component.SQL.ADAL | SQL ADAL 런타임 | 15.6.27406.0 | 필수
Microsoft.VisualStudio.Component.SQL.CLR | SQL Server용 CLR 데이터 형식 | 15.0.26208.0 | 필수
Microsoft.VisualStudio.Component.SQL.CMDUtils | SQL Server 명령줄 유틸리티 | 15.0.26208.0 | 필수
Microsoft.VisualStudio.Component.SQL.DataSources | SQL Server 지원용 데이터 원본 | 15.0.26621.2 | 필수
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | SQL Server Express 2016 LocalDB | 15.7.27617.1 | 필수
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | 15.0.26208.0 | 필수
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | 15.9.28107.0 | 필수
Microsoft.VisualStudio.Component.Static.Analysis.Tools | 정적 분석 도구 | 15.0.26208.0 | 필수
Microsoft.VisualStudio.Component.TextTemplating | 텍스트 템플릿 변환 | 15.0.26208.0 | 필수
Microsoft.VisualStudio.Component.VC.CLI.Support | C++/CLI 지원 | 15.6.27309.0 | 필수
Microsoft.VisualStudio.Component.VC.Tools.ARM | ARM용 Visual C++ 컴파일러 및 라이브러리 | 15.8.27825.0 | 필수
Microsoft.VisualStudio.Component.VC.Tools.ARM64 | ARM64용 Visual C++ 컴파일러 및 라이브러리 | 15.9.28230.55 | 필수
Microsoft.VisualStudio.Component.VisualStudioData | 데이터 원본 및 서비스 참조 | 15.6.27406.0 | 필수
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Windows 10 SDK(10.0.14393.0) | 15.6.27406.0 | 필수
Microsoft.VisualStudio.Component.Windows10SDK.17134 | Windows 10 SDK(10.0.17134.0) | 15.8.27924.0 | 필수

## <a name="unaffiliated-components"></a>독립적 구성 요소

이러한 구성 요소는 작업에 포함되지 않지만 개별 구성 요소로 선택할 수 있습니다.

구성 요소 ID | 속성 | 버전
--- | --- | ---
해당 없음 | 해당 없음 | 해당 없음

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>참고 항목

* [Visual Studio 작업 및 구성 요소 ID](workload-and-component-ids.md)
* [Visual Studio 관리자 가이드](visual-studio-administrator-guide.md)
* [명령줄 매개 변수를 사용하여 Visual Studio 설치](use-command-line-parameters-to-install-visual-studio.md)
  * [명령줄 매개 변수 예](command-line-parameter-examples.md)
* [Visual Studio의 오프라인 설치 만들기](create-an-offline-installation-of-visual-studio.md)
