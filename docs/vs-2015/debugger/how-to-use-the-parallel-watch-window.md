---
title: '방법: 병렬 조사식 창 사용 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.parallelwatch
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, parallel watch window
ms.assetid: 28004d9b-420c-48f7-b80e-ab1519802558
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 734a55cb06ee46afc6fc3518d6dffe349690d3d7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697486"
---
# <a name="how-to-use-the-parallel-watch-window"></a>방법: 병렬 조사식 창 사용
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

병렬 조사식 창에서 한 식이 여러 스레드에서 보유하는 값을 동시에 표시할 수 있습니다. 각 행은 애플리케이션에서 실행 중인 스레드를 나타냅니다. 스레드는 여러 행에 나타날 수도 있습니다. 보다 구체적으로 말하자면, 각 행은 함수 시그니처가 현재 스택 프레임의 함수와 일치하는 함수 호출을 나타냅니다. 열에 있는 항목의 정렬, 순서 변경, 제거 및 그룹화를 수행할 수 있습니다. 스레드에 플래그를 지정하거나 해제할 수 있으며 스레드를 중지(일시 중단)하거나 재개(다시 시작)할 수 있습니다. 다음 열은 **병렬 조사식** 창에 표시됩니다.  
  
- 특히 주의할 스레드를 표시할 수 있는 플래그 열  
  
- 화살표가 선택된 프레임을 나타내는 프레임 열  
  
- 컴퓨터, 프로세스, 타일, 작업 및 스레드를 표시할 수 있는 구성 가능한 열  
  
  > [!TIP]
  > 병렬 **조사식** 창에 작업 정보를 표시 하려면 **병렬 작업** 창을 열어야 합니다.  
  
- **\<Add Watch>** 조사할 식을 입력할 수 있는 열입니다.  
  
  [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-display-the-parallel-watch-window"></a>병렬 조사식 창을 표시하려면  
  
1. 코드에서 중단점을 설정합니다.  
  
2. 메뉴 모음에서 **디버그**, **디버깅 시작**을 차례로 선택합니다. 애플리케이션이 중단점에 도달할 때까지 기다립니다.  
  
3. 메뉴 모음에서 **디버그**, **창**, **병렬 조사식**을 선택한 다음, 조사식 창을 선택합니다. 창을 4개까지 열 수 있습니다.  
  
### <a name="to-add-a-watch-expression"></a>조사식을 추가하려면  
  
- **\<Add Watch>** 조사식 식을 선택 하 고 지정 합니다.  
  
### <a name="to-flag-or-unflag-a-thread"></a>스레드에 플래그를 지정하거나 해제하려면  
  
- 행에 대 한 플래그 열을 선택 하거나 스레드에 대 한 바로 가기 메뉴를 열고 **플래그** 또는 플래그 **해제를 선택**합니다.  
  
### <a name="to-display-only-flagged-threads"></a>플래그가 지정된 스레드만 표시하려면  
  
- **병렬 조사식** 창의 왼쪽 위 모퉁이에서 플래그가 지정 된 항목만 표시 단추를 선택 합니다.  
  
### <a name="to-switch-frames"></a>프레임을 전환하려면  
  
- 프레임 열을 두 번 클릭합니다. (키보드: 행을 선택하고 Enter 키를 누릅니다.)  
  
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
  
## <a name="see-also"></a>관련 항목  
 [다중 스레드 응용 프로그램 디버그](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [방법: GPU 스레드 창 사용](../debugger/how-to-use-the-gpu-threads-window.md)   
 [연습: C++ AMP 애플리케이션 디버깅](https://msdn.microsoft.com/library/40e92ecc-f6ba-411c-960c-b3047b854fb5)
