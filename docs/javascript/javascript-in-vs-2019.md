---
title: Visual Studio 2019의 JavaScript 및 TypeScript
titleSuffix: ''
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
ms.openlocfilehash: 6598f018147a025b93ea2e9dd81ae5eceacb4829
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90852467"
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
* Visual Studio 설치 관리자에서 기본적으로 제공되고 [VS Marketplace](https://marketplace.visualstudio.com/items?itemName=TypeScriptTeam.typescript-395)에서 독립 실행형 SDK 다운로드로 제공되는 TypeScript SDK.

> [!TIP]
> Visual Studio 2019에서 개발된 프로젝트의 경우 다양한 플랫폼과 환경에서 이식성을 높이려면 TypeScript NuGet 또는 TypeScript npm 패키지를 사용하는 것이 좋습니다. 자세한 내용은 [NuGet을 사용하여 TypeScript 코드 컴파일](../javascript/compile-typescript-code-nuget.md) 및 [tsc를 사용하여 TypeScript 코드 컴파일](../javascript/compile-typescript-code-npm.md)을 참조하세요.

## <a name="projects"></a>프로젝트

UWP JavaScript 앱은 Visual Studio 2019에서 더 이상 지원되지 않습니다. JavaScript UWP 프로젝트(확장명이 *.jsproj*인 파일)는 만들거나 열 수 없습니다. Windows에서 제대로 실행되는 [PWA(프로그레시브 웹앱)를 만드는 방법](/microsoft-edge/progressive-web-apps/get-started)에 대한 설명서를 사용하여 자세히 알아볼 수 있습니다.
