---
title: 방법 - 찾기 도구 사용 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Window Finder Tool
ms.assetid: 5841926b-08c3-4e43-88bd-4223d04f9aef
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7833502c1f36adb654ecc4cc4d3b4dfb742a85b8
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2020
ms.locfileid: "85348732"
---
# <a name="how-to-use-the-finder-tool"></a>방법: 찾기 도구 사용
**창 찾기**의 찾기 도구를 사용하여 창 속성 또는 메시지를 표시할 수 있습니다. 또한 찾기 도구는 사용할 수 없는 자식 창을 찾을 수 있으며 사용할 수 없는 자식 창이 겹치는 경우 강조 표시할 창을 파악할 수 있습니다.

 ![Spy&#43;&#43; 창 찾기 대화 상자](../debugger/media/icon_spy--_find.png "Icon_Spy++_Find") 창 찾기 대화 상자의 찾기 도구

 위의 그림은 아래 3단계 이후의 창 찾기 대화 상자를 보여 줍니다.

### <a name="to-display-window-properties-or-messages"></a>창 속성 또는 메시지를 표시하려면

1. Spy++와 대상 창이 모두 보이도록 창을 정렬합니다.

2. **Spy** 메뉴에서 **창 찾기**를 선택합니다.

    [창 찾기 대화 상자](../debugger/find-window-dialog-box.md)가 열립니다.

3. **찾기 도구**를 대상 창 위로 끕니다.

    도구를 끌면 **창 찾기** 대화 상자가 선택한 창의 세부 정보에 표시됩니다.

   - 또는

     검사할 창의 핸들(예: 디버거에서 복사한 항목)이 있으면 **핸들** 텍스트 상자에 입력합니다.

   > [!TIP]
   > 화면을 깔끔하게 유지하려면 **Spy 숨기기** 옵션을 선택합니다. 이 옵션을 사용하면 기본 Spy++ 창이 숨겨지고 다른 애플리케이션 상단에 **창 찾기** 대화 상자만 표시되도록 유지됩니다. Spy++ 주 창은 **확인** 또는 **취소**를 클릭하거나 **Spy++ 숨기기** 옵션을 클릭하면 복원됩니다.

4. **표시**에서 **속성** 또는 **메시지**를 선택합니다.

5. **확인**을 누릅니다.

    **속성**을 선택한 경우 [창 속성 대화 상자](../debugger/window-properties-dialog-box.md)가 열립니다. **메시지**를 선택한 경우 [메시지 뷰](../debugger/messages-view.md) 창이 열립니다.

## <a name="see-also"></a>참조
- [Spy++ 뷰](../debugger/spy-increment-views.md)
- [Spy++ 사용](../debugger/using-spy-increment.md)
- [Spy++ 참조](../debugger/spy-increment-reference.md)