---
title: '방법: Visual Studio 내부의 Word 문서에 스키마 매핑'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XML schemas [Office development in Visual Studio], mapping
- mappings [Office development in Visual Studio], XML schemas to Word documents
- Word [Office development in Visual Studio], mapping XML schemas
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 281d9dc18ae1d0550ba844e58d4e39c3723c8dfb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85538153"
---
# <a name="how-to-map-schemas-to-word-documents-inside-visual-studio"></a>방법: Visual Studio 내부의 Word 문서에 스키마 매핑
  **중요** Microsoft word와 관련 하 여이 항목에서 설명 하는 정보는 microsoft word에서 사용자 지정 XML과 관련 된 특정 기능의 구현을 제거 했을 때 미국 및 해당 지역 외부에 있거나 microsoft에서 실행 되는 프로그램 (1 월 2010 이전에 Microsoft에서 사용이 허가 된 Microsoft Word 제품)의 혜택 및 사용을 위해서만 제공 됩니다. Microsoft Word에 대 한이 정보는 microsoft word 제품이 2010 년 1 월 10 일 이후 Microsoft에서 사용이 허가 된 Microsoft Word 제품,에서 실행 되는 프로그램을 개발 하거나 사용 하는 미국 또는 지역에 있는 개인 또는 조직에서 읽거나 사용할 수 없습니다. 이러한 제품은 해당 날짜 이전에 사용이 허가 된 제품과 동일 하 게 작동 하지 않습니다.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 문서가 Visual Studio에서 열려 있는 동안 XML 스키마를 문서에 매핑할 수 있습니다. Visual Studio 외부에서 문서를 열 때 사용 하는 것과 동일한 Microsoft Office Word 도구를 사용 합니다. Office 프로젝트는 Word 솔루션을 만들기 전이나 후에 스키마를 문서에 매핑 하는지 여부에 관계 없이 동일한 개체를 만듭니다.

## <a name="to-map-an-xml-schema-to-a-word-document-in-visual-studio"></a>Visual Studio에서 XML 스키마를 Word 문서에 매핑하려면

1. Visual Studio 내에서 Word 문서 또는 템플릿 프로젝트를 엽니다.

2. 문서를 클릭 하 여 디자이너에 포커스를 이동 합니다.

3. 리본에서 **개발자** 탭을 클릭 합니다.

    > [!NOTE]
    > **개발자** 탭이 표시되지 않는 경우 먼저 개발자 탭을 표시해야 합니다. 자세한 내용은 [방법: 리본 메뉴에 개발자 탭 표시](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)를 참조 하세요.

4. **XML** 그룹에서 **스키마**를 클릭 합니다.

     **템플릿 및 추가 기능** 대화 상자가 열립니다.

5. **XML 스키마** 탭을 클릭 합니다.

6. **스키마 추가**를 클릭 합니다.

     **스키마 추가** 대화 상자가 열립니다.

7. 스키마 파일을 찾아 선택한 다음 **열기**를 클릭 합니다.

     **스키마 설정** 대화 상자가 열립니다.

8. 별칭을 할당 하거나 **확인** 을 클릭 하 여 별칭 없이 스키마를 추가 합니다.

9. **확인**을 클릭합니다.

     **XML 구조** 창이 열립니다.

10. **XML 구조** 창에서 해당 컨트롤을 만들려는 문서 위치로 요소를 끌어 옵니다.

## <a name="see-also"></a>추가 정보
- [방법: Visual Studio 내에서 워크시트에 스키마 매핑](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)
- [문서 수준 사용자 지정의 XML 스키마 및 데이터](../vsto/xml-schemas-and-data-in-document-level-customizations.md)
