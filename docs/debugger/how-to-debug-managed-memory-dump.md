---
title: .NET 진단 분석기를 사용하여 관리되는 메모리 덤프 디버그 | Microsoft Docs
description: Visual Studio의 .NET 진단 분석기를 사용하여 관리되는 메모리 덤프를 분석하는 방법을 알아봅니다.
ms.custom: SEO-VS-2021
ms.date: 04/21/2021
ms.topic: how-to
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- analyzers
- dump debugging
- debugging managed memory dump
- debugging [Visual Studio]
author: poppastring
ms.author: madownie
manager: andster
monikerRange: '>= vs-2019'
ms.workload:
- multiple
ms.openlocfilehash: 083095ad534aa6b9131ba103178313cb1cdc4b7c
ms.sourcegitcommit: 925db7adb9cb554b081c7e727d09680d4863feed
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/24/2021
ms.locfileid: "107953066"
---
# <a name="how-to-debug-a-managed-memory-dump-with-net-diagnostic-analyzers"></a>.NET 진단 분석기를 사용하여 관리되는 메모리 덤프를 디버그하는 방법



이 자습서에서는 다음을 수행합니다.

> [!div class="checklist"]
> * 메모리 덤프 열기
> * 덤프에 대해 분석기 선택 및 실행
> * 분석기 결과 검토
> * 문제 코드로 이동


이 문서에 설명된 예제에서는 요청에 제때 응답하지 않는 사용자 앱이 문제입니다. 


## <a name="opening-a-memory-dump-in-visual-studio"></a>Visual Studio에서 메모리 덤프 열기

1. **파일 > 열기 > 파일** 메뉴 명령을 사용하여 Visual Studio에서 메모리 덤프를 열고 메모리 덤프를 선택합니다.

1. 메모리 덤프 요약 페이지에서 **진단 분석 실행** 이라는 새 **작업** 을 확인합니다.

   ![작업 - 진단 분석](../debugger/media/diagnostic-analyzer-dump-summary-actions.png)

1. 이 작업을 선택하여 디버거를 시작하고 새 **진단 분석** 페이지를 엽니다. 이 페이지에는 기본 증상에 따라 구성된 사용 가능한 분석기 옵션 목록이 있습니다.


## <a name="select-and-execute-analyzers-against-the-dump"></a>덤프에 대해 분석기 선택 및 실행

해당 증상을 조사하기 위한 최선의 옵션은 이 예제의 문제에 가장 잘 부합하는 **프로세스 응답성** 에서 사용할 수 있습니다.

   ![진단 분석기 선택](../debugger/media/diagnostic-analyzer-diagnostics-analysis-window.png)

1. **분석** 단추를 클릭하여 조사 프로세스를 시작합니다. 

1. 분석기는 메모리 덤프에서 캡처된 프로세스 정보와 CLR 데이터의 조합에 따라 결과를 표시합니다.
 
## <a name="review-the-results-of-the-analyzers"></a>분석기 결과 검토

1. 이 경우 분석기는 두 개의 오류를 발견했습니다. 분석기 결과를 선택하여 **분석 요약** 및 제안된 **수정** 을 확인합니다.

   ![진단 분석기 결과](../debugger/media/diagnostic-analyzer-diagnostics-analysis-results.png)

1. **분석 요약** 에는 “CLR 스레드 풀에 고갈이 발생하고 있습니다.”라고 나와 있습니다. 이 정보는 현재 CLR이 사용 가능한 모든 스레드 풀 스레드를 사용했음을 나타냅니다. 즉, 스레드가 해제될 때까지 사용자 서비스는 새 요청에 응답할 수 없습니다.

    > [!NOTE] 
    > 이 경우 **수정** 은 “Do not synchronously wait on Monitors, Events, Task, or any other objects that may block your thread. See if you can update the method to be asynchronous.”(모니터, 이벤트, 작업 또는 스레드를 차단할 수 있는 기타 모든 개체를 동기적으로 대기하지 않습니다. 메서드를 비동기로 업데이트할 수 있는지 확인하세요.)입니다.

## <a name="navigating-to-the-problematic-code"></a>문제 코드로 이동

다음 작업은 문제 코드를 찾는 것입니다.

1. **호출 스택 표시** 링크를 클릭하면 Visual Studio는 이 동작을 표시하는 스레드로 즉시 전환됩니다.

1. **호출 스택** 창에는 프레임워크 코드(System.)에서 사용자 코드(SyncOverAsyncExmple.)를 빠르게 구별할 수 있는 메서드가 표시됩니다.

   ![진단 분석기의 호출 스택 링크](../debugger/media/diagnostic-analyzer-call-stack.png)

1. 각 호출 스택 프레임은 하나의 메서드에 해당하며, 스택 프레임을 두 번 클릭하면 Visual Studio는 이 스레드에서 해당 시나리오로 직접 연결된 코드로 이동합니다.

1. 이 예제에서는 기호나 코드가 없지만 **기호가 로드되지 않음** 페이지에서 **[소스 코드 디컴파일](../debugger/decompilation.md)** 옵션을 선택할 수 있습니다.

   ![디컴파일](../debugger/media/diagnostic-analyzer-decompilation.png)

1. 아래 디컴파일된 소스에서 비동기 작업(ConsumeThreadPoolThread)이 동기 차단 함수를 호출하고 있음을 분명히 알 수 있습니다.

    > [!NOTE]  
    > WaitHandle.WaitOne 메서드를 포함하는 “DoSomething()” 메서드는 신호를 받을 때까지 현재 스레드 풀 스레드를 차단합니다.

   앱 응답성을 높이려면 모든 비동기 컨텍스트에서 동기 코드 차단을 제거하는 것이 중요합니다.

   ![디컴파일된 코드 분석](../debugger/media/diagnostic-analyzer-decompiled-code.png)


## <a name="see-also"></a>추가 정보

* [디버거에서 덤프 파일 사용](../debugger/using-dump-files.md)
* [디버깅 중에 .NET 어셈블리에서 소스 코드 생성](../debugger/decompilation.md)
* [기호 파일(.pdb) 및 원본 파일 지정](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
