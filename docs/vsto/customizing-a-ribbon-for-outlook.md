---
title: Outlook에 대 한 리본 사용자 지정
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Inspectors [Office development in Visual Studio]
- Outlook [Office development in Visual Studio], Ribbon
- customizing the Ribbon, about customizing the Ribbon
- custom Ribbon, about customizing the Ribbon
- Ribbon [Office development in Visual Studio], Outlook
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2865bd89da3b59a24208e07739e8c56254959c88
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72986098"
---
# <a name="customize-a-ribbon-for-outlook"></a>Outlook에 대 한 리본 사용자 지정
  Microsoft Office Outlook에서 리본을 사용자 지정할 경우 애플리케이션에서 사용자 지정 리본이 나타나는 위치를 고려해야 합니다. Outlook에서 리본은 사용자가 메일 메시지 만들기 등의 특정 작업을 수행할 때 열리는 창과 기본 애플리케이션 UI(사용자 인터페이스)에 표시됩니다. 이러한 애플리케이션 창의 이름을 검사기라고 합니다.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="add-a-custom-ribbon-to-the-main-application-ui"></a>기본 응용 프로그램 UI에 사용자 지정 리본 추가
 Outlook의 기본 애플리케이션 UI를 탐색기라고 합니다. **리본 (비주얼 디자이너)** 항목을 사용 하는 경우 **속성** 창에서 리본의 **RibbonType** 속성을 클릭 한 다음 **Microsoft**탐색기를 선택 하 여 탐색기에 리본 메뉴를 추가할 수 있습니다.

## <a name="assign-a-ribbon-to-an-inspector"></a>검사기에 리본 할당
 검사기에 대한 메시지 클래스에 해당하는 리본 형식을 지정하여 사용자 지정하려는 검사기를 식별합니다.

 **리본 (비주얼 디자이너)** 항목을 사용 하는 경우 **속성** 창에서 리본의 **RibbonType** 속성을 클릭 한 다음 값 목록에서 리본 id를 하나 이상 선택 합니다.

 프로젝트에 리본을 두 개 이상 추가할 수 있습니다. 두 개 이상의 리본이 리본 ID를 공유하는 경우 프로젝트의 `ThisAddin` 클래스에서 `CreateRibbonExtensibilityObject` 메서드를 재정의하여 런타임에 표시할 리본을 지정합니다. 자세한 내용은 [리본 개요](../vsto/ribbon-overview.md)를 참조 하세요. 각 리본 유형에 대 한 자세한 내용은 기술 문서 [Outlook 2007에서 리본 사용자 지정](/previous-versions/office/developer/office-2007/bb226712(v=office.12))을 참조 하세요.

## <a name="specify-the-ribbon-type-by-using-ribbon-xml"></a>리본 XML을 사용 하 여 리본 형식 지정
 **리본 (XML)** 항목을 사용 하는 경우 메서드에서 *ribbonID* 매개 변수의 값을 확인 <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> 하 고 적절 한 리본을 반환 합니다.

 <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> 메서드는 Visual Studio를 통해 리본 코드 파일에서 자동으로 생성됩니다. *RibbonID* 매개 변수는 탐색기 또는 특정 유형의 검사기를 식별 하는 문자열입니다. *RibbonID* 매개 변수의 가능한 값에 대 한 전체 목록은 기술 문서 [Outlook 2007에서 리본 사용자 지정](/previous-versions/office/developer/office-2007/bb226712(v=office.12))을 참조 하세요.

 다음 코드 예제에서는 `Microsoft.Outlook.Mail.Compose` 검사기에만 사용자 지정 리본을 표시하는 방법을 보여 줍니다. 사용자가 새 메일 메시지를 만들 때 열리는 검사기입니다. 표시할 리본은 `GetResourceText()` **리본** 클래스에서 생성 되는 메서드에 지정 됩니다. **Ribbon** 클래스에 대 한 자세한 내용은 [리본 XML](../vsto/ribbon-xml.md)을 참조 하세요.

 [!code-csharp[Trin_RibbonOutlookBasic#1](../vsto/codesnippet/CSharp/Trin_RibbonOutlookBasic/Ribbon1.cs#1)]
 [!code-vb[Trin_RibbonOutlookBasic#1](../vsto/codesnippet/VisualBasic/Trin_RibbonOutlookBasic/Ribbon1.vb#1)]

## <a name="see-also"></a>참조
- [런타임에 리본 메뉴에 액세스](../vsto/accessing-the-ribbon-at-run-time.md)
- [리본 개요](../vsto/ribbon-overview.md)
- [리본 디자이너](../vsto/ribbon-designer.md)
- [리본 XML](../vsto/ribbon-xml.md)
