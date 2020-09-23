---
title: 창 뷰에서 창 검색 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- windows, searching in Windows view
ms.assetid: 30306970-b861-4315-acf8-f86a43d4e73b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 880f6ec3ea0882d92f5376859ed629e23781f5f9
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90851972"
---
# <a name="how-to-search-for-a-window-in-windows-view"></a>방법: 창 뷰에서 창 검색
창 뷰에서 핸들, 캡션 텍스트, 클래스 또는 캡션 텍스트와 클래스의 조합을 검색 조건으로 사용하여 특정 창을 검색할 수 있습니다. 검색의 초기 방향을 지정할 수도 있습니다. 대화 상자의 필드에는 창 트리에서 선택한 창의 특성이 표시됩니다.

 클래스 이름 및 제목을 기준으로 데스크톱 수준 창을 식별할 수 있도록, 두 번째 수준으로 확장된(데스크톱의 자식 요소인 모든 창) 트리에서 시작합니다. 데스크톱 수준 창을 선택한 후 해당 수준을 확장하여 특정 자식 창을 찾을 수 있습니다.

### <a name="to-search-for-a-window-in-windows-view"></a>창 뷰에서 창을 검색하려면

1. Spy++와 [창 뷰](../debugger/windows-view.md) 창 및 대상 창이 모두 보이도록 창을 정렬합니다.

2. **검색** 메뉴에서 **창 찾기**를 선택합니다.

    [창 검색 대화 상자](../debugger/window-search-dialog-box.md)가 열립니다.

   > [!TIP]
   > 화면을 깔끔하게 유지하려면 **Spy 숨기기** 옵션을 선택합니다. 이 옵션을 사용하면 기본 Spy++ 창이 숨겨지고 다른 애플리케이션 위에 **창 검색** 대화 상자만 표시되도록 유지됩니다. Spy++ 주 창은 **확인** 또는 **취소**를 클릭하거나 **Spy++ 숨기기** 옵션을 클릭하면 복원됩니다.

3. **찾기 도구**를 대상 창 위로 끕니다. 도구를 끌면 **창 검색** 대화 상자가 선택한 창의 세부 정보에 표시됩니다.

   - 또는

     원하는 창의 핸들(예: 디버거에서)을 알고 있는 경우 **핸들** 상자에 입력하면 됩니다.

   - 또는

     원하는 창의 캡션 텍스트 및/또는 클래스를 알고 있는 경우 **캡션** 및 **클래스** 텍스트 상자에 입력하고 **핸들** 텍스트 상자를 지우면 됩니다.

4. 검색의 초기 방향으로 **위로** 또는 **아래로**를 선택합니다.

5. **확인**을 클릭합니다.

    일치하는 창이 검색되면 [창 뷰](../debugger/windows-view.md) 창에 강조 표시됩니다.