---
title: '방법: 특정 목록 인스턴스에 대 한 이벤트 수신기 만들기 | Microsoft Docs'
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, event receivers
- event receivers [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c37da8b798c3b6a0fdc093d5c443584f68b4b5cc
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91585838"
---
# <a name="how-to-create-an-event-receiver-for-a-specific-list-instance"></a>방법: 특정 목록 인스턴스에 대 한 이벤트 수신기 만들기
  목록 인스턴스 이벤트 수신기는 목록 정의의 모든 인스턴스에서 발생 하는 이벤트에 응답 합니다. 이벤트 수신기 템플릿에서 특정 목록 인스턴스를 대상으로 지정할 수는 없지만 목록 정의로 범위가 지정 된 이벤트 수신기를 수정 하 여 특정 목록 인스턴스의 이벤트에 응답할 수 있습니다.

 특정 목록 인스턴스를 대상으로 지정 하려면 이벤트 수신기의 *Elements.xml* 에서를로 바꾸고 `ListTemplateId` `ListUrl` 목록 인스턴스의 URL을 추가 합니다.

## <a name="create-a-list-instance-event-receiver"></a>목록 인스턴스 이벤트 수신기 만들기
 다음 단계에서는 사용자 지정 공지 목록 인스턴스에서 발생 하는 이벤트에만 응답 하도록 목록 항목 이벤트 수신기를 수정 하는 방법을 보여 줍니다.

#### <a name="to-modify-an-event-receiver-to-respond-to-a-specific-list-instance"></a>특정 목록 인스턴스에 응답 하도록 이벤트 수신기를 수정 하려면

1. 브라우저에서 SharePoint 사이트를 엽니다.

2. 탐색 창에서 링크를 **나열** 합니다.

3. **모든 사이트 콘텐츠** 페이지에서 **만들기** 링크를 선택 합니다.

4. **만들기** 대화 상자에서 **알림** 유형을 선택 하 고 알림의 이름을 **testannouncements**로 지정한 다음 **만들기** 단추를 선택 합니다.

5. 에서 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 이벤트 수신기 프로젝트를 만듭니다.

6. **원하는 이벤트 수신기 유형을** 선택 하십시오. 목록에서 **목록 항목 이벤트**를 선택 합니다.

    > [!NOTE]
    > 목록 정의의 범위에 해당 하는 다른 종류의 이벤트 수신기를 선택할 수도 있습니다. 예를 들어 **메일 이벤트** 나열 또는 **워크플로 이벤트 나열**을 선택할 수 있습니다.

7. **이벤트 소스로 사용할 항목** 을 선택 하십시오. 목록에서 **공지**를 선택 합니다.

8. **다음 이벤트 처리** 목록에서 **항목을 추가 하** 고 있습니다. 확인란을 선택한 다음 **마침** 단추를 선택 합니다.

9. **솔루션 탐색기**의 EventReceiver1 아래에서 *Elements.xml*를 엽니다.

     이벤트 수신기가 다음 코드 줄을 사용하여 알림 목록 정의를 현재 참조합니다.

    ```xml
    <Receivers ListTemplateId="104">
    ```

     이 줄을 다음 텍스트로 변경합니다.

    ```xml
    <Receivers ListUrl="Lists/TestAnnouncements">
    ```

     그러면 방금 만든 새 **Testannouncements** 발표 목록에서 발생 하는 이벤트에만 응답 하도록 이벤트 수신기가 전달 됩니다. `ListURL`SharePoint 서버의 목록 인스턴스를 참조 하도록 특성을 변경할 수 있습니다.

10. 이벤트 수신기에 대 한 코드 파일을 열고 ItemAdding 메서드에 중단점을 설정 합니다.

11. **F5** 키를 선택 하 여 솔루션을 빌드하고 실행 합니다.

12. SharePoint의 탐색 창에서 **Testannouncements** 링크를 선택 합니다.

13. **새 알림 추가** 링크를 선택 합니다.

14. 알림의 제목을 입력 한 다음 **저장** 단추를 선택 합니다.

     새 항목이 사용자 지정 공지 목록에 추가 되 면 중단점이 적중 됩니다.

15. 다시 시작 하려면 **F5** 키를 선택 합니다.

16. 탐색 창에서 **목록** 링크를 선택 하 고 **공지** 링크를 선택 합니다.

17. 새 공지를 추가 합니다.

     수신기가 사용자 지정 알림 목록 인스턴스인 **Testannouncements**이벤트에만 응답 하도록 구성 되어 있으므로 이벤트 수신기는 새 알림에서 트리거되지 않습니다.

## <a name="see-also"></a>참고 항목
- [방법: 이벤트 수신기 만들기](../sharepoint/how-to-create-an-event-receiver.md)
- [SharePoint 솔루션 개발](../sharepoint/developing-sharepoint-solutions.md)
