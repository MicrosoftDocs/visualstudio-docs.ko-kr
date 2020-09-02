---
title: '방법: Office 프로젝트에서 이벤트 처리기 만들기'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Basic [Office development in Visual Studio], event handlers
- event handlers [Office development in Visual Studio]
- Visual C# [Office development in Visual Studio], event handlers
- events [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ee85d89dcb990cebd595dadbd7b28add4a7b371a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85538309"
---
# <a name="how-to-create-event-handlers-in-office-projects"></a>방법: Office 프로젝트에서 이벤트 처리기 만들기
  Visual Basic 및 c #에서 이벤트 처리기를 만드는 방법에는 여러 가지가 있습니다. 디자인 뷰에서 컨트롤을 두 번 클릭 하 여 컨트롤에 대 한 기본 이벤트 처리기를 만들거나 **속성** 창의 이벤트 창을 사용 하 여 컨트롤의 모든 이벤트에 대 한 처리기를 만들 수 있습니다. 그러나 코드 보기에 있는 경우 디자인 뷰로 전환 하 여 이벤트 처리기를 만들 수 없습니다.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-create-an-event-handler-in-visual-basic"></a>Visual Basic에서 이벤트 처리기를 만들려면

1. 코드 편집기 위쪽의 **클래스 이름** 드롭다운 목록에서 이벤트 처리기를 만들려는 개체를 선택 합니다.

    > [!NOTE]
    > 또는에 대 한 이벤트 처리기를 만들려는 `ThisDocument` 경우 `ThisWorkbook` **클래스 이름** 드롭다운 목록에서 **(ThisDocument 이벤트)** 또는 **(ThisWorkbook 이벤트)** 를 선택 해야 합니다.

2. 코드 편집기 위쪽의 **메서드 이름** 드롭다운 목록에서 이벤트를 선택 합니다.

     Visual Studio에서 이벤트 처리기를 만들고 새로 만든 이벤트 처리기로 삽입 지점을 이동 합니다. 이벤트 처리기가 이미 있으면 삽입 지점은 기존 이벤트 처리기로 이동 합니다.

### <a name="to-create-an-event-handler-in-c"></a>C에서 이벤트 처리기를 만들려면\#

1. 정규화 된 이벤트 이름 뒤에 공백을 입력 한 다음 나중에 공백을 사용 하 여를 입력 하 여 클래스의 **시작** 이벤트에서 이벤트 대리자를 만듭니다 **+=** . 예를 들면 다음과 같습니다.

     `this.<object name>.<event name> +=`

2. 코드 줄의 끝에서 TAB 키를 두 번 누릅니다.

     Visual Studio는 자동으로 코드 줄을 완성 하 고, 이벤트 처리기를 만들고, 새로 만든 이벤트 처리기로 삽입 지점을 이동 합니다.

## <a name="see-also"></a>추가 정보
- [Office 솔루션에서 코드 작성](../vsto/writing-code-in-office-solutions.md)
- [연습: NamedRange 컨트롤의 이벤트에 대 한 프로그래밍](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)
- [Office 솔루션 빌드](../vsto/building-office-solutions.md)
