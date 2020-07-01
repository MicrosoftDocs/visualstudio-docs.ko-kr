---
title: 디버거에서 GPU 스레드 보기 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.debug.gputthreads
- vs.debug.gputhreads
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, GPU threads window
ms.assetid: c647c502-a9f0-48e0-a430-976744a5fa51
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cbbb49a1017fb0bc65300f3c16050db4954e1103
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2020
ms.locfileid: "85348719"
---
# <a name="how-to-use-the-gpu-threads-window-c"></a>방법: GPU 스레드 창 사용(C++)
GPU 스레드 창에서 디버깅 중인 애플리케이션의 GPU에서 실행되는 스레드를 검사하고 관련 작업을 수행할 수 있습니다. GPU에서 실행되는 애플리케이션에 대한 자세한 내용은 [C++ AMP 개요](/cpp/parallel/amp/cpp-amp-overview)를 참조하세요.

 GPU 스레드 창에는 각 행이 모든 열에서 값이 동일한 GPU 스레드의 집합을 나타내는 테이블이 포함되어 있습니다. 열에 있는 항목의 정렬, 순서 변경, 제거 및 그룹화를 수행할 수 있습니다. GPU 스레드 창에서 스레드에 플래그를 지정하거나 해제할 수 있으며 스레드를 중지(일시 중단)하거나 재개(다시 시작)할 수 있습니다. 다음과 같은 열이 GPU 스레드 창에 표시됩니다.

- 특히 주의할 스레드를 표시할 수 있는 플래그 열

- 현재 스레드 열 - 노란색 화살표는 현재 스레드를 나타냅니다.

- **스레드 수** 열 - 스레드 수를 동일한 위치에 표시합니다.

- **줄** 열 - 각 스레드 그룹이 위치한 코드 줄을 표시합니다.

- **주소** 열 - 각 스레드 그룹이 위치한 명령 주소를 표시합니다. 기본적으로 이 열은 숨겨집니다.

- **위치** 열 - 소스 코드의 위치를 표시합니다.

- **상태** 열 - 스레드가 활성화되어 있는지, 차단되어 있는지, 시작되지 않았는지 또는 완료되었는지를 표시합니다.

- **타일** 열 - 행의 스레드에 대한 타일 인덱스를 표시합니다.

  테이블의 머리글은 표시되고 있는 타일과 스레드를 보여 줍니다.

  [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-display-the-gpu-threads-window"></a>GPU 스레드 창을 표시하려면

1. **솔루션 탐색기**에서 프로젝트의 바로 가기 메뉴를 열고 **속성**을 선택합니다.

2. 프로젝트의 **속성 페이지** 창에 있는 **구성 속성** 아래에서 **디버깅**을 선택합니다.

3. **실행할 디버거** 목록에서 **로컬 Windows 디버거**를 선택합니다. **디버거 형식** 목록에서 **GPU 전용**을 선택합니다. GPU에서 실행되는 코드의 중단점에서 중단하려면 이 디버거를 선택해야 합니다.

4. **확인** 단추를 선택합니다.

5. GPU 코드에서 중단점을 설정합니다.

6. 메뉴 모음에서 **디버그**, **디버깅 시작**을 차례로 선택합니다. 애플리케이션이 중단점에 도달할 때까지 기다립니다.

7. 메뉴 모음에서 **디버그**, **Windows**, **GPU 스레드**를 선택합니다.

### <a name="to-switch-to-a-different-thread"></a>다른 스레드로 전환하려면

- 열을 두 번 클릭합니다. (키보드: 행을 선택하고 Enter 키를 선택합니다.)

### <a name="to-display-a-particular-tile-and-thread"></a>특정 타일 및 스레드를 표시하려면

1. GPU 스레드 창에서 **스레드 전환기 확장** 단추를 선택합니다.

2. 텍스트 상자에 타일 및 스레드 값을 입력합니다.

3. 위에 화살표가 있는 단추를 선택합니다.

### <a name="to-display-or-hide-a-column"></a>열을 표시하거나 숨기려면

- GPU 스레드 창에 대한 바로 가기 메뉴를 열고 **열**을 선택한 다음, 표시하거나 숨기려는 열을 선택합니다.

### <a name="to-sort-by-a-column"></a>열을 기준으로 정렬하려면

- 열 머리글을 선택합니다.

### <a name="to-group-threads"></a>스레드를 그룹화하려면

- GPU 스레드 창에 대한 바로 가기 메뉴를 열고 **그룹화 방법**을 선택한 다음, 표시된 열 이름 중 하나를 선택합니다. 스레드의 그룹을 해제하려면 **없음**을 선택합니다.

### <a name="to-freeze-or-thaw-a-row-of-threads"></a>스레드의 행을 중지하거나 재개하려면

- 행에 대한 바로 가기 메뉴를 열고 **중지** 또는 **재개**를 선택합니다.

### <a name="to-flag-or-unflag-a-row-of-threads"></a>스레드의 행에 플래그를 지정하거나 해제하려면

- 스레드의 플래그 열을 선택하거나 스레드에 대한 바로 가기 메뉴를 열고 **플래그** 또는 **플래그 해제**를 선택합니다.

### <a name="to-display-only-flagged-threads"></a>플래그가 지정된 스레드만 표시하려면

- GPU 스레드 창에서 플래그 단추를 선택합니다.

## <a name="see-also"></a>참조
- [다중 스레드 애플리케이션 디버그](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [방법: 병렬 조사식 창 사용](../debugger/how-to-use-the-parallel-watch-window.md)
- [연습: C++ AMP 애플리케이션 디버깅](/cpp/parallel/amp/walkthrough-debugging-a-cpp-amp-application)