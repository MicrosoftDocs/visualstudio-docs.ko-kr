---
title: '방법: 메시지 뷰에서 메시지 검색 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Message Search dialog box
- Messages view
- messages, searching for
ms.assetid: 732b7ccc-54ea-41db-823b-2b96e3e4083e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 37f99c30c23461ada406bb0650f86d45d2a4a2e9
ms.sourcegitcommit: 3fe6bed9ef8fb1478106645f655c7472009ae43a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64832466"
---
# <a name="how-to-search-for-a-message-in-messages-view"></a>방법: 메시지 뷰에서 메시지 검색
메시지 뷰에서 핸들, 유형 또는 메시지 ID를 검색 조건으로 사용하여 특정 메시지를 검색할 수 있습니다. 이러한 항목 중 하나(또는 조합)는 유효한 검색 조건입니다. 검색의 초기 방향을 지정할 수도 있습니다. 대화 상자의 필드에 현재 선택한 메시지의 특성이 미리 로드됩니다.

### <a name="to-search-for-a-message-in-messages-view"></a>메시지 뷰에서 메시지를 검색하려면

1. Spy++와 활성 [메시지 뷰](../debugger/messages-view.md) 창이 보이도록 창을 정렬합니다.

2. **검색** 메뉴에서 **메시지 찾기**를 선택합니다.

    [메시지 검색 대화 상자](../debugger/message-search-dialog-box.md)가 열립니다.

3. **찾기 도구**를 원하는 창 위로 끕니다. 도구를 끌면 **메시지 검색** 대화 상자가 선택한 창의 세부 정보에 표시됩니다.

   - 또는

     검사할 메시지가 있는 창의 핸들이 있으면 **핸들** 텍스트 상자에 입력합니다.

   - 또는

     원하는 메시지 유형 및/또는 메시지 ID를 알고 있는 경우 **유형** 및 **메시지** 드롭다운 메뉴에서 선택하고 **핸들** 텍스트 상자를 지웁니다.

4. 값을 지정하지 않을 필드의 선택을 취소합니다.

   > [!TIP]
   > 화면을 깔끔하게 유지하려면 **Spy 숨기기** 옵션을 선택합니다. 이 옵션을 사용하면 기본 Spy++ 창이 숨겨지고 다른 애플리케이션 상단에 **창 찾기** 대화 상자만 표시되도록 유지됩니다. Spy++ 주 창은 **확인** 또는 **취소**를 클릭하거나 **Spy++ 숨기기** 옵션을 클릭하면 복원됩니다.

5. 검색의 초기 방향으로 **위로** 또는 **아래로**를 선택합니다.

6. **확인**을 클릭합니다.

   일치하는 메시지가 검색되면 메시지 뷰 창에 강조 표시됩니다. [메시지 뷰](../debugger/messages-view.md)를 참조하세요.