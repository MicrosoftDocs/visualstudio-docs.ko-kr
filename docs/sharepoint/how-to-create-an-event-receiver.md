---
title: '방법: 이벤트 수신기 만들기 | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.SPE.EventReceiver
dev_langs:
- VB
- CSharp
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
ms.openlocfilehash: 26d8c9f433fad051716b6ebd37e3d1f3b3f9f4eb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86016928"
---
# <a name="how-to-create-an-event-receiver"></a>방법: 이벤트 수신기 만들기
  *이벤트 수신기*를 만들면 사용자가 목록 또는 목록 항목과 같은 SharePoint 항목을 조작할 때 응답할 수 있습니다. 예를 들어 사용자가 일정을 변경 하거나 연락처 목록에서 이름을 삭제할 때 이벤트 수신기의 코드를 트리거할 수 있습니다. 이 항목을 따라 목록 인스턴스에 이벤트 수신기를 추가 하는 방법을 배울 수 있습니다.

 이러한 단계를 완료 하려면 설치 되어 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 있고 지원 되는 버전의 Windows 및 SharePoint가 있어야 합니다. 이 예제에는 SharePoint 프로젝트가 필요 하므로 [연습: 사이트 열, 콘텐츠 형식 및 sharepoint 용 목록 만들기](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)항목의 절차를 완료 해야 합니다.

## <a name="adding-an-event-receiver"></a>이벤트 수신기 추가
 [연습: SharePoint 용 사이트 열, 콘텐츠 형식 및 목록 만들기](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) 에서 만든 프로젝트에는 사용자 지정 사이트 열, 사용자 지정 목록 및 콘텐츠 형식이 포함 되어 있습니다. 다음 절차에서는 목록과 같은 SharePoint 항목에서 발생 하는 이벤트를 처리 하는 방법을 보여 주기 위해 간단한 이벤트 처리기 (이벤트 수신기)를 목록 인스턴스에 추가 하 여이 프로젝트를 확장 합니다.

#### <a name="to-add-an-event-receiver-to-the-list-instance"></a>목록 인스턴스에 이벤트 수신기를 추가 하려면

1. [연습: SharePoint 용 사이트 열, 콘텐츠 형식 및 목록 만들기](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)에서 만든 프로젝트를 엽니다.

2. **솔루션 탐색기**에서 **클리닉**이라는 SharePoint 프로젝트 노드를 선택 합니다.

3. 메뉴 모음에서 **프로젝트**  >  **새 항목 추가**를 선택 합니다.

4. **Visual c #** 또는 **Visual Basic**에서 **SharePoint** 노드를 확장 한 다음 **2010** 항목을 선택 합니다.

5. **템플릿** 창에서 **이벤트 수신기**를 선택 하 고 이름을 **TestEventReceiver1**로 지정한 다음 **확인** 단추를 선택 합니다.

     **SharePoint 사용자 지정 마법사** 가 나타납니다.

6. **원하는 이벤트 수신기 유형을** 선택 하십시오. 목록에서 **목록 항목 이벤트**를 선택 합니다.

7. **이벤트 소스로 사용할 항목** 을 선택 하십시오. 목록에서 **환자 (Clinic\Patients)** 를 선택 합니다.

8. **다음 이벤트 처리** 목록에서 **항목 추가**됨 옆의 확인란을 선택 하 고 **마침** 단추를 선택 합니다.

     새 이벤트 수신기의 코드 파일에는 라는 단일 메서드가 포함 되어 있습니다 `ItemAdded` . 다음 단계에서는이 메서드에 코드를 추가 하 여 기본적으로 모든 연락처의 이름을 Scott 밤색으로 지정 합니다.

9. 기존 메서드를 `ItemAdded` 다음 코드로 바꾼 다음 **F5** 키를 선택 합니다.

     [!code-csharp[SP_EventReceiver#1](../sharepoint/codesnippet/CSharp/CustomField1/TestEventReceiver1/TestEventReceiver1.cs#1)]
     [!code-vb[SP_EventReceiver#1](../sharepoint/codesnippet/VisualBasic/CustomField1_VB/EventReceiver1/EventReceiver1.vb#1)]

     코드가 실행 되 고 SharePoint 사이트가 웹 브라우저에 나타납니다.

10. 빠른 실행 모음에서 **환자** 링크를 선택 하 고 **새 항목 추가** 링크를 선택 합니다.

     새 항목의 항목 양식이 열립니다.

11. 필드에 데이터를 입력 한 다음 **저장** 단추를 선택 합니다.

     **저장** 단추를 선택 하면 **환자 이름** 열이 자동으로 Scott 갈색 이름으로 업데이트 됩니다.

## <a name="see-also"></a>추가 정보

- [SharePoint 솔루션 개발](../sharepoint/developing-sharepoint-solutions.md)