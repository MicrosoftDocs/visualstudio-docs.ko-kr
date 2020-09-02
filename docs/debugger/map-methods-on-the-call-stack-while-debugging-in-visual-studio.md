---
title: 호출 스택의 시각적 맵 만들기 | Microsoft Docs
ms.date: 11/26/2018
ms.topic: how-to
f1_keywords:
- vs.progression.debugwithcodemaps
dev_langs:
- CSharp
- VB
- FSharp
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
ms.assetid: d6a72e5e-f88d-46fc-94a3-1789d34805ef
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2cf0cda942241ca77aa750624b6de25b5ae39391
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85348537"
---
# <a name="create-a-visual-map-of-the-call-stack-while-debugging-c-visual-basic-c-javascript"></a>디버그하는 동안 호출 스택의 시각적 맵 만들기(C#, Visual Basic, C++, JavaScript)

디버깅하는 동안 호출 스택을 시각적으로 추적할 코드 맵을 만듭니다. 맵을 기록해 두면 코드에서 어떤 작업을 하고 있는지 추적하여 버그를 찾는 데 집중할 수 있습니다.

연습은 다음 비디오를 시청하세요. [비디오: 코드 맵 디버거 통합을 사용하여 시각적으로 디버그(Channel 9)](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012Debug-visually-with-Code-Map-debugger-integration)

코드 맵에서 사용할 수 있는 명령 및 작업에 관한 자세한 내용은 [코드 맵 찾아보기 및 다시 정렬](../modeling/browse-and-rearrange-code-maps.md)을 참조하세요.

>[!IMPORTANT]
>[Visual Studio Enterprise Edition](https://visualstudio.microsoft.com/downloads)에서만 코드 맵을 만들 수 있습니다.

다음은 코드 맵을 간략하게 살펴보는 것입니다.

 ![코드 맵의 호출 스택으로 디버그](../debugger/media/debuggermap_overview.png "DebuggerMap_Overview")

## <a name="map-the-call-stack"></a><a name="MapStack"></a> 호출 스택 매핑

1. Visual Studio Enterprise C#, Visual Basic, C++ 또는 JavaScript 프로젝트에서 **디버그** > **디버깅 시작**을 선택하거나 **F5** 키를 눌러 디버깅을 시작합니다.

1. 앱이 중단 모드로 전환되거나 한 단계씩 함수를 실행한 후 **디버그** > **코드 맵**을 선택하거나 **Ctrl**+**Shift**+ **`** 를 누릅니다.

   현재 호출 스택은 새 코드 맵에 주황색으로 표시됩니다.

   ![코드 맵의 호출 스택 참조](../debugger/media/debuggermap_seeundocallstack.png "DebuggerMap_SeeUndoCallStack")

디버깅을 계속할 때 코드 맵이 자동으로 업데이트됩니다. 맵 항목 또는 레이아웃을 변경해도 코드에는 영향을 주지 않습니다. 맵에서 이름 바꾸기, 이동 또는 제거 기능을 자유롭게 사용할 수 있습니다.

항목에 관한 자세한 정보를 보려면 해당 항목을 가리키고 항목의 도구 설명을 확인합니다. 도구 모음에서 **범례**를 선택하여 각 아이콘의 의미를 알아볼 수도 있습니다.

![코드 맵 범례](../debugger/media/debuggermap_showlegend.png "코드 맵 범례")

>[!NOTE]
>코드 맵 위쪽에 있는 **다이어그램이 코드의 이전 버전을 기반으로 할 수 있습니다.** 라는 메시지는 지도를 마지막으로 업데이트한 후 코드가 변경되었을 수 있음을 의미합니다. 예를 들어 맵에 대한 호출이 더 이상 코드에 없는 경우가 있습니다. 메시지를 닫은 다음 맵을 다시 업데이트하기 전에 솔루션 다시 빌드를 시도합니다.

## <a name="map-external-code"></a>맵 외부 코드

기본적으로 맵에는 고유한 코드만 나타납니다. 맵에서 외부 코드를 보려면:

- **호출 스택** 창에서 마우스 오른쪽 단추를 클릭하고 **외부 코드 표시**를 선택합니다.

  ![호출 스택 창을 사용하여 외부 코드 표시](../debugger/media/debuggermap_callstackmenu.png "DebuggerMap_CallStackMenu")
- 또는 Visual Studio **Tools**의 **내 코드만 사용**(또는 **디버그**) > **옵션** > **디버깅**의 선택을 취소합니다.

  ![옵션 대화 상자를 사용하여 외부 코드 표시](../debugger/media/debuggermap_debugoptions.png "DebuggerMap_DebugOptions")

## <a name="control-the-maps-layout"></a>맵 레이아웃 제어

맵 레이아웃을 변경해도 코드에 영향을 미치지 않습니다.

맵 레이아웃을 제어하려면 맵 도구 모음에서 **레이아웃** 메뉴를 선택합니다.

**레이아웃** 메뉴에서 다음을 수행할 수 있습니다.

- 기본 레이아웃을 변경합니다.
- **디버깅 시 자동으로 레이아웃 지정**의 선택을 취소하여 맵을 자동으로 다시 정렬하는 기능을 중지합니다.
- **증분 레이아웃**의 선택을 취소하여 항목을 추가할 때 최소한으로 맵을 다시 정렬합니다.

## <a name="make-notes-about-the-code"></a><a name="MakeNotes"></a> 코드에 대해 메모하기

주석을 추가하여 코드에서 수행되는 작업을 추적할 수 있습니다.

주석을 추가하려면 코드 맵을 마우스 오른쪽 단추로 클릭하고 **편집** > **새 주석**을 선택한 다음, 주석을 입력합니다.

주석에 새 줄을 추가하려면 **Shift**+**Enter**를 누릅니다.

 ![코드 맵의 호출 스택에 주석 추가](../debugger/media/debuggermap_addcomment.png "DebuggerMap_AddComment")

## <a name="update-the-map-with-the-next-call-stack"></a><a name="UpdateMap"></a> 다음 호출 스택과 함께 맵 업데이트

앱을 다음 중단점까지 실행하거나 한 단계씩 함수를 실행하면 맵이 새 호출 스택을 자동으로 추가합니다.

![다음 호출 스택으로 코드 맵 업데이트](../debugger/media/debuggermap_addclearcallstack.png "DebuggerMap_AddClearCallStack")

맵이 새 호출 스택을 자동으로 추가하는 기능을 중지하려면 코드 맵 도구 모음에서 ![코드 맵에 호출 스택을 자동으로 표시](../debugger/media/debuggermap_automaticupdateicon.gif "코드 맵에 호출 스택을 자동으로 표시")를 선택합니다. 맵은 기존 호출 스택을 계속 강조 표시합니다. 맵에 현재 호출 스택을 수동으로 추가하려면 **Ctrl**+**Shift**+ **`** 를 누릅니다.

## <a name="add-related-code-to-the-map"></a><a name="AddRelatedCode"></a> 맵에 관련 코드 추가

이제 C# 또는 Visual Basic에서 맵을 가져왔으므로 필드, 속성 및 기타 메서드 같은 항목을 추가하여 코드에서 수행되는 작업을 추적할 수 있습니다.

코드에서 메서드 정의로 이동하려면 맵에서 메서드를 두 번 클릭하거나, 해당 메서드를 선택하고 **F12** 키를 누르거나, 메서드를 마우스 오른쪽 단추로 클릭하고 **정의로 이동**을 선택합니다.

![코드 맵의 메서드에 대한 코드 정의로 이동](../debugger/media/debuggermap_gotocodedefinition.png "DebuggerMap_GoToCodeDefinition")

추적할 항목을 맵에 추가하려면 메서드를 마우스 오른쪽 단추로 클릭하고 추적할 항목을 선택합니다. 가장 최근 추가된 항목은 녹색으로 표시됩니다.

![호출 스택 코드 맵의 메서드와 관련된 필드](../debugger/media/debuggermap_showedfields.png "DebuggerMap_ShowedFields")

>[!NOTE]
>기본적으로 맵에 항목을 추가하면 클래스, 네임스페이스 및 어셈블리와 같은 부모 그룹 노드도 추가됩니다. 코드 맵 도구 모음에서 **부모 포함** 단추를 선택하거나 항목을 추가하는 동안 **Ctrl** 키를 눌러 이 기능을 켜고 끌 수 있습니다.

![호출 스택 코드 맵의 메서드에서 필드 표시](../debugger/media/debuggermap_showfields.png "DebuggerMap_ShowFields")

더 많은 코드를 보려면 맵 빌드를 계속합니다.

 ![필드를 사용하는 메서드 표시: 호출 스택 코드 맵](../debugger/media/debuggermap_findallreferences.png "DebuggerMap_FindAllReferences")

 ![호출 스택 코드 맵에서 필드를 사용하는 메서드](../debugger/media/debuggermap_foundallreferences.png "DebuggerMap_FoundAllReferences")

## <a name="find-bugs-using-the-map"></a><a name="FindBugs"></a> 맵을 사용하여 버그 찾기
 코드를 시각화하면 버그를 더 빠르게 찾을 수 있습니다. 예를 들어 드로잉 앱에서 버그를 조사한다고 가정하겠습니다. 선을 그렸다가 취소하려는 경우 다른 선을 그릴 때까지 아무 것도 발생하지 않습니다.

 따라서 `clear`, `undo` 및 `Repaint` 메서드에서 중단점을 설정하고, 디버깅을 시작하고, 다음과 같은 맵을 빌드합니다.

 ![코드 맵에 다른 호출 스택 추가](../debugger/media/debuggermap_addpaintobjectcallstack.png "DebuggerMap_AddPaintObjectCallStack")

 `Repaint`를 제외하고 맵 호출 `undo`에 대한 모든 사용자 제스처를 확인할 수 있습니다. `undo`가 즉시 작동하지 않는 이유를 이해할 수 있을 것입니다.

 버그를 수정하고 앱 실행을 계속한 후에 맵은 `undo`의 새 호출을 `Repaint`에 추가합니다.

 ![코드 맵의 호출 스택에 새 메서드 호출 추가](../debugger/media/debuggermap_addnewcallforrepaint.png "DebuggerMap_AddNewCallForRepaint")

## <a name="share-the-map-with-others"></a>다른 사용자와 맵 공유

맵을 내보내고, Microsoft Outlook을 사용하여 다른 사용자에게 보내고, 솔루션에 저장하고, 버전 제어에 체크 인할 수 있습니다.

맵을 공유하거나 저장하려면 코드 맵 도구 모음에서 **공유**를 사용합니다.

![다른 사용자와 호출 스택 코드 맵 공유](../debugger/media/debuggermap_sharewithothers.png "다른 사용자와 호출 스택 코드 맵 공유")

## <a name="see-also"></a>참조
[솔루션 전체의 종속성 매핑](../modeling/map-dependencies-across-your-solutions.md)

[코드 맵을 사용하여 애플리케이션 디버그](../modeling/use-code-maps-to-debug-your-applications.md)

[코드 맵 분석기를 사용하여 잠재적 문제 찾기](../modeling/find-potential-problems-using-code-map-analyzers.md)

[코드 맵 찾아보기 및 다시 정렬](../modeling/browse-and-rearrange-code-maps.md)
