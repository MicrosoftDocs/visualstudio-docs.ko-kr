---
title: '방법: 기본 제공 탭 사용자 지정'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], tabs
- built-in tabs [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5f73ec7a8555a5e5d569d4316ca619747550bf11
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547188"
---
# <a name="how-to-customize-a-built-in-tab"></a>방법: 기본 제공 탭 사용자 지정
  기본 제공 탭에 그룹 및 컨트롤을 추가할 수 있습니다. 기본 제공 탭은 Microsoft Office 응용 프로그램의 리본에 이미 있는 탭입니다. 예를 들어 **데이터** 탭은 Excel의 기본 제공 탭입니다. 사용자 지정 그룹을 만드는 경우 탭에서 마지막에 표시되지만 탭의 아무곳으로나 그룹을 이동할 수 있습니다.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

> [!NOTE]
> 기본 제공 탭에 그룹을 추가할 수 있지만 기본 제공 탭에서 기본 제공 그룹을 제거할 수는 없습니다.

### <a name="to-add-groups-to-a-built-in-tab"></a>기본 제공 탭에 그룹을 추가하려면

1. **솔루션 탐색기**에서 리본 코드 파일을 마우스 오른쪽 단추로 클릭 한 다음 **디자이너 보기**를 클릭 합니다.

    > [!NOTE]
    > 리본 코드 파일이 **솔루션 탐색기**에 표시 되지 않으면 프로젝트에 **리본 항목** 을 추가 해야 합니다. [방법: 리본 메뉴 사용자 지정 시작을](../vsto/how-to-get-started-customizing-the-ribbon.md)참조 하세요.

2. 리본 디자이너에서 탭을 마우스 오른쪽 단추로 클릭 한 다음 **속성**을 클릭 합니다.

3. **속성** 창에서 **ControlId** 속성을 확장 한 다음 **고 controlidtype** 속성을 **Office**로 설정 합니다.

4. 사용자 지정 하려는 기본 제공 탭의 *컨트롤 id* 로 사용자 **id** 속성을 설정 합니다.

     컨트롤 ID는 Microsoft Office 애플리케이션에 기본 제공된 탭, 그룹 및 컨트롤을 고유하게 식별하는 이름입니다.

     컨트롤 Id 목록은 [office 2010 도움말 파일: office 흐름 사용자 인터페이스 제어 식별자](https://www.microsoft.com/download/details.aspx?id=6627)를 참조 하세요.

5. **도구 상자**의 **Office 리본 컨트롤** 탭에서 그룹을 탭으로 끌어옵니다.

    > [!NOTE]
    > 기본 제공 그룹은 디자이너에 표시되지 않습니다. 따라서 기본 제공 탭으로 작업 하는지 여부를 확인 하는 유일한 방법은 탭의 **ControlId** 속성을 검사 하는 것입니다.

### <a name="to-position-groups-on-a-built-in-tab"></a>기본 제공 탭에 그룹을 배치하려면

1. 리본 디자이너에서 사용자 지정 그룹을 선택합니다.

2. **속성** 창에서 **Position** 속성을 확장 합니다.

3. **PositionType** 속성을 적절 한 값으로 설정 합니다.

    - **BeforeOfficeId** 지정 된 기본 제공 그룹 앞에 그룹을 배치 합니다.

    - **After트 id** 는 지정 된 기본 제공 그룹 뒤에 그룹을 배치 합니다.

4. 로 구성 **된 속성을** 기본 제공 그룹의 컨트롤 id로 설정 합니다.

     컨트롤 Id 목록은 [office 2010 도움말 파일: office 흐름 사용자 인터페이스 제어 식별자](https://www.microsoft.com/download/details.aspx?id=6627)를 참조 하세요.

## <a name="see-also"></a>참조
- [리본 개요](../vsto/ribbon-overview.md)
- [리본 디자이너](../vsto/ribbon-designer.md)
- [리본 XML](../vsto/ribbon-xml.md)
- [연습: 리본 디자이너를 사용 하 여 사용자 지정 탭 만들기](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [연습: 리본 XML을 사용 하 여 사용자 지정 탭 만들기](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
- [방법: 리본 메뉴 사용자 지정 시작](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [방법: 리본의 탭 위치 변경](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)
- [방법: Backstage 보기에 컨트롤 추가](../vsto/how-to-add-controls-to-the-backstage-view.md)
- [방법: 추가 기능 사용자 인터페이스 오류 표시](../vsto/how-to-show-add-in-user-interface-errors.md)
