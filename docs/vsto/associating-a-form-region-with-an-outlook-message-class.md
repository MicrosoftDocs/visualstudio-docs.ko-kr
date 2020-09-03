---
title: Outlook 메시지 클래스에 양식 영역 연결
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VSTO.NewFormRegionWizard.InvalidMessageClassName
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- FormRegionMessageClassAttribute
- form regions [Office development in Visual Studio], message classes
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 45db262b6bf7843a3893c5d60f0b6eaea5fcb70b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "71254571"
---
# <a name="associate-a-form-region-with-an-outlook-message-class"></a>Outlook 메시지 클래스에 양식 영역 연결
  양식 영역을 각 항목의 메시지 클래스와 연결 하 여 양식 영역을 표시 하는 Microsoft Office Outlook 항목을 지정할 수 있습니다. 예를 들어 메일 항목의 아래쪽에 양식 영역을 추가 하려는 경우 양식 영역을 메시지 클래스와 연결할 수 있습니다 `IPM.Note` .

 양식 영역을 메시지 클래스와 연결 하려면 **새 Outlook 양식 영역** 마법사에서 메시지 클래스 이름을 지정 하거나 양식 영역 팩터리 클래스에 특성을 적용 합니다.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="understand-outlook-message-classes"></a>Outlook 메시지 클래스 이해
 Outlook 메시지 클래스는 Outlook 항목의 형식을 식별 합니다. 다음 표에서는 이러한 8 가지 표준 항목 유형과 해당 메시지 클래스 이름을 나열 합니다.

|Outlook 항목 유형|메시지 클래스 이름|
|-----------------------|------------------------|
|AppointmentItem|`IPM.Appointment`|
|ContactItem|`IPM.Contact`|
|DistListItem|`IPM.DistList`|
|JournalItem|`IPM.Activity`|
|MailItem|`IPM.Note`|
|PostItem|`IPM.Post` 또는 `IPM.Post.RSS`|
| TaskItem|`IPM.Task`|

 사용자 지정 메시지 클래스의 이름을 지정할 수도 있습니다. 사용자 지정 메시지 클래스는 Outlook에서 정의한 사용자 지정 양식을 식별 합니다.

> [!NOTE]
> 바꾸기 및 모두 바꾸기 양식 영역에 대해 새 사용자 지정 메시지 클래스 이름을 지정할 수 있습니다. 기존 사용자 지정 양식의 메시지 클래스 이름을 사용할 필요는 없습니다. 사용자 지정 메시지 클래스의 이름은 고유 해야 합니다. 이름이 고유한 지 확인 하는 한 가지 방법은 다음과 유사한 명명 규칙을 사용 하는 것입니다. \<*StandardMessageClassName*> . \<*Company*> .\<*MessageClassName*> (예: `IPM.Note.Contoso.MyMessageClass` ).

## <a name="associate-a-form-region-with-an-outlook-message-class"></a>Outlook 메시지 클래스에 양식 영역 연결
 양식 영역을 메시지 클래스와 연결 하는 방법에는 다음 두 가지가 있습니다.

- **새 Outlook 양식 영역** 마법사를 사용 합니다.

- 클래스 특성을 적용 합니다.

### <a name="use-the-new-outlook-form-region-wizard"></a>새 Outlook 양식 영역 마법사 사용
 **새 Outlook 양식 영역** 마법사의 마지막 페이지에서 표준 메시지 클래스를 선택 하 고 양식 영역에 연결할 사용자 지정 메시지 클래스의 이름을 입력할 수 있습니다.

 양식 영역이 폼의 전체 양식이 나 기본 페이지를 대체 하도록 디자인 된 경우 표준 메시지 클래스를 사용할 수 없습니다. 양식에 새 페이지를 추가 하거나 폼의 아래쪽에 추가 된 양식에 대해서만 표준 메시지 클래스 이름을 지정할 수 있습니다. 자세한 내용은 [방법: Outlook 추가 기능 프로젝트에 양식 영역 추가](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)를 참조 하세요.

 하나 이상의 사용자 지정 메시지 클래스를 포함 하려면 **이 양식 영역을 표시할 사용자 지정 메시지 클래스** 의 이름을 입력 하십시오. 상자에 이름을 입력 합니다.

 입력 하는 이름은 다음 지침을 따라야 합니다.

- 정규화 된 메시지 클래스 이름을 사용 합니다 (예: "IPM. 참고. Contoso ").

- 여러 메시지 클래스 이름을 구분 하려면 세미콜론을 사용 합니다.

- 표준 Outlook 메시지 클래스 (예: "IPM")를 포함 하지 마십시오. Note "또는" IPM. 담당자 ". 사용자 지정 메시지 클래스 (예: "IPM")만 포함 합니다. 참고. Contoso ".

- 기본 메시지 클래스를 단독으로 지정 하지 마십시오 (예: "IPM").

- 각 메시지 클래스 이름에 대해 256 자를 초과 하지 않습니다.

  [ **마침**]을 클릭 하면 **새 Outlook 양식 영역** 마법사에서 입력의 형식에 대 한 유효성을 검사 합니다.

> [!NOTE]
> **새 Outlook 양식 영역** 마법사는 사용자가 제공 하는 메시지 클래스 이름이 올바른지 또는 유효한 지 확인 하지 않습니다.

 마법사를 완료 하면 **새 Outlook 양식 영역** 마법사가 지정 된 메시지 클래스 이름을 포함 하는 양식 영역 클래스에 특성을 적용 합니다. 이러한 특성을 수동으로 적용할 수도 있습니다.

### <a name="apply-class-attributes"></a>클래스 특성 적용
 **새 Outlook 양식 영역** 마법사를 완료 한 후 양식 영역을 outlook 메시지 클래스와 연결할 수 있습니다. 이렇게 하려면 양식 영역 팩터리 클래스에 특성을 적용 합니다.

 다음 예제에서는 <xref:Microsoft.Office.Tools.Outlook.FormRegionMessageClassAttribute> 라는 양식 영역 팩터리 클래스에 적용 된 두 가지 특성을 보여 줍니다 `myFormRegion` . 첫 번째 특성은 메일 메시지 양식의 표준 메시지 클래스에 양식 영역을 연결 합니다. 두 번째 특성은 이라는 사용자 지정 메시지 클래스에 양식 영역을 연결 합니다 `IPM.Task.Contoso` .

 [!code-vb[Trin_Outlook_FR_Attributes#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Attributes/FormRegion1.vb#1)]
 [!code-csharp[Trin_Outlook_FR_Attributes#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Attributes/FormRegion1.cs#1)]

 특성은 다음 지침을 따라야 합니다.

- 사용자 지정 메시지 클래스의 경우 정규화 된 메시지 클래스 이름을 사용 합니다 (예: "IPM. 참고. Contoso ").

- 기본 메시지 클래스를 단독으로 지정 하지 마십시오 (예: "IPM").

- 각 메시지 클래스 이름에 대해 256 자를 초과 하지 않습니다.

- 양식 영역이 폼의 전체 폼 또는 기본 페이지를 대체 하는 경우 표준 메시지 클래스의 이름을 포함 하지 마세요. 양식에 새 페이지를 추가 하거나 폼의 아래쪽에 추가 된 양식에 대해서만 표준 메시지 클래스 이름을 지정할 수 있습니다. 자세한 내용은 [방법: Outlook 추가 기능 프로젝트에 양식 영역 추가](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)를 참조 하세요.

  Visual Studio는 프로젝트를 빌드할 때 메시지 클래스 이름 형식의 유효성을 검사 합니다.

> [!NOTE]
> Visual Studio에서는 사용자가 제공 하는 메시지 클래스 이름이 올바른지 또는 유효한 지 확인 하지 않습니다.

## <a name="see-also"></a>참고 항목
- [런타임에 양식 영역 액세스](../vsto/accessing-a-form-region-at-run-time.md)
- [Outlook 양식 영역 만들기](../vsto/creating-outlook-form-regions.md)
- [연습: Outlook 양식 영역 디자인](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Outlook 양식 영역 만들기 지침](../vsto/guidelines-for-creating-outlook-form-regions.md)
- [양식 이름 및 메시지 클래스 개요](/office/vba/outlook/Concepts/Forms/form-name-and-message-class-overview)
- [Outlook 양식과 항목이 함께 작동 하는 방법](/office/vba/outlook/Concepts/Forms/how-outlook-forms-and-items-work-together)
