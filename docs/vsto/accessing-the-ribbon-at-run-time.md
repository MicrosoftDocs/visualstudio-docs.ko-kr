---
title: 런타임에 리본 메뉴에 액세스
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Globals class, Ribbon
- Ribbon [Office development in Visual Studio], accessing
- RibbonManager class
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7c7fdda6234f1e98117cdb1bf047762ed9d4621a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "71255741"
---
# <a name="access-the-ribbon-at-run-time"></a>런타임에 리본 메뉴에 액세스
  리본을 표시, 숨기기 및 수정하고, 사용자가 사용자 지정 작업창, 작업 창 또는 Outlook 양식 영역의 컨트롤에서 코드를 실행할 수 있도록 하는 코드를 작성할 수 있습니다.

 `Globals` 클래스를 사용하여 리본 메뉴에 액세스할 수 있습니다. Outlook 프로젝트의 경우 특정 Outlook 검사기나 Outlook 탐색기 창에 나타나는 리본 메뉴에 액세스할 수 있습니다.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

## <a name="access-the-ribbon-by-using-the-globals-class"></a>Globals 클래스를 사용 하 여 리본 메뉴에 액세스
 `Globals` 클래스를 사용하여 프로젝트의 어디에서나 문서 수준 프로젝트 또는 VSTO 추가 기능 프로젝트의 리본 메뉴에 액세스할 수 있습니다.

 클래스에 대 한 자세한 내용은 `Globals` [Office 프로젝트의 개체에 대 한 전역 액세스](../vsto/global-access-to-objects-in-office-projects.md)를 참조 하세요.

 다음 예제에서는 `Globals` 클래스를 사용하여 `Ribbon1`이라는 사용자 지정 리본 메뉴에 액세스하고 리본 메뉴의 콤보 상자에 표시되는 텍스트를 `Hello World`로 설정합니다.

 [!code-vb[Trin_Outlook_FR_Access#4](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#4)]
 [!code-csharp[Trin_Outlook_FR_Access#4](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#4)]

## <a name="access-a-collection-of-ribbons-that-appear-in-a-specific-outlook-inspector-window"></a>특정 Outlook 검사기 창에 나타나는 리본 컬렉션에 액세스
 Outlook *검사기*에 나타나는 리본 컬렉션에 액세스할 수 있습니다. 검사기는 사용자가 메일 메시지 만들기 등의 특정 작업을 수행할 때 Outlook에서 열리는 창입니다. 검사기 창의 리본 메뉴에 액세스하려면 `Globals` 클래스의 `Ribbons` 속성을 호출하고 검사기를 나타내는 <xref:Microsoft.Office.Interop.Outlook.Inspector> 개체를 전달합니다.

 다음 예제에서는 현재 포커스가 있는 검사기의 리본 컬렉션을 가져옵니다. 이 예제에서는 `Ribbon1`이라는 리본 메뉴에 액세스하고 리본 메뉴의 콤보 상자에 표시되는 텍스트를 `Hello World`로 설정합니다.

 [!code-vb[Trin_Outlook_FR_Access#5](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#5)]
 [!code-csharp[Trin_Outlook_FR_Access#5](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#5)]

## <a name="access-a-collection-of-ribbons-that-appear-for-a-specific-outlook-explorer"></a>특정 Outlook 탐색기에 대해 표시 되는 리본 컬렉션 액세스
 Outlook *탐색기*에 나타나는 리본 컬렉션에 액세스할 수 있습니다. 탐색기는 Outlook 인스턴스에 대한 기본 애플리케이션 UI(사용자 인터페이스)입니다. 탐색기 창의 리본 메뉴에 액세스하려면 `Globals` 클래스의 `Ribbons` 속성을 호출하고 탐색기를 나타내는 <xref:Microsoft.Office.Interop.Outlook.Explorer> 개체를 전달합니다.

 다음 예제에서는 현재 포커스가 있는 탐색기의 리본 컬렉션을 가져옵니다. 이 예제에서는 `Ribbon1`이라는 리본 메뉴에 액세스하고 리본 메뉴의 콤보 상자에 표시되는 텍스트를 `Hello World`로 설정합니다.

 [!code-vb[Trin_Outlook_FR_Access#6](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#6)]
 [!code-csharp[Trin_Outlook_FR_Access#6](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#6)]

## <a name="see-also"></a>참고 항목
- [리본 개요](../vsto/ribbon-overview.md)
- [리본 디자이너](../vsto/ribbon-designer.md)
- [리본 XML](../vsto/ribbon-xml.md)
- [리본 개체 모델 개요](../vsto/ribbon-object-model-overview.md)
- [연습: 리본 디자이너를 사용 하 여 사용자 지정 탭 만들기](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [연습: 런타임에 리본 메뉴의 컨트롤 업데이트](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)
- [Outlook에 대 한 리본 사용자 지정](../vsto/customizing-a-ribbon-for-outlook.md)
- [런타임에 양식 영역 액세스](../vsto/accessing-a-form-region-at-run-time.md)
