---
title: 병렬 스레드의 변수에 조사식 설정 | Microsoft Docs
ms.date: 04/25/2017
ms.topic: how-to
f1_keywords:
- vs.debug.parallelwatch
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, parallel watch window
ms.assetid: 28004d9b-420c-48f7-b80e-ab1519802558
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9fb0d5ac60ea5ab89b02a624488b5df4f8a7164b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85348628"
---
# <a name="set-a-watch-on-variables-in-parallel-threads-in-visual-studio-c-visual-basic-c"></a>Visual Studio에서 병렬 스레드의 변수에 조사식 설정(C#, Visual Basic, C++)
병렬 조사식 창에서 한 식이 여러 스레드에서 보유하는 값을 동시에 표시할 수 있습니다. 각 행은 애플리케이션에서 실행 중인 스레드를 나타냅니다. 스레드는 여러 행에 나타날 수도 있습니다. 보다 구체적으로 말하자면, 각 행은 함수 시그니처가 현재 스택 프레임의 함수와 일치하는 함수 호출을 나타냅니다. 열에 있는 항목의 정렬, 순서 변경, 제거 및 그룹화를 수행할 수 있습니다. 스레드에 플래그를 지정하거나 해제할 수 있으며 스레드를 중지(일시 중단)하거나 재개(다시 시작)할 수 있습니다. 다음 열은 **병렬 조사식** 창에 표시됩니다.

- 특히 주의할 스레드를 표시할 수 있는 플래그 열

- 노란색 화살표가 현재 스레드를 나타내는 현재 스레드 열(끝이 굽은 녹색 화살표는 현재가 아닌 스레드에 현재 디버거 컨텍스트가 있음을 나타냄)

- 컴퓨터, 프로세스, 타일, 작업 및 스레드를 표시할 수 있는 구성 가능한 열

  > [!TIP]
  > **병렬 조사식** 창에 작업 정보를 표시하려면 먼저 **작업** 창을 열어야 합니다.

- 조사할 식을 입력할 수 있는 빈 ‘조사식 추가’ 열

  [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-display-the-parallel-watch-window"></a>병렬 조사식 창을 표시하려면

1. 코드에서 중단점을 설정합니다.

2. 메뉴 모음에서 **디버그**, **디버깅 시작**을 차례로 선택합니다. 애플리케이션이 중단점에 도달할 때까지 기다립니다.

3. 메뉴 모음에서 **디버그**, **창**, **병렬 조사식**을 선택한 다음, 조사식 창을 선택합니다. 창을 4개까지 열 수 있습니다.

### <a name="to-add-a-watch-expression"></a>조사식을 추가하려면

- 빈 ‘조사식 추가’ 열 중 하나를 선택한 다음, 조사식을 입력합니다.

### <a name="to-flag-or-unflag-a-thread"></a>스레드에 플래그를 지정하거나 해제하려면

- 행의 플래그 열(첫 번째 열)을 선택하거나 스레드의 바로 가기 메뉴를 열고 **플래그** 또는 **플래그 해제**를 선택합니다.

### <a name="to-display-only-flagged-threads"></a>플래그가 지정된 스레드만 표시하려면

- **병렬 조사식** 창의 왼쪽 위 모퉁이에서 **플래그가 지정된 항목만 표시** 단추를 선택합니다.

### <a name="to-switch-to-another-thread"></a>다른 스레드로 전환하려면

- 현재 스레드 열(두 번째 열)을 두 번 클릭합니다. (키보드: 행을 선택하고 Enter 키를 누릅니다.)

### <a name="to-sort-a-column"></a>열을 정렬하려면

- 열 머리글을 선택합니다.

### <a name="to-group-threads"></a>스레드를 그룹화하려면

- 병렬 조사식 창에 대한 바로 가기 메뉴를 열고 **그룹화 방법**을 선택한 다음, 적절한 하위 메뉴 항목을 선택합니다.

### <a name="to-freeze-or-thaw-threads"></a>스레드를 중지하거나 재개하려면

- 행에 대한 바로 가기 메뉴를 열고 **중지** 또는 **재개**를 선택합니다.

### <a name="to-export-the-data-in-the-parallel-watch-window"></a>병렬 조사식 창에서 데이터를 내보내려면

- **Excel에서 열기** 단추를 선택한 다음, **Excel에서 열기** 또는 **CSV로 내보내기**를 선택합니다.

### <a name="to-filter-by-a-boolean-expression"></a>부울 식을 기준으로 필터링하려면

- **부울 식으로 필터링** 상자에 부울 식을 입력합니다. 디버거는 각 스레드 컨텍스트에 대한 식을 평가합니다. 값이 `true`인 행만 표시됩니다.

## <a name="see-also"></a>참조
- [다중 스레드 애플리케이션 디버그](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [방법: GPU 스레드 창 사용](../debugger/how-to-use-the-gpu-threads-window.md)
- [연습: C++ AMP 애플리케이션 디버깅](/cpp/parallel/amp/walkthrough-debugging-a-cpp-amp-application)