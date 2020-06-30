---
title: 디버깅하는 동안 호출 스택의 맵 메서드
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.progression.debugwithcodemaps
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- call stacks, code maps
- Call Stack window, mapping calls
- debugging [Visual Studio], diagramming the call stack
- call stacks, mapping
- Call Stack window, visualizing
- debugging code visually
- debugging [Visual Studio], mapping the call stack
- call stacks, visualizing
- debugging, code maps
- Call Stack window, tracing calls visually
- Call Stack window, show on code map
- debugging [Visual Studio], tracing the call stack visually
- debugging [Visual Studio], visualizing the call stack
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e1638b16eea9bfa20962359f0b63a7415915d0fc
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85532706"
---
# <a name="map-methods-on-the-call-stack-while-debugging-in-visual-studio"></a>Visual Studio에서 디버깅하는 동안 호출 스택의 맵 메서드

디버깅하는 동안 호출 스택을 시각적으로 추적할 코드 맵을 만듭니다. 맵을 기록해 두면 코드에서 어떤 작업을 하고 있는지 추적하여 버그를 찾는 데 집중할 수 있습니다.

 ![코드 맵의 호출 스택으로 디버그](../debugger/media/debuggermap_overview.png)

 필요한 사항:

 ::: moniker range="vs-2017"

- [Visual Studio Enterprise](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)

::: moniker-end

::: moniker range="vs-2019"

- [Visual Studio Enterprise](https://visualstudio.microsoft.com/downloads)

::: moniker-end

- Visual c #, Visual Basic, c + +, JavaScript 또는 X + +와 같이 디버그할 수 있는 코드

  참조

- [비디오: 코드 맵 디버거 통합으로 시각적으로 디버그 (Channel 9)](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012Debug-visually-with-Code-Map-debugger-integration)

- [호출 스택 매핑](#MapStack)

- [코드에 대 한 정보를 작성 합니다.](#MakeNotes)

- [다음 호출 스택으로 맵 업데이트](#UpdateMap)

- [맵에 관련 코드 추가](#AddRelatedCode)

- [맵을 사용 하 여 버그 찾기](#FindBugs)

- [Q & A](#QA)

  코드 맵으로 작업할 때 사용할 수 있는 명령 및 작업에 대 한 자세한 내용은 [코드 맵 찾아보기 및 다시 정렬](../modeling/browse-and-rearrange-code-maps.md)을 참조 하세요.

## <a name="map-the-call-stack"></a><a name="MapStack"></a> 호출 스택 매핑

1. 디버깅을 시작합니다. (키보드: **F5**)

2. 앱이 중단 모드로 들어가거나 함수를 한 단계씩 실행 한 후 **코드 맵**을 선택 합니다. (키보드: **Ctrl**  +  **Shift**  +  **`** )

     ![호출 스택 매핑을 시작할 코드 맵 선택](../debugger/media/debuggermap_choosecodemap.png)

     현재 호출 스택은 새 코드 맵에 주황색으로 표시됩니다.

     ![코드 맵의 호출 스택 참조](../debugger/media/debuggermap_seeundocallstack.png)

     디버깅하는 동안 맵이 자동으로 업데이트됩니다. [다음 호출 스택으로 맵 업데이트](#UpdateMap)를 참조 하세요.

## <a name="make-notes-about-the-code"></a><a name="MakeNotes"></a> 코드에 대해 메모하기

 코드에서 발생 하는 상황을 추적 하는 주석을 추가 합니다. 주석에서 새 줄을 추가 하려면 **Shift + Return**을 누릅니다.

 ![코드 맵의 호출 스택에 설명 추가](../debugger/media/debuggermap_addcomment.png)

## <a name="update-the-map-with-the-next-call-stack"></a><a name="UpdateMap"></a> 다음 호출 스택과 함께 맵 업데이트

 응용 프로그램을 다음 중단점까지 실행하거나 함수로 한 단계씩 실행합니다. 맵은 새로운 호출 스택을 추가합니다.

 ![다음 호출 스택으로 코드 맵 업데이트](../debugger/media/debuggermap_addclearcallstack.png)

## <a name="add-related-code-to-the-map"></a><a name="AddRelatedCode"></a> 맵에 관련 코드 추가

 이제 지도가 있나요? C # 또는 Visual Basic으로 작업 하는 경우 코드에서 발생 하는 일을 추적 하기 위해 필드, 속성 및 기타 메서드 등의 항목을 추가 합니다.

 메서드를 두 번 클릭하여 코드 정의를 보거나 메서드에 대한 바로 가기 메뉴를 사용합니다. (키보드: 맵에서 메서드를 선택 하 고 **F12**키를 누릅니다.)

 ![코드 맵의 메서드에 대한 코드 정의로 이동](../debugger/media/debuggermap_gotocodedefinition.png)

 맵에서 추적할 항목을 추가합니다.

 ![호출 스택 코드 맵의 메서드에서 필드 표시](../debugger/media/debuggermap_showfields.png)

> [!NOTE]
> 기본적으로 맵에 항목을 추가하면 클래스, 네임스페이스 및 어셈블리와 같은 부모 그룹 노드도 추가됩니다. 이 방법은 유용 하지만 맵 도구 모음에서 **부모 포함** 단추를 사용 하거나 항목을 추가할 때 **CTRL** 키를 눌러이 기능을 해제 하 여 지도를 단순하게 유지할 수 있습니다.

 ![호출 스택 코드 맵의 메서드와 관련된 필드](../debugger/media/debuggermap_showedfields.png)

 여기서 어떤 메서드가 동일한 필드를 사용하는지 쉽게 확인할 수 있습니다. 가장 최근 추가된 항목은 녹색으로 표시됩니다.

 더 많은 코드를 보려면 맵 빌드를 계속합니다.

 ![필드를 사용하는 메서드 표시: 호출 스택 코드 맵](../debugger/media/debuggermap_findallreferences.png)

 ![호출 스택 코드 맵에서 필드를 사용하는 메서드](../debugger/media/debuggermap_foundallreferences.png)

## <a name="find-bugs-using-the-map"></a><a name="FindBugs"></a> 맵을 사용하여 버그 찾기

 코드를 시각화하면 버그를 더 빠르게 찾을 수 있습니다. 예를 들어 그리기 프로그램에서 버그를 조사 하 고 있다고 가정 합니다. 선을 그렸다가 취소하려는 경우 다른 선을 그릴 때까지 아무 것도 발생하지 않습니다.

 따라서 `clear`, `undo` 및 `Repaint` 메서드에서 중단점을 설정하고, 디버깅을 시작하고, 다음과 같은 맵을 빌드합니다.

 ![코드 맵에 다른 호출 스택 추가](../debugger/media/debuggermap_addpaintobjectcallstack.png)

 `Repaint`를 제외하고 맵 호출 `undo`에 대한 모든 사용자 제스처를 확인할 수 있습니다. `undo`가 즉시 작동하지 않는 이유를 이해할 수 있을 것입니다.

 버그를 수정하고 프로그램 실행을 계속한 후에 맵은 `undo`의 새 호출을 `Repaint`에 추가합니다.

 ![코드 맵의 호출 스택에 새 메서드 호출 추가](../debugger/media/debuggermap_addnewcallforrepaint.png)

## <a name="q--a"></a><a name="QA"></a> Q & A

- **모든 호출이 지도에 표시 되는 것은 아닙니다. 굳이?**

   기본적으로 맵에는 고유한 코드만 나타납니다. 외부 코드를 보려면 **호출 스택** 창에서 설정 합니다.

   ![호출 스택 창을 사용하여 외부 코드 표시](../debugger/media/debuggermap_callstackmenu.png)

   또는 Visual Studio 디버깅 옵션에서 **내 코드만 사용** 을 해제 합니다.

   ![옵션 대화 상자를 사용하여 외부 코드 표시](../debugger/media/debuggermap_debugoptions.png)

- **맵을 변경하면 코드에 영향이 있습니까?**

   지도를 변경 해도 코드에는 영향을 주지 않습니다. 맵에서 이름 바꾸기, 이동 또는 제거 기능을 자유롭게 사용할 수 있습니다.

- **"다이어그램은 코드의 이전 버전을 기반으로 할 수 있습니다." 라는 메시지의 의미는 무엇입니까?**

   지도를 마지막으로 업데이트한 후 코드가 변경되었을 수 있습니다. 예를 들어 맵에 대한 호출이 더 이상 코드에 없는 경우가 있습니다. 메시지를 닫은 다음 맵을 다시 업데이트하기 전에 솔루션 다시 빌드를 시도합니다.

- **맵의 레이아웃을 제어 어떻게 할까요?**

   맵 도구 모음에서 **레이아웃** 메뉴를 엽니다.

  - 기본 레이아웃을 변경합니다.

  - 지도를 자동으로 다시 정렬 하지 않으려면 **디버그할 때 자동으로 레이아웃**을 해제 합니다.

  - 항목을 추가할 때 맵을 최대한 적게 다시 정렬 하려면 **증분 레이아웃**을 해제 합니다.

- **다른 사용자와 맵을 공유할 수 있습니까?**

   Microsoft Outlook이 있는 경우 맵을 내보내고 다른 사용자에 게 보낼 수 있으며, 소스 제어로 체크 인할 수 있도록 솔루션에 저장할 수 있습니다.

   ![다른 사용자와 호출 스택 코드 맵 공유](../debugger/media/debuggermap_sharewithothers.png)

- **맵에 새 호출 스택이 자동으로 추가되지 않게 하려면 어떻게 해야 합니까?**

   ![맵 도구 모음에서 코드 맵에 자동으로 호출 스택 표시 &#45; 단추를 선택 ](../debugger/media/debuggermap_automaticupdateicon.gif) 합니다. 맵에 현재 호출 스택을 수동으로 추가하려면 **Ctrl** + **Shift** +  **`** 를 누릅니다.

   디버그 하는 동안 맵은 맵의 기존 호출 스택을 계속 강조 표시 합니다.

- **항목 아이콘 및 화살표는 무슨 의미입니까?**

   항목에 대 한 자세한 정보를 보려면 해당 항목 위로 마우스 포인터를 이동 하 고 항목의 도구 설명을 확인 합니다. **범례** 에서 각 아이콘의 의미를 확인할 수도 있습니다.

   ![호출 스택 코드 맵에 있는 아이콘의 의미](../debugger/media/debuggermap_showlegend.png)

  참조

- [호출 스택 매핑](#MapStack)

- [코드에 대 한 정보를 작성 합니다.](#MakeNotes)

- [다음 호출 스택으로 맵 업데이트](#UpdateMap)

- [맵에 관련 코드 추가](#AddRelatedCode)

- [맵을 사용 하 여 버그 찾기](#FindBugs)

## <a name="see-also"></a>참조

- [솔루션 전체의 종속성 매핑](../modeling/map-dependencies-across-your-solutions.md)
- [코드 맵을 사용하여 애플리케이션 디버그](../modeling/use-code-maps-to-debug-your-applications.md)
- [코드 맵 분석기를 사용하여 잠재적 문제 찾기](../modeling/find-potential-problems-using-code-map-analyzers.md)
- [코드 맵 찾아보기 및 다시 정렬](../modeling/browse-and-rearrange-code-maps.md)
