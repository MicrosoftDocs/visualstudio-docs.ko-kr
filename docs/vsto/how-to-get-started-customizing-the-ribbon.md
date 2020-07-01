---
title: '방법: 리본 메뉴 사용자 지정 시작'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom Ribbon, adding Ribbon to project
- Ribbon [Office development in Visual Studio], adding
- Ribbon [Office development in Visual Studio], customizing
- customizing the Ribbon, adding Ribbon to project
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: be311f87862f4447d903294508927735d3507b08
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85520070"
---
# <a name="how-to-get-started-customizing-the-ribbon"></a>방법: 리본 메뉴 사용자 지정 시작
  Microsoft Office 응용 프로그램의 리본을 사용자 지정 하려면 Office 프로젝트에 **리본 (비주얼 디자이너)** 또는 **리본 (XML)** 항목을 추가 합니다.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-add-a-ribbon-to-a-project"></a>프로젝트에 리본을 추가 하려면

1. **프로젝트** 메뉴에서 **새 항목 추가**를 클릭 합니다.

2. **새 항목 추가** 대화 상자에서 **리본 (비주얼 디자이너)** 또는 **리본 (XML)** 을 선택 합니다. 이러한 템플릿에 대 한 자세한 내용은 [리본 개요](../vsto/ribbon-overview.md)를 참조 하세요.

3. **이름** 상자에 리본 항목의 이름을 입력 합니다.

    이름은 다음 문자를 포함할 수 없습니다.

   - 파운드(#)

   - 백분율(%)

   - 앰퍼샌드 (&)

   - 별표(*)

   - 세로 막대(|)

   - 백슬래시(\\)

   - 콜론(:)

   - 큰따옴표(")

   - 보다 작음(\<)

   - 보다 큼(>)

   - 물음표(?)

   - 슬래시(/)

   - 선행 또는 후행 공백(' ')

   - Windows 또는 DOS (예: "nul", "aux", "con", "com1", "lpt1" 등) 용으로 예약 된 이름

4. **확인**을 클릭합니다.

   리본 항목이 **솔루션 탐색기**에 나타납니다. 다음 단계에 대 한 자세한 내용은 [리본 개요](../vsto/ribbon-overview.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목
- [런타임에 리본 메뉴에 액세스](../vsto/accessing-the-ribbon-at-run-time.md)
- [리본 디자이너](../vsto/ribbon-designer.md)
- [리본 XML](../vsto/ribbon-xml.md)
- [연습: 리본 디자이너를 사용 하 여 사용자 지정 탭 만들기](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [연습: 리본 XML을 사용 하 여 사용자 지정 탭 만들기](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
