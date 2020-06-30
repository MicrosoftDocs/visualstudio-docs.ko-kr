---
title: '방법: 리본의 탭 위치 변경'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], tabs
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8f821ea2a469fc06f80a7aaea96d07274d02a81d
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544861"
---
# <a name="how-to-change-the-position-of-a-tab-on-the-ribbon"></a>방법: 리본의 탭 위치 변경
  **탭 컬렉션 편집기**를 사용 하 여 리본 메뉴에서 사용자 지정 탭의 순서를 변경할 수 있습니다. 리본 메뉴의 기본 제공 탭 앞 이나 뒤에 사용자 지정 탭을 배치할 수 있습니다. 기본 제공 탭은 Microsoft Office 응용 프로그램의 리본에 이미 있는 탭입니다. 예를 들어 **데이터** 탭은 Excel의 기본 제공 탭입니다.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-change-the-order-of-tabs-on-the-ribbon"></a>리본 메뉴의 탭 순서를 변경 하려면

1. **솔루션 탐색기**에서 리본 코드 파일 (*.vb* 또는 *.cs* 파일)을 선택 합니다.

2. **보기** 메뉴에서 **디자이너**를 클릭 합니다.

3. 리본 디자이너를 마우스 오른쪽 단추로 클릭 한 다음 **속성**을 클릭 합니다.

4. **속성** 창에서 **탭** 속성을 선택 하 고 줄임표 단추 (![ASP.NET mobile designer ellipse](../sharepoint/media/mwellipsis.gif "ASP.NET 모바일 디자이너 줄임표"))를 클릭 합니다.

     **탭 컬렉션 편집기** 가 나타납니다.

5. **탭 컬렉션 편집기**의 **멤버** 목록에서 이동할 탭을 선택 하 고 위로 또는 아래로 화살표를 클릭 하 여 탭 순서를 변경 합니다.

### <a name="to-position-a-tab-before-or-after-a-built-in-tab-on-the-ribbon"></a>리본의 기본 제공 탭 앞 이나 뒤에 탭을 배치 하려면

1. 리본 디자이너에서 사용자 지정 탭을 선택 합니다.

2. **속성** 창에서 **ControlId** 속성을 확장 한 다음 **고 controlidtype** 속성 값이 **Custom**으로 설정 되어 있는지 확인 합니다.

3. **속성** 창에서 **Position** 속성을 확장 합니다.

4. **PositionType** 속성을 적절 한 값으로 설정 합니다.

    - **BeforeOfficeId** 지정 된 기본 제공 탭 앞에 그룹을 배치 합니다.

    - **After트 id** 지정 된 기본 제공 탭 뒤에 그룹을 배치 합니다.

5. 이 속성을 기본 제공 탭의 컨트롤 ID로 **설정 합니다.**

     컨트롤 Id 목록은 [office 2010 도움말 파일: office 흐름 사용자 인터페이스 제어 식별자](https://www.microsoft.com/download/details.aspx?id=6627)를 참조 하세요.

## <a name="see-also"></a>참고 항목
- [리본 개요](../vsto/ribbon-overview.md)
- [리본 디자이너](../vsto/ribbon-designer.md)
- [리본 XML](../vsto/ribbon-xml.md)
- [연습: 리본 디자이너를 사용 하 여 사용자 지정 탭 만들기](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [연습: 리본 XML을 사용 하 여 사용자 지정 탭 만들기](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
