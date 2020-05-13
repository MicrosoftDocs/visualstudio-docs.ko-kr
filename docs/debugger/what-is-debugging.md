---
title: 디버깅이란 무엇인가요?
description: 앱을 디버그 하는 것을 이해합니다
ms.custom: debug-experiment
ms.date: 10/17/2018
ms.topic: conceptual
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c01317f3b8fa92cf1bc17c3745f708e0d3f26e5b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62901233"
---
# <a name="what-is-debugging"></a>디버깅이란 무엇인가요?

Visual Studio 디버거는 강력한 도구입니다. 사용방법을 설명하기 전에, *디버그*,*디버깅* 그리고 *디버그 모드*와 같은 용어에 대해 각각 무엇인지 알아보겠습니다. 이러한 방법으로 나중에 버그를 찾고 수정하는 것에 대해서 다룰 때도 동일한 작업을 하게 될 것 입니다.

## <a name="debugger-vs-debugging"></a>디버깅 및 디버거

*디버깅*은 수많은 의미를 뜻하고 있습니다. 그러나 문자 그대로, 대부분의 코드에서 버그를 잡아내는 역할을 수행합니다. 자,이렇게 할 수 있는 방법은 여러가지가 있습니다. 예를 들어, 오타를 찾는 코드를 스캔하여 디버깅할 수 있으며, 또는 코드 분석기를 사용할 수도 있습니다. 성능 프로파일러를 사용하여 코드를 디버그할 수도 있습니다. 또는 *디버거*를 사용하여 디버그를 할 수 있습니다.

디버거는 실행 중인 앱에 접근하여 코드를 검사할 수 있도록 도와주는 매우 전문화된 개발 도구입니다. Visual Studio의 디버깅 설명서에 일반적으로 "디버깅"이라고 말할 때 이러한 의미를 갖습니다.

## <a name="debug-mode-vs-running-your-app"></a>디버그 모드 및 앱 실행

처음으로 Visual Studio에서 앱을 실행하는 경우 도구 ![모음에서](../debugger/media/dbg-tour-start-debugging.png " 녹색") 화살표 단추(또는 **F5**)를 눌러 시작할 수 있습니다. 기본적으로 **디버그** 값은 왼쪽 드롭다운 목록에 표시됩니다. Visual Studio를 처음 접하는 경우에는 앱 디버깅이 앱 실행과 관련이 있다는 느낌을 받을 수 있습니다. 그러나 기본적으로 두 가지는 매우 다른 작업입니다.

![디버그 빌드를 선택 합니다.](../debugger/media/what-is-debugging-debug-build.png)

**디버그** 값은 디버그 구성을 나타냅니다. 앱을 시작하는 경우 (녹색 화살표 또는 **F5**를 눌러) 디버그 구성에서 *디버그 모드*를 시작할 수 있습니다. 이렇게 하면 앱에서 버그를 찾는 데 사용할 수 있는 디버깅 기능 집합들이 활성화됩니다.

프로젝트가 열려 있는 경우 **디버그**라고 표시된 드롭다운 선택기를 선택하고 대신 **릴리스**를 선택하세요.

![릴리스 빌드를 선택 합니다.](../debugger/media/what-is-debugging-release-build.png)

이 설정을 전환하면 프로젝트가 디버그 구성에서 릴리스 구성으로 변경됩니다. Visual Studio 프로젝트에는 사용하는 프로그램에 대한 별도의 릴리스 및 디버그 구성이 있습니다. 디버깅을 위한 디버그 버전과 최종 릴리스 배포를 위한 릴리스 버전을 빌드할 수 있습니다. 릴리스 빌드는 성능에 최적화되어 있지만 디버깅에는 디버그 빌드가 더 좋습니다

## <a name="when-to-use-a-debugger"></a>디버거를 사용 하는 경우

디버거는 버그를 찾고 수정하기 위한 필수적인 도구입니다. 그러나 상황에 적합해야 하며, 버그나 오류를 신속하게 해결할 수 있는 모든 도구를 활용하는 것이 중요합니다. 때로는 올바른 "도구"가 더 나은 코딩 방법일 수 있습니다. 디버거와 다른 도구를 언제 사용해야 되는지를 학습함으로써, 여러분은 디버거를 보다 효과적으로 사용하는 방법도 배울 수 있습니다.

## <a name="next-steps"></a>다음 단계

이 문서에서는 몇 가지 일반적인 디버깅 개념을 알아보았습니다. 다음으로 Visual Studio로 디버그하는 방법과 어떻게 코드에서 버그를 줄일 수 있는가에 대해 학습합니다. 다음 문서에서는 C# 코드 예제를 보여 주지만 이 개념은 Visual Studio에서 지원하는 모든 언어에 적용됩니다.

> [!div class="nextstepaction"]
> [완전 초보자를 위한 디버깅](../debugger/debugging-absolute-beginners.md)

> [!div class="nextstepaction"]
> [디버깅 기술 및 도구](../debugger/write-better-code-with-visual-studio.md)
