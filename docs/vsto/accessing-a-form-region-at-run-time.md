---
title: 런타임에 양식 영역 액세스
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Inspectors [Office development in Visual Studio]
- Explorers [Office development in Visual Studio]
- form regions [Office development in Visual Studio], accessing at run time
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5dd8818b57a1aa33b70254303150d8f00e36cc02
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "71255794"
---
# <a name="access-a-form-region-at-run-time"></a>런타임에 양식 영역 액세스

|적용 대상|
|----------------|
|이 항목의 정보는 다음 프로젝트 형식 및 Microsoft Office 버전에만 적용됩니다. 자세한 내용은 [Office 응용 프로그램 및 프로젝트 형식에 따라 사용 가능한 기능](../vsto/features-available-by-office-application-and-project-type.md)을 참조 하세요.<br /><br /> **프로젝트 형식**<br /><br /> -VSTO 추가 기능 프로젝트<br /><br /> **Microsoft Office 버전**<br /><br /> -   [!INCLUDE[Outlook_14_short](../vsto/includes/outlook-14-short-md.md)]|

 `Globals` 클래스를 사용하여 Outlook 프로젝트의 어디에서나 양식 영역에 액세스할 수 있습니다. 클래스에 대 한 자세한 내용은 `Globals` [Office 프로젝트의 개체에 대 한 전역 액세스](../vsto/global-access-to-objects-in-office-projects.md)를 참조 하세요.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="access-form-regions-that-appear-in-a-specific-outlook-inspector-window"></a>특정 Outlook 검사기 창에 표시 되는 양식 영역에 액세스
 특정 Outlook 검사기에 나타나는 모든 양식 영역에 액세스하려면 `FormRegions` 클래스의 `Globals` 속성을 호출하고 검사기를 나타내는 <xref:Microsoft.Office.Interop.Outlook.Inspector> 개체를 전달합니다.

 다음 예제에서는 현재 포커스가 있는 검사기에 나타나는 양식 영역 컬렉션을 가져옵니다. 이 예제에서는 `formRegion1` 이라는 컬렉션의 양식 영역에 액세스하고 텍스트 상자에 나타나는 텍스트를 `Hello World`로 설정합니다.

 [!code-vb[Trin_Outlook_FR_Access#2](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#2)]
 [!code-csharp[Trin_Outlook_FR_Access#2](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#2)]

## <a name="access-form-regions-that-appear-in-a-specific-outlook-explorer-window"></a>특정 Outlook 탐색기 창에 표시 되는 양식 영역에 액세스
 특정 Outlook 탐색기에 나타나는 모든 양식 영역에 액세스하려면 `FormRegions` 클래스의 `Globals` 속성을 호출하고 탐색기를 나타내는 <xref:Microsoft.Office.Interop.Outlook.Explorer> 개체를 전달합니다.

 다음 예제에서는 현재 포커스가 있는 탐색기에 나타나는 양식 영역 컬렉션을 가져옵니다. 이 예제에서는 `formRegion1` 이라는 컬렉션의 양식 영역에 액세스하고 텍스트 상자에 나타나는 텍스트를 `Hello World`로 설정합니다.

 [!code-vb[Trin_Outlook_FR_Access#3](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#3)]
 [!code-csharp[Trin_Outlook_FR_Access#3](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#3)]

## <a name="access-all-form-regions"></a>모든 양식 영역 액세스
 모든 탐색기 및 모든 검사기에 나타나는 모든 양식 영역에 액세스하려면 `FormRegions` 클래스의 `Globals` 속성을 호출합니다.

 다음 예제에서는 모든 탐색기 및 모든 검사기에 나타나는 양식 영역 컬렉션을 가져옵니다. 그런 다음 `formRegion1` 이라는 양식 영역에 액세스하고 텍스트 상자에 나타나는 텍스트를 `Hello World`로 설정합니다.

 [!code-vb[Trin_Outlook_FR_Access#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#1)]
 [!code-csharp[Trin_Outlook_FR_Access#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#1)]

## <a name="access-controls-on-a-form-region"></a>양식 영역에 대 한 액세스 제어
 `Globals` 클래스를 사용하여 양식 영역의 컨트롤에 액세스하려면 컨트롤에서 양식 영역 코드 파일 외부의 코드에 액세스할 수 있도록 만들어야 합니다.

### <a name="form-regions-designed-in-the-form-region-designer"></a>양식 영역 디자이너에서 디자인 된 양식 영역
 C#의 경우 액세스하려는 각 컨트롤의 한정자를 변경합니다. 이렇게 하려면 양식 영역 디자이너에서 각 컨트롤을 선택하고 **Modifiers** 속성을 **Internal** 로 변경하거나 **속성** 창에서 **public** 으로 변경합니다. 예를 들어 **의** Modifier `textBox1` 속성을 **Internal**로 변경한 경우 `textBox1` 을 입력하여 `Globals.FormRegions.FormRegion1.textBox1`에 액세스할 수 있습니다.

 Visual Basic의 경우 한정자를 변경할 필요가 없습니다.

### <a name="imported-form-regions"></a>가져온 양식 영역
 Outlook에서 디자인된 양식 영역을 가져올 때 양식 영역에 있는 각 컨트롤의 액세스 한정자가 private으로 설정됩니다. 양식 영역 디자이너를 사용하여 가져온 양식 영역을 수정할 수 없으므로 **속성** 창에서 컨트롤의 한정자를 변경할 수 없습니다.

 양식 영역 코드 파일 외부에서 컨트롤에 액세스할 수 있게 하려면 양식 영역 코드 파일 내에서 해당 컨트롤을 반환하도록 속성을 만듭니다.

 C #에서 속성을 만드는 방법에 대 한 자세한 내용은 [방법: 읽기/쓰기 속성 선언 및 사용 &#40;C&#35; 프로그래밍 가이드&#41;](/dotnet/csharp/programming-guide/classes-and-structs/how-to-declare-and-use-read-write-properties)를 참조 하세요.

 Visual Basic에서 속성을 만드는 방법에 대 한 자세한 내용은 [방법: 속성 만들기 (Visual Basic)](/dotnet/visual-basic/programming-guide/language-features/procedures/how-to-create-a-property)를 참조 하세요.

## <a name="see-also"></a>참고 항목
- [Outlook 양식 영역 만들기 지침](../vsto/guidelines-for-creating-outlook-form-regions.md)
- [연습: Outlook 양식 영역 디자인](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [방법: Outlook 추가 기능 프로젝트에 양식 영역 추가](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
- [Outlook 양식 영역의 사용자 지정 작업](../vsto/custom-actions-in-outlook-form-regions.md)
- [Outlook 메시지 클래스에 양식 영역 연결](../vsto/associating-a-form-region-with-an-outlook-message-class.md)
- [연습: Outlook에서 디자인 한 양식 영역 가져오기](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)
- [방법: Outlook에서 양식 영역 표시 하지 않기](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)
- [Outlook 양식 영역 만들기](../vsto/creating-outlook-form-regions.md)
- [런타임에 리본 메뉴에 액세스](../vsto/accessing-the-ribbon-at-run-time.md)
