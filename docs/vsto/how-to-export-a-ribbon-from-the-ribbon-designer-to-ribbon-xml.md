---
title: '방법: 리본 디자이너에서 리본 XML로 리본 메뉴 내보내기'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom Ribbon, XML
- customizing the Ribbon, XML
- Ribbon [Office development in Visual Studio], XML
- Ribbon [Office development in Visual Studio], exporting
- XML [Office development in Visual Studio], Ribbon
- Ribbon Designer [Office development in Visual Studio]
- exporting Ribbon
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 57918e8a51a3948a2c69eb0c8ab5438b147e44f0
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85543470"
---
# <a name="how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml"></a>방법: 리본 디자이너에서 리본 XML로 리본 메뉴 내보내기
  **리본 (비주얼 디자이너)** 항목은 가능한 모든 유형의 리본 사용자 지정을 지원 하지 않습니다. 고급 방법으로 리본을 사용자 지정 하기 위해 디자이너에서 리본 XML로 리본 메뉴를 내보내고 XML을 직접 편집할 수 있습니다.

> [!NOTE]
> 모든 속성 값이 리본 XML 파일에 표시 되는 것은 아닙니다. 자세한 내용은 [리본 개요](../vsto/ribbon-overview.md)를 참조 하세요.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml"></a>리본 디자이너에서 리본 XML로 리본 메뉴를 내보내려면

1. **솔루션 탐색기**에서 리본 코드 파일을 마우스 오른쪽 단추로 클릭 한 다음 **디자이너 보기**를 클릭 합니다.

2. 리본 디자이너를 마우스 오른쪽 단추로 클릭 한 다음 **XML로 리본 메뉴 내보내기를**클릭 합니다.

     Visual Studio에서 리본 XML 파일 및 리본 XML 코드 파일을 프로젝트에 추가 합니다.

3. 리본 코드 클래스에서로 시작 하는 주석을 찾습니다 `TODO:` .

4. 개발 중인 솔루션의 형식에 따라 이러한 주석의 코드 블록을 **ThisAddin**, **ThisWorkbook**또는 **ThisDocument** 클래스에 복사 합니다.

     이 코드를 사용 하 여 Microsoft Office 응용 프로그램에서 사용자 지정 리본을 검색 하 고 로드할 수 있습니다. 자세한 내용은 [Ribbon XML](../vsto/ribbon-xml.md)을 참조하세요.

5. **ThisAddin**, **ThisWorkbook**또는 **ThisDocument** 클래스에서 코드 블록의 주석 처리를 제거 합니다.

     코드의 주석 처리를 해제 한 후에는 다음 예제와 유사 합니다. 이 예제에서는 리본 클래스가 호출 됩니다 `MyRibbon` .

     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.cs#1)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.vb#1)]

6. 리본 XML 코드 파일로 전환 하 고 `Ribbon Callbacks` 지역을 찾습니다.

     여기서는 단추 클릭과 같은 사용자 동작을 처리 하는 콜백 메서드를 작성 합니다.

7. 리본 디자이너 코드에서 작성 한 각 이벤트 처리기에 대 한 콜백 메서드를 만듭니다.

8. 이벤트 처리기에서 모든 이벤트 처리기 코드를 콜백 메서드로 이동 하 고, RibbonX (리본 확장성) 프로그래밍 모델을 사용 하도록 코드를 수정 합니다.

     콜백 메서드를 작성 하 고 RibbonX 프로그래밍 모델을 사용 하는 방법에 대 한 자세한 내용은 [리본 XML](../vsto/ribbon-xml.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목
- [리본 개요](../vsto/ribbon-overview.md)
- [리본 디자이너](../vsto/ribbon-designer.md)
- [리본 XML](../vsto/ribbon-xml.md)
- [연습: 리본 디자이너를 사용 하 여 사용자 지정 탭 만들기](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [연습: 리본 XML을 사용 하 여 사용자 지정 탭 만들기](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
