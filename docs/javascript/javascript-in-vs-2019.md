---
title: Visual Studio 2019의 JavaScript 및 TypeScript
ms.date: 03/16/2020
ms.technology: vs-javascript
ms.topic: conceptual
dev_langs:
- JavaScript
- TypeScript
- DHTML
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: '>= vs-2019'
ms.openlocfilehash: 199a27dbfef2b7297563e87d973137e2acd9c745
ms.sourcegitcommit: eef26de3d7a5c971baedbecf3b4941fb683ddb2d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/17/2020
ms.locfileid: "81544291"
---
# <a name="javascript-and-typescript-in-visual-studio-2019"></a>Visual Studio 2019의 JavaScript 및 TypeScript

## <a name="overview"></a>개요

Visual Studio 2019는 JavaScript를 직접 사용할 뿐 아니라 특히 대규모로 프로젝트를 개발하는 경우 생산성과 효율성이 더 높은 JavaScript 개별 환경을 제공하도록 개발된 [TypeScript 프로그래밍 언어](http://www.typescriptlang.org/)를 사용하는 JavaScript 개발을 위한 풍부한 지원을 제공합니다. Visual Studio에서 다양한 애플리케이션 형식 및 서비스의 JavaScript 또는 TypeScript 코드를 작성할 수 있습니다.

## <a name="javascript-language-service"></a>JavaScript 언어 서비스

Visual Studio 2019의 JavaScript 환경은 TypeScript 지원을 제공하는 동일한 엔진으로 구동됩니다. 이 덕분에 향상된 기능 지원, 다양성 및 통합 기능을 즉시 사용할 수 있습니다.

레거시 JavaScript Language Service로 복원하는 옵션은 더 이상 사용할 수 없습니다. 사용자는 이제 새로운 JavaScript Language Service를 즉시 사용할 수 있습니다. 새 언어 서비스는 정적 분석으로 구동되는 TypeScript 언어 서비스만 기반으로 합니다. 이를 통해 향상된 도구를 제공할 수 있으므로, JavaScript 코드에서 형식 정의를 기반으로 하는 더 풍부한 IntelliSense를 활용할 수 있습니다. 새 서비스는 가볍고 레거시 서비스보다 더 적은 메모리를 사용하므로 코드 크기 조정에 따라 더 나은 성능을 제공합니다. 또한 더 큰 프로젝트를 처리하는 언어 서비스의 성능을 개선했습니다.

## <a name="typescript-support"></a>TypeScript 지원

Visual Studio 2019는 TypeScript 컴파일을 프로젝트에 통합하는 다음과 같은 여러 가지 옵션을 제공합니다.

* [TypeScript NuGet 패키지](https://www.nuget.org/packages/Microsoft.TypeScript.MSBuild). TypeScript 3.2 이상용 NuGet 패키지가 프로젝트에 설치되면 해당 버전의 TypeScript 언어 서비스가 편집기에 로드됩니다.
* [TypeScript npm 패키지](https://www.npmjs.com/package/typescript). TypeScript 2.1 이상용 npm 패키지가 프로젝트에 설치되면 해당 버전의 TypeScript 언어 서비스가 편집기에 로드됩니다.
* Visual Studio 설치 관리자에서 기본적으로 제공되고 [VS Marketplace](https://marketplace.visualstudio.com/items?itemName=TypeScriptTeam.typescript-331-vs2017)에서 독립 실행형 SDK 다운로드로 제공되는 TypeScript SDK.

> [!TIP]
> Visual Studio 2019에서 개발된 프로젝트의 경우 다양한 플랫폼과 환경에서 이식성을 높이려면 TypeScript NuGet 또는 TypeScript npm 패키지를 사용하는 것이 좋습니다.

NuGet 패키지의 일반적인 용도 중 하나는 .NET Core CLI를 사용하여 TypeScript를 컴파일하는 것입니다. TypeScript SDK 설치에서 빌드 대상을 가져오도록 프로젝트 파일을 수동으로 편집하지 않는 이상, NuGet 패키지는 `dotnet build` 및 `dotnet publish`와 같은 .NET Core CLI 명령을 사용하여 TypeScript 컴파일을 사용하도록 설정할 유일한 방법입니다.

## <a name="remove-default-imports-aspnet-core-projects"></a>기본값 가져오기 제거(ASP.NET Core 프로젝트)

[SDK 스타일이 아닌 형식](https://docs.microsoft.com/nuget/resources/check-project-format)을 사용하는 이전 프로젝트에서는 몇몇 프로젝트 파일 요소를 제거해야 할 수 있습니다.

프로젝트에서 MSBuild 지원을 위해 NuGet 패키지를 사용하는 경우 프로젝트 파일이 `Microsoft.TypeScript.Default.props` 또는 `Microsoft.TypeScript.targets`를 가져와야 합니다. 파일은 NuGet 패키지가 가져오기 때문에 개별적으로 포함할 경우 의도하지 않은 동작이 발생할 수 있습니다.

1. 프로젝트를 마우스 오른쪽 단추로 클릭하고 **프로젝트 언로드**를 선택합니다.

1. 프로젝트를 마우스 오른쪽 단추로 클릭하고 **편집\<프로젝트 파일 이름\>** 을 선택합니다. 

   프로젝트 파일이 열립니다.

1. `Microsoft.TypeScript.Default.props` 및 `Microsoft.TypeScript.targets`에 대한 참조를 제거합니다.

   제거해야 하는 가져오기는 다음과 비슷하게 표시됩니다.

   ```xml
   <Import
      Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\TypeScript\Microsoft.TypeScript.Default.props"
      Condition="Exists('$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\TypeScript\Microsoft.TypeScript.Default.props')" />

   <Import
      Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\TypeScript\Microsoft.TypeScript.targets"
      Condition="Exists('$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\TypeScript\Microsoft.TypeScript.targets')" />
   ```

## <a name="projects"></a>프로젝트

UWP JavaScript 앱은 Visual Studio 2019에서 더 이상 지원되지 않습니다. JavaScript UWP 프로젝트(확장명이 *.jsproj*인 파일)는 만들거나 열 수 없습니다. Windows에서 제대로 실행되는 [PWA(프로그레시브 웹앱)를 만드는 방법](/microsoft-edge/progressive-web-apps/get-started)에 대한 설명서를 사용하여 자세히 알아볼 수 있습니다.
