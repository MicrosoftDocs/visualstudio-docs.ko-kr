---
title: 테스트 탐색기를 사용하여 단위 테스트 디버그
description: Visual Studio에서 테스트 탐색기를 사용하여 단위 테스트를 디버그하는 방법을 알아봅니다.
ms.date: 07/14/2020
ms.topic: how-to
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2def56c6a3860ce0476f448f87bdde25c7970807
ms.sourcegitcommit: a77158415da04e9bb8b33c332f6cca8f14c08f8c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2020
ms.locfileid: "86393546"
---
# <a name="debug-and-analyze-unit-tests-with-test-explorer"></a>테스트 탐색기를 사용하여 단위 테스트 디버그 및 분석

테스트 탐색기를 사용하여 테스트에 대한 디버깅 세션을 시작할 수 있습니다. Visual Studio 디버거에서 코드를 단계별로 실행하면 단위 테스트 및 테스트 중인 프로젝트 간을 앞뒤로 매끄럽게 이동할 수 있습니다. 디버깅을 시작하려면

1. Visual Studio 편집기에서 디버그하려는 하나 이상의 테스트 메서드에서 중단점을 설정합니다.

    > [!NOTE]
    > 테스트 메서드는 순서에 관계 없이 실행할 수 있기 때문에 디버그하려는 모든 테스트 메서드에 중단점을 설정합니다.

::: moniker range="vs-2017"
2. 테스트 탐색기에서 테스트 메서드를 선택한 후 오른쪽 클릭 메뉴에서 **선택한 테스트 디버그**를 선택합니다.
::: moniker-end
::: moniker range=">=vs-2019"
2. 테스트 탐색기에서 테스트 메서드를 선택한 후 오른쪽 클릭 메뉴에서 **디버그**를 선택합니다.

   ![테스트 실행 정보](../test/media/vs-2019/test-explorer-debug.png)
::: moniker-end

   디버거에 대한 자세한 내용은 [Visual Studio에서 디버그](../debugger/debugger-feature-tour.md)를 참조하세요.

## <a name="diagnose-test-method-performance-issues"></a>테스트 메서드 성능 문제 진단

::: moniker range="vs-2017"
테스트 메서드에 너무 많은 시간이 소요되는 이유를 진단하려면 테스트 탐색기에서 메서드를 선택하고 오른쪽 클릭 메뉴에서 **선택한 테스트 프로파일링**을 선택합니다. [계측 프로파일링 보고서](../profiling/understanding-instrumentation-data-values.md?view=vs-2017)를 참조하세요.
::: moniker-end

::: moniker range=">=vs-2019"
테스트 메서드에 너무 많은 시간이 소요되는 이유를 진단하려면 테스트 탐색기에서 메서드를 선택하고 오른쪽 클릭 메뉴에서 **프로필**을 선택합니다. [계측 프로파일링 보고서](../profiling/understanding-instrumentation-data-values.md?view=vs-2017)를 참조하세요.
::: moniker-end

> [!NOTE]
> 해당 기능은 현재 .NET Core에서 지원되지 않습니다.

## <a name="see-also"></a>참조

- [코드 단위 테스트](../test/unit-test-your-code.md)
- [테스트 탐색기를 사용하여 단위 테스트 실행](../test/run-unit-tests-with-test-explorer.md)
- [테스트 탐색기 FAQ](test-explorer-faq.md)
