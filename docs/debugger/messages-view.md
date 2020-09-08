---
title: 메시지 뷰 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.externaltools.spyplus.messagesview
helpviewer_keywords:
- Messages view
ms.assetid: 14c2a786-c23a-4b2d-acad-8c32a856c70d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6b20ed28518c9156e82c6fe75ecceda74c66615d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62845856"
---
# <a name="messages-view"></a>메시지 뷰
각 창에는 연결된 메시지 스트림이 있습니다. 메시지 뷰 창에 이 메시지 스트림이 표시됩니다. 창 핸들, 메시지 코드 및 메시지가 표시됩니다. 스레드 또는 프로세스를 위한 메시지 뷰도 만들 수 있습니다. 이렇게 하면 특정 프로세스나 스레드에서 소유하는 모든 창에 전송된 메시지를 볼 수 있으며, 창 초기화 메시지를 캡처하는 데 특히 유용합니다.

 일반적인 메시지 뷰 창이 아래에 나와 있습니다. 첫 번째 열은 창 핸들을 포함하고 두 번째 열은 메시지 코드([메시지 코드](../debugger/message-codes.md) 참조)를 포함합니다. 디코딩된 메시지 매개 변수 및 반환 값은 오른쪽에 있습니다.

 ![Spy&#43;&#43; 메시지 뷰](../debugger/media/spy--_messagesview.png "Spy++_MessagesView") Spy++ 메시지 뷰

## <a name="procedures"></a>절차

#### <a name="to-open-a-messages-view-for-a-window-process-or-thread"></a>창, 프로세스 또는 스레드의 메시지 뷰를 열려면

1. 포커스를 [창 뷰](../debugger/windows-view.md), [프로세스 뷰](../debugger/processes-view.md) 또는 [스레드 뷰](../debugger/threads-view.md) 창으로 이동합니다.

2. 검토할 메시지를 포함하는 항목의 노드를 찾아 선택합니다.

3. **Spy** 메뉴에서 **로그 메시지**를 선택합니다.

     [메시지 옵션 대화 상자](../debugger/message-options-dialog-box.md)가 열립니다.

4. 표시할 메시지의 옵션을 선택합니다.

5. **확인**을 눌러 메시지 로깅을 시작합니다.

     메시지 뷰 창이 열리고 **메시지** 메뉴가 Spy++ 도구 모음에 추가됩니다. 선택한 옵션에 따라 메시지가 활성 메시지 뷰 창으로 스트리밍을 시작합니다.

6. 메시지가 충분하면 **메시지** 메뉴에서 **로깅 중지**를 선택합니다.

## <a name="in-this-section"></a>섹션 내용
 [메시지 뷰 제어](../debugger/how-to-control-messages-view.md) 메시지 뷰를 관리하는 방법을 설명합니다.

 [창 찾기에서 메시지 뷰 열기](../debugger/how-to-open-messages-view-from-find-window.md) 창 찾기 대화 상자에서 메시지 뷰를 여는 방법을 설명합니다.

 [메시지 뷰에서 메시지 검색](../debugger/how-to-search-for-a-message-in-messages-view.md) 메시지 뷰에서 특정 메시지를 찾는 방법을 설명합니다.

 [메시지 로그 표시 시작 및 중지](../debugger/how-to-start-and-stop-the-message-log-display.md) 메시지 로깅을 시작 및 중지하는 방법을 설명합니다.

 [메시지 코드](../debugger/message-codes.md) 메시지 뷰에 나열되는 메시지의 코드를 정의합니다.

 [메시지 속성 표시](../debugger/how-to-display-message-properties.md) 메시지에 대한 자세한 정보를 표시하는 방법입니다.

## <a name="related-sections"></a>관련 단원
 [Spy++ 뷰](../debugger/spy-increment-views.md) 창, 메시지, 프로세스 및 스레드의 Spy++ 트리 뷰에 대해 설명합니다.

 [Spy++ 사용](../debugger/using-spy-increment.md) Spy++ 도구를 소개하고 해당 도구를 사용할 수 있는 방법에 대해 설명합니다.

 [메시지 옵션 대화 상자](../debugger/message-options-dialog-box.md) 활성 메시지 뷰에 나열되는 메시지를 선택하는 데 사용됩니다.

 [메시지 검색 대화 상자](../debugger/message-search-dialog-box.md) 메시지 뷰에서 특정 메시지의 노드를 찾는 데 사용됩니다.

 [메시지 속성 대화 상자](../debugger/message-properties-dialog-box.md) 메시지 뷰에서 선택한 메시지의 속성을 표시하는 데 사용됩니다.

 [Spy++ 참조](../debugger/spy-increment-reference.md) 각 Spy++ 메뉴 및 대화 상자에 대해 설명하는 단원이 있습니다.