---
title: Visual Studio Tools for Unity | Microsoft Docs
description: Unity를 사용한 플랫폼 간 게임 및 앱 개발을 지원하는 무료 Visual Studio 확장 기능인 Visual Studio Tools for Unity의 개요를 확인합니다.
ms.custom: ''
ms.date: 10/25/2019
ms.technology: vs-unity-tools
ms.prod: visual-studio-dev16
ms.topic: overview
ms.assetid: 6cabc626-5310-4622-a743-210a9abb5535
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: ee4e9e0dc9df4eb5decb3fc9c2afb0411e9cb75c
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93405389"
---
# <a name="visual-studio-tools-for-unity"></a>Visual Studio Tools for Unity
![Visual Studio Tools for Unity](../media/hero.png)

## <a name="overview"></a>개요
Visual Studio Tools for Unity는 Visual Studio를 Unity를 사용한 플랫폼 간 게임 및 앱 개발을 위한 효과적인 도구로 전환하는 무료 Visual Studio 확장 기능입니다.

Unity 편집기는 게임 세계를 하나로 통합하는 데 탁월하지만, 편집기에서 코드를 작성할 수는 없습니다. Visual Studio Tools for Unity를 사용하면 Visual Studio의 친숙한 코드 편집, 디버깅 및 생산성 기능을 통해 C#을 사용하여 Unity 프로젝트에 대한 편집기 및 게임 스크립트를 만들 수 있으며, Visual Studio의 강력한 디버깅 기능을 사용하여 디버그할 수 있습니다.

하지만 Visual Studio Tools for Unity는 그 이상의 기능을 제공합니다. Unity 편집기와의 긴밀한 통합으로 단순한 작업을 수행하며 앞뒤로 전환하는 시간을 줄이고, Unity 특정 생산성 향상 기능을 제공하고, 필요할 때면 언제든지 Unity 설명서를 볼 수 있게 도와줍니다.

### <a name="compatible-with-visual-studio-community-on-windows-and-macos-and-bundled-with-unity"></a>Windows 및 macOS의 Visual Studio Community와 호환되며 Unity와 함께 제공됨
Visual Studio 및 Mac용 Visual Studio Community는 무료로 제공되며 Unity 설치와 함께 제공됩니다. 설치 및 설정에 대한 자세한 내용은 Visual Studio Tools for Unity [시작 설명서](getting-started-with-visual-studio-tools-for-unity.md)를 참조하세요.

## <a name="intellisense-for-unity-messages"></a>Unity 메시지에 대한 IntelliSense
IntelliSense 코드 완성을 사용하면 해당 매개 변수를 포함하여 `OnCollisionEnter`와 같은 [Unity API 메시지를 빠르고 쉽게 구현](using-visual-studio-tools-for-unity.md#intellisense-for-unity-api-messages)할 수 있습니다.

![OnCollisionEnter를 보여 주는 IntelliSense 대화 상자](../media/vs/intellisense-example.png)

## <a name="superior-debugging"></a>탁월한 디버깅
Visual Studio Tools for Unity는 Visual Studio만의 강력한 [디버깅](using-visual-studio-tools-for-unity.md#unity-debugging) 기능을 지원합니다.

* 조건부 중단점을 포함하는 중단점을 설정합니다.
* 조사식 창에서 복잡한 식을 평가합니다.
* 변수 및 인수 값을 조사하고 수정합니다.
* 복잡한 개체 및 데이터 구조로 드릴다운합니다.

![변수를 검사하는 중단점에서 중지됨](../media/vs/debugging-inspecting.png)

## <a name="integrated-suggestions-for-best-practices-and-performance-insights"></a>모범 사례 및 성능 인사이트에 대한 통합된 제안
Unity 프로젝트에 대한 Visual Studio의 깊은 이해를 바탕으로 모범 사례를 캡처하는 향상된 코드를 작성합니다.

![CompareTag를 사용한 VS 리팩터링 문자열 비교](../media/vs/unity-diagnostics.png)

## <a name="codelens-support-for-unity-scripts-and-messages"></a>Unity 스크립트 및 메시지에 대한 CodeLens 지원
Unity 스크립트 및 메시지 함수는 Unity에서 제공하는 내용과 코드의 내용을 더 쉽게 인식할 수 있도록 힌트로 데코레이트됩니다.

 ![Unity 스크립트 및 Unity 메시지에 대한 CodeLens 힌트를 보여 주는 새 스크립트](../media/vs/codelens-support.png)

> [!NOTE]
> CodeLens 지원은 Visual Studio 2019에서 사용할 수 있습니다.

## <a name="optimized-view-of-all-your-scripts-to-match-unity"></a>Unity와 일치하는 모든 스크립트의 최적화된 보기
UPE(Unity 프로젝트 탐색기)는 표준 솔루션 탐색기에서 프로젝트 파일을 볼 수 있는 또 다른 방법입니다. UPE는 표시되는 파일을 필터링하고 Unity와 일치하는 계층 구조에 표시합니다(Visual Studio 2019의 **보기 > Unity 프로젝트 탐색기**).

![Unity 프로젝트 탐색기](../media/vs/unity-project-explorer.png)

> [!NOTE]
> Unity 프로젝트 탐색기는 Visual Studio 2019에서 사용할 수 있습니다. Mac용 Visual Studio의 Solution Pad는 기본적으로 Unity 프로젝트에 대해 유사한 동작을 포함하며, 추가적인 뷰가 필요하지 않습니다.

* [Visual Studio Tools for Unity 시작](getting-started-with-visual-studio-tools-for-unity.md)
