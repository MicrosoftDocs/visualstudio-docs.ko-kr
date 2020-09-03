---
title: '방법: 스레드 창 사용 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.threads
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- threading [Visual Studio], debugging
- Thread.Name property
- debugger, Threads window
- SetThreadName function
- Threads window
- '@TIB'
- debugging [Visual Studio], threads
ms.assetid: adfbe002-3d7b-42a9-b42a-5ac0903dfc25
caps.latest.revision: 48
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: da41524fcb231ea399dbbd2a2904afd935e5c4f8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "67824250"
---
# <a name="how-to-use-the-threads-window"></a>방법: 스레드 창 사용
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**스레드** 창에서 디버깅 중인 응용 프로그램의 스레드를 검사 하 고 작업할 수 있습니다.  
  
 **스레드** 창에는 각 행이 응용 프로그램의 스레드를 나타내는 테이블이 있습니다. 기본적으로 이 테이블에는 애플리케이션의 모든 스레드가 나열되지만 목록을 필터링하여 관심 있는 스레드만 표시할 수 있습니다. 열마다 다른 유형의 정보가 있습니다. 일부 열을 숨길 수도 있습니다. 모든 열을 표시하면 왼쪽부터 다음 정보가 나타납니다.  
  
- 플래그 열 - 주의해야 할 스레드에 표시할 수 있습니다. 스레드에 플래그를 지정 하는 방법에 대 한 자세한 내용은 [방법: 스레드 플래그 지정 및](../debugger/how-to-flag-and-unflag-threads.md)플래그 해제를 참조 하세요.  
  
- 활성 스레드 열 - 노란색 화살표는 활성 스레드를 나타냅니다. 화살표의 윤곽선은 실행이 중단되고 디버거가 실행된 스레드를 나타냅니다.  
  
- **Id** 열에는 각 스레드의 id 번호가 포함 되어 있습니다.  
  
- 관리 되는 스레드의 관리 되는 ID 번호를 포함 하는 **관리 되는 id** 열입니다.  
  
- 사용자 인터페이스 스레드, 원격 프로시저 호출 처리기 또는 작업자 스레드로 스레드를 분류 하는 **범주** 열입니다. 특정 범주는 애플리케이션의 주 스레드를 식별합니다.  
  
- 이름 **열-** 각 스레드를 이름 (있는 경우) 또는로 식별 \<No Name> 합니다.  
  
- **위치** 열-스레드가 실행 되는 위치를 표시 합니다. 이 위치를 확장하여 스레드의 전체 호출 스택을 표시할 수 있습니다.  
  
- **우선** 순위 열-시스템에서 각 스레드에 할당 한 우선 순위 또는 우선 순위를 포함 합니다.  
  
- **선호도 마스크** 열-일반적으로 숨겨진 고급 열입니다. 이 열에는 각 스레드에 대한 프로세서 선호도 마스크가 표시됩니다. 다중 프로세서 시스템에서는 선호도 마스크에 따라 스레드가 실행될 수 있는 프로세서가 결정됩니다.  
  
- 일시 **중단 된 횟수 열-** 일시 중단 된 횟수를 포함 합니다. 이 횟수에 따라 스레드를 실행할 수 있는지 여부가 결정됩니다. 일시 중단 횟수에 대한 설명은 이 항목의 뒷부분에 나오는 "스레드 중지 및 재개"를 참조하십시오.  
  
- **프로세스 이름** 열-각 스레드가 속한 프로세스를 포함 합니다. 이 열은 여러 프로세스를 디버깅하는 경우에 유용하지만 일반적으로 숨겨져 있습니다.  
  
### <a name="to-display-the-threads-window-in-break-mode-or-run-mode"></a>중단 모드나 실행 모드에서 스레드 창을 표시하려면  
  
- **디버그** 메뉴에서 **창**을 가리킨 다음 **스레드**를 클릭 합니다.  
  
### <a name="to-display-or-hide-a-column"></a>열을 표시하거나 숨기려면  
  
- **스레드** 창의 맨 위에 있는 도구 모음에서 **열**을 클릭 한 다음 표시 하거나 숨기려는 열의 이름을 선택 하거나 선택 취소 합니다.  
  
### <a name="to-switch-the-active-thread"></a>활성 스레드를 전환하려면  
  
- 다음 단계 중 하나를 수행합니다.  
  
  - 스레드를 두 번 클릭합니다.  

  - 스레드를 마우스 오른쪽 단추로 클릭 하 고 **스레드로 전환을**클릭 합니다.  

    노란색 화살표가 새 활성 스레드 옆에 나타납니다. 화살표의 회색 윤곽선은 실행이 중단되고 디버거가 실행된 스레드를 나타냅니다.  
  
## <a name="grouping-and-sorting-threads"></a>스레드 그룹화 및 정렬  
 스레드를 그룹화하면 테이블에 각 그룹의 제목이 나타납니다. 제목에는 "작업자 스레드" 또는 "플래그가 해제된 스레드" 등의 그룹 설명과 트리 컨트롤이 포함됩니다. 각 그룹의 멤버 스레드가 그룹 제목 아래에 나타납니다. 그룹에 대한 멤버 스레드를 숨기려면 트리 컨트롤을 사용하여 그룹을 축소합니다.  
  
 그룹화가 정렬보다 우선하기 때문에 예를 들어 스레드를 범주별로 그룹화한 다음 각 범주 내의 ID로 정렬할 수 있습니다.  
  
#### <a name="to-sort-threads"></a>스레드를 정렬하려면  
  
1. **스레드** 창의 맨 위에 있는 도구 모음에서 열의 맨 위에 있는 단추를 클릭 합니다.  
  
     이제 해당 열의 값으로 스레드가 정렬됩니다.  
  
2. 정렬 순서를 역순으로 바꾸려면 동일한 단추를 다시 클릭합니다.  
  
     목록 맨 위에 나타난 스레드가 이제 맨 아래에 나타납니다.  
  
#### <a name="to-group-threads"></a>스레드를 그룹화하려면  
  
- **스레드** 창 도구 모음에서 **그룹화** 방법 목록을 클릭 하 고 스레드를 그룹화 할 조건을 클릭 합니다.  
  
#### <a name="to-sort-threads-within-groups"></a>그룹 내에서 스레드를 정렬하려면  
  
1. **스레드** 창의 맨 위에 있는 도구 모음에서 **그룹화** 방법 목록을 클릭 하 고 스레드를 그룹화 할 조건을 클릭 합니다.  
  
2. **스레드** 창에서 열의 맨 위에 있는 단추를 클릭 합니다.  
  
     이제 해당 열의 값으로 스레드가 정렬됩니다.  
  
#### <a name="to-expand-or-collapse-all-groups"></a>모든 그룹을 확장하거나 축소하려면  
  
- **스레드** 창의 맨 위에 있는 도구 모음에서 **그룹 확장** 또는 **그룹 축소**를 클릭 합니다.  
  
## <a name="searching-for-specific-threads"></a>특정 스레드 검색  
 [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]에서 지정된 문자열과 일치하는 스레드를 검색할 수 있습니다. **스레드** 창에서 스레드를 검색 하면 모든 열에서 검색 문자열과 일치 하는 모든 스레드가 창에 표시 됩니다. 이 정보에는 **위치** 열에서 호출 스택의 맨 위에 표시 되는 스레드 위치가 포함 됩니다. 그러나 기본적으로 전체 호출 스택이 검색되지는 않습니다.  
  
#### <a name="to-search-for-specific-threads"></a>특정 스레드를 검색하려면  
  
- **스레드** 창의 맨 위에 있는 도구 모음에서 **검색** 상자로 이동하고 다음을 수행합니다.  
  
  - 검색 문자열을 입력하고 Enter 키를 누릅니다.  

    \- 또는 -  

  - **검색** 상자 옆의 드롭다운 목록을 클릭 하 고 이전 검색에서 검색 문자열을 선택 합니다.  
  
- (선택 사항) 검색에 전체 호출 스택을 포함하려면 **호출 스택 검색**을 선택합니다.  
  
## <a name="freezing-and-thawing-threads"></a>스레드 중지 및 재개  
 스레드를 중지하면 리소스를 사용할 수 있어도 스레드 실행이 시작되지 않습니다.  
  
 네이티브 코드에서 Windows 함수를 호출 하 여 스레드를 일시 중단 하거나 다시 시작할 수 있으며, `SuspendThread` `ResumeThread` 또는 MFC 함수 [Cwinthread:: SuspendThread](https://msdn.microsoft.com/library/57189c7e-fd71-42e5-bc4b-3de7cd373d28) 및 [cwinthread:: ResumeThread](https://msdn.microsoft.com/library/d6f97a2f-5c9f-4ee1-b978-d74938784db5)를 호출할 수 있습니다. 또는를 호출 하는 경우 `SuspendThread` `ResumeThread` **스레드** 창에 표시 되는 *일시 중단 된 횟수*를 변경 합니다. 그러나 네이티브 스레드를 중지하거나 재개하는 경우에는 일시 중단된 횟수를 변경하지 않습니다. 네이티브 코드에서는 스레드가 재개되고 일시 중단된 횟수가 0인 경우 이외에는 스레드를 실행할 수 없습니다.  
  
 관리 코드에서는 스레드를 중지하거나 재개하면 일시 중단된 횟수가 변경됩니다. 관리 코드에서는 중지된 스레드의 일시 중단된 횟수가 1입니다. 네이티브 코드에서 중지된 스레드의 일시 중단된 횟수는 0입니다. 단, `SuspendThread` 호출로 인해 스레드가 일시 중단된 경우는 예외입니다.  
  
> [!NOTE]
> 네이티브 코드에서 관리 코드로의 호출을 디버깅할 때 관리 코드는 이를 호출한 네이티브 코드와 동일한 실제 스레드에서 실행됩니다. 네이티브 스레드를 일시 중단하거나 중지하면 관리 코드도 중지됩니다.  
  
#### <a name="to-freeze-or-thaw-execution-of-a-thread"></a>스레드 실행을 중지하거나 재개하려면  
  
- **스레드** 창의 맨 위에 있는 도구 모음에서 **스레드 중지** 또는 **스레드 재개**를 클릭 합니다.  
  
     이 동작은 **스레드** 창에서 선택되는 스레드에만 적용됩니다.  
  
## <a name="displaying-flagged-threads"></a>플래그가 지정된 스레드 표시  
 **스레드** 창에서 아이콘으로 스레드를 표시하여 특별한 주의가 필요한 스레드에 플래그를 설정할 수 있습니다. 자세한 내용은 [방법: 스레드 플래그 지정 및](../debugger/how-to-flag-and-unflag-threads.md)플래그 해제를 참조 하세요. 스레드 창에서 모든 스레드를 표시하거나 플래그가 지정된 스레드만 표시하도록 선택할 수 있습니다.  
  
#### <a name="to-display-only-flagged-threads"></a>플래그가 지정된 스레드만 표시하려면  
  
- **스레드** 창의 왼쪽 위 모퉁이에서 플래그 단추를 선택 합니다.  
  
## <a name="displaying-thread-call-stacks-and-switching-between-frames"></a>스레드 호출 스택 표시 및 프레임 간 전환  
 다중 스레드 프로그램에서 각 스레드에는 자신의 고유한 호출 스택이 있습니다. **스레드** 창을 사용하여 편리하게 이러한 스택을 볼 수 있습니다.  
  
#### <a name="to-view-the-call-stack-of-a-thread"></a>스레드의 호출 스택을 보려면  
  
- **위치** 열에서 스레드 위치 옆의 반전 된 삼각형을 클릭 합니다.  
  
     위치가 확장되어 스레드의 전체 호출 스택이 표시됩니다.  
  
#### <a name="to-view-or-collapse-the-call-stacks-of-all-threads"></a>모든 스레드의 호출 스택을 보거나 축소하려면  
  
- **스레드** 창의 맨 위에 있는 도구 모음에서 **호출 스택 확장** 또는 **호출 스택 축소**를 클릭 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [다중 스레드 응용 프로그램 디버그](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [연습: 다중 스레드 애플리케이션 디버그](../debugger/walkthrough-debugging-a-multithreaded-application.md)
