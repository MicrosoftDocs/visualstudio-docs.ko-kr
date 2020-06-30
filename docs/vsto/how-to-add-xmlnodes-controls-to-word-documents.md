---
title: '방법: Word 문서에 XMLNodes 컨트롤 추가'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLNodes control, adding to documents
- controls [Office development in Visual Studio], adding to documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 95fc165c1a3123d68529f6ccaea99fea963c2a67
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85543496"
---
# <a name="how-to-add-xmlnodes-controls-to-word-documents"></a>방법: Word 문서에 XMLNodes 컨트롤 추가
  **중요** Microsoft word와 관련 하 여이 항목에서 설명 하는 정보는 microsoft word에서 사용자 지정 XML과 관련 된 특정 기능의 구현을 제거 했을 때 미국 및 해당 지역 외부에 있거나 microsoft에서 실행 되는 프로그램 (1 월 2010 이전에 Microsoft에서 사용이 허가 된 Microsoft Word 제품)의 혜택 및 사용을 위해서만 제공 됩니다. Microsoft Word에 대 한이 정보는 microsoft word 제품이 2010 년 1 월 10 일 이후 Microsoft에서 사용이 허가 된 Microsoft Word 제품,에서 실행 되는 프로그램을 개발 하거나 사용 하는 미국 또는 지역에 있는 개인 또는 조직에서 읽거나 사용할 수 없습니다. 이러한 제품은 해당 날짜 이전에 사용이 허가 된 제품과 동일 하 게 작동 하지 않습니다.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 반복 되는 XML 스키마 요소를 Microsoft Office Word 문서에 매핑하면 Visual Studio에서 자동으로 <xref:Microsoft.Office.Tools.Word.XMLNodes> 컨트롤을 문서에 추가 합니다.

 반복 되지 않는 XML 스키마 요소를 매핑하는 방법에 대 한 자세한 내용은 [방법: Word 문서에 XMLNode 컨트롤 추가](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)를 참조 하세요.

> [!NOTE]
> <xref:Microsoft.Office.Tools.Word.XMLNodes>컨트롤은 **도구 상자** 또는 **데이터 소스** 창에서 사용할 수 없으며 프로그래밍 방식으로 만들 수 없습니다.

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-add-an-xmlnodes-control-to-a-document"></a>문서에 XMLNodes 컨트롤을 추가 하려면

1. Visual Studio 디자이너의 문서에 있는 리본 메뉴에서 **개발자** 탭을 클릭 합니다.

    > [!NOTE]
    > **개발자** 탭이 표시되지 않는 경우 먼저 개발자 탭을 표시해야 합니다. 자세한 내용은 [방법: 리본 메뉴에 개발자 탭 표시](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)를 참조 하세요.

2. **XML** 그룹에서 **스키마**를 클릭 합니다.

     **템플릿 및 추가 기능** 대화 상자가 열립니다.

3. **XML 스키마** 탭을 클릭 합니다.

4. **스키마 추가**를 클릭 합니다.

     **스키마 추가** 대화 상자가 열립니다.

5. 반복 스키마 요소를 포함 하는 XML 스키마를 선택 하 고 **열기**를 클릭 합니다.

     **스키마 설정** 대화 상자가 나타납니다.

6. 별칭을 할당 하거나 **확인** 을 클릭 하 여 별칭 없이 스키마를 추가 합니다.

     스키마가 **스키마 추가** 대화 상자에 추가 됩니다.

7. **스키마 추가** 대화 상자에서 **확인**을 클릭 합니다.

     **XML 구조** 태스크 창이 열립니다.

8. **XML 구조** 태스크 창에서 반복 스키마 요소를 클릭 하 여 문서에 추가 합니다.

     <xref:Microsoft.Office.Tools.Word.XMLNodes>컨트롤이 만들어지고 프로젝트에 추가 됩니다.

## <a name="see-also"></a>참고 항목
- [XMLNodes 컨트롤](../vsto/xmlnodes-control.md)
- [확장 된 개체를 사용 하 여 Word 자동화](../vsto/automating-word-by-using-extended-objects.md)
- [호스트 항목 및 호스트 컨트롤 개요](../vsto/host-items-and-host-controls-overview.md)
- [호스트 항목 및 호스트 컨트롤의 프로그래밍에 대 한 제한 사항](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
