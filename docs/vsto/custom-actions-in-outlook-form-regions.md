---
title: Outlook 양식 영역의 사용자 지정 작업
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio], custom actions
- custom actions [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 817cf9fe8698c2908e873246a8971f90fe72b460
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "71254449"
---
# <a name="custom-actions-in-outlook-form-regions"></a>Outlook 양식 영역의 사용자 지정 작업
  작업 사용자가 Microsoft Office Outlook 항목에 응답할 수 있는 단추를 표시 합니다. 예를 들어 메일 항목에 응답 하려면 사용자가 **회신**, **전체 회신**또는 **전달** 작업 단추를 클릭 합니다. 이러한 각 작업은 새 메일 항목을 만들고 원래 항목의 정보를 사용 하 여 해당 항목의 필드를 채웁니다.

 모든 종류의 Outlook 항목을 여는 사용자 지정 작업을 만들 수 있습니다. 예를 들어 새 약속이 나 작업 항목을 여는 사용자 지정 작업을 추가할 수 있습니다. 사용자 지정 작업의 속성을 설정 하거나 사용자 지정 코드를 사용 하 여 새 항목의 필드를 채웁니다. 사용자 지정 작업은 Outlook 검사기 창에 열려 있는 항목의 **사용자 지정 작업** 드롭다운에 표시 됩니다.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="add-custom-actions-to-a-form-region"></a>양식 영역에 사용자 지정 작업 추가
 양식 영역에 사용자 지정 작업을 추가 하려면 **사용자 지정 동작** 대화 상자를 사용 합니다. **솔루션 탐색기**에서 양식 영역을 선택 하 고, **속성 창**에서 **매니페스트** 노드를 확장 하 고, **customactions** 속성을 선택 하 고, 줄임표 단추 (![ASP.NET Mobile Designer ellipse](../sharepoint/media/mwellipsis.gif "ASP.NET 모바일 디자이너 줄임표"))를 클릭 하 여 **사용자 지정 작업** 대화 상자를 열 수 있습니다.

 **사용자 지정 동작** 대화 상자를 사용 하 여 *대상 양식을*지정할 수 있습니다. 대상 폼은 사용자가 사용자 지정 작업을 실행할 때 표시 되는 양식입니다.

 **사용자 지정 작업** 대화 상자를 사용 하 여 원래 항목의 정보가 대상 양식에 표시 되는 방식을 지정할 수도 있습니다.

 다음 표에서는 **사용자 지정 작업** 대화 상자에서 사용할 수 있는 속성에 대해 설명 합니다.

|속성|설명|
|--------------|-----------------|
|**AddressLike**|대상 폼의 주소를 지정 하는 방법을 지정 합니다.|
|**본문**|원본 항목의 본문이 대상 폼에 추가 되는 방법을 지정 합니다.|
|**사용**|사용자 지정 동작을 사용할 수 있는지 여부를 나타냅니다. 이 속성이 **false**로 설정 된 경우 사용자 지정 작업을 사용할 수 없습니다.|
|**메서드**|사용자 지정 작업을 실행할 때 사용할 수 있는 응답 유형을 지정 합니다. 사용자 지정 작업은 양식을 보내거나 양식을 열거나 사용자에 게 양식을 보낼지 아니면 사용자에 게 표시할 수 있습니다.|
|**이름**|코드에서이 사용자 지정 작업을 참조 하는 데 사용할 수 있는 내부 이름을 지정 합니다.|
|**ShowOnRibbon**|원래 항목의 리본 메뉴에 사용자 지정 작업을 표시할지 여부를 나타냅니다.|
|**주제 접두사**|대상 폼의 제목 줄 시작 부분에 삽입 되는 텍스트를 지정 합니다.|
|**TargetForm**|대상 양식의 메시지 클래스 이름을 지정 합니다. 예를 들어 IPM를 입력 **합니다. ** 작업 폼을 여는 작업입니다.|
|**제목**|사용자 지정 작업 단추의 레이블을 지정 합니다.|

## <a name="customize-a-custom-action-at-run-time"></a>런타임에 사용자 지정 작업 사용자 지정
 코드를 사용 하 여 사용자 지정 작업에 동작을 추가할 수도 있습니다. 예를 들어 전자 메일 받는 사람의 이름을 사용 하는 코드를 추가 하 고 해당 이름을 새 약속 항목의 참석자로 추가할 수 있습니다. 이렇게 하려면 [MailItem 개체](/office/vba/api/Outlook.MailItem)의 [CustomAction](/office/vba/api/Outlook.MailItem.CustomAction) 이벤트를 처리 합니다.

## <a name="see-also"></a>참고 항목
- [Outlook 양식 영역 만들기](../vsto/creating-outlook-form-regions.md)
- [연습: Outlook 양식 영역 디자인](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Outlook 메시지 클래스에 양식 영역 연결](../vsto/associating-a-form-region-with-an-outlook-message-class.md)
