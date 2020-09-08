---
title: 디버깅이란 무엇인가요?
description: 앱을 디버그한다는 것의 의미를 알아봅니다.
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62901233"
---
# <a name="what-is-debugging"></a>디버깅이란 무엇인가요?

Visual Studio 디버거는 강력한 도구입니다. 이 도구를 사용하는 방법을 보여 주기 전에 ‘디버거’, ‘디버깅’, ‘디버그 모드’ 등 몇 가지 용어에 대해 설명하려고 합니다.    이렇게 하면 나중에 버그 찾기 및 수정에 대해 다룰 때 동일한 내용에 대해 이야기할 것입니다.

## <a name="debugger-vs-debugging"></a>디버거 및 디버깅 비교

‘디버깅’이라는 용어는 여러 다양한 것을 의미할 수 있지만 대부분의 경우 코드에서 버그를 제거하는 것을 의미합니다.  현재 이 작업을 수행하는 방법은 여러 가지가 있습니다. 예를 들어 오타를 찾는 코드를 검사하거나 코드 분석기를 사용하여 디버그할 수 있습니다. 성능 프로파일러를 사용하여 코드를 디버그할 수도 있습니다. 또는 ‘디버거’를 사용하여 디버그할 수 있습니다. 

디버거는 실행 중인 앱에 연결되며 코드를 검사할 수 있는 매우 특수한 개발자 도구입니다. Visual Studio의 디버깅 설명서에서 “디버깅”이라고 할 때의 일반적인 의미는 이와 같습니다.

## <a name="debug-mode-vs-running-your-app"></a>디버그 모드 및 앱 실행 비교

Visual Studio에서 처음 앱을 실행하는 경우 도구 모음에서 녹색 화살표 단추(![디버깅 시작](../debugger/media/dbg-tour-start-debugging.png "디버깅 시작"))를 누르거나 **F5**를 눌러 시작할 수 있습니다. 기본적으로 **디버그** 값은 왼쪽의 드롭다운에 표시됩니다. Visual Studio를 처음 사용하는 경우라면 이로 인해 앱 디버그와 앱 실행이 서로 관련이 있다는 인상을 받을 수 있습니다. 두 작업이 실제 서로 관련이 있기는 하지만 기본적으로 두 작업은 서로 매우 다른 작업입니다.

![디버그 빌드 선택](../debugger/media/what-is-debugging-debug-build.png)

**디버그** 값은 디버그 구성을 나타냅니다. 디버그 구성에서 앱을 시작하면(녹색 화살표 또는 **F5** 키를 누름) ‘디버그 모드’로 앱을 시작합니다. 즉, 디버거가 연결된 앱을 실행하는 것입니다.  이렇게 하면 전체 디버깅 기능을 사용할 수 있으므로 앱에서 버그를 찾는 데 도움이 됩니다.

프로젝트가 열려 있는 경우에는 **디버그**라고 표시된 드롭다운 선택기를 선택하고 그렇지 않은 경우에는 **릴리스**를 선택합니다.

![릴리스 빌드 선택](../debugger/media/what-is-debugging-release-build.png)

이 설정을 전환하면 디버그 구성에서 릴리스 구성으로 프로젝트를 변경하는 것입니다. Visual Studio 프로젝트에는 사용하는 프로그램에 대한 별도의 릴리스 및 디버그 구성이 있습니다. 디버그 버전은 디버깅용으로 빌드하고 릴리스 버전은 최종 릴리스 배포용으로 빌드합니다. 성능에 최적화되어 있는 것은 릴리스 빌드이나 디버그하는 데 더 적합한 것은 디버그 빌드입니다.

## <a name="when-to-use-a-debugger"></a>디버거를 사용하는 경우

디버거는 앱에서 버그를 찾고 수정하는 데 사용되는 필수 도구입니다. 하지만 컨텍스트가 가장 중요하며, 버그 또는 오류를 신속하게 제거하는 데 도움이 되는 모든 도구를 원하는 대로 활용하는 것이 중요합니다. 경우에 따라 적절한 “도구”가 코딩을 사용하는 것보다 더 나은 방법이 될 수 있습니다. 디버거를 사용하는 경우와 다른 도구를 사용하는 경우를 비교하여 알아두면 디버거를 더 효과적으로 사용하는 방법도 알 수 있습니다.

## <a name="next-steps"></a>다음 단계

이 문서에서는 몇 가지 일반적인 디버깅 개념을 알아보았습니다. 다음으로는 Visual Studio를 사용하여 디버그하는 방법과 버그가 적은 코드를 작성하는 방법을 알아볼 수 있습니다. 다음 문서에서는 C# 코드 예제를 보여 주지만 개념은 Visual Studio에서 지원하는 모든 언어에 적용됩니다.

> [!div class="nextstepaction"]
> [완전 초보자를 위한 디버깅](../debugger/debugging-absolute-beginners.md)

> [!div class="nextstepaction"]
> [디버깅 기술 및 도구](../debugger/write-better-code-with-visual-studio.md)
