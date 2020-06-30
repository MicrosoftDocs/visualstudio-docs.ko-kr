---
title: '방법: Backstage 보기에 컨트롤 추가 '
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- customizing the Ribbon, menus
- controls, Ribbon
- menus, customizing
- Microsoft Office Button
- custom Ribbon, menus
- Ribbon, customizing
- Office button
- Ribbon, menus
- Microsoft Office Menu
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5b4ea5cdcd869f16f987e9431359511831af9573
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85538348"
---
# <a name="how-to-add-controls-to-the-backstage-view"></a>방법: Backstage 보기에 컨트롤 추가
  리본 디자이너를 사용 하 여 **파일** 탭을 클릭할 때 열리는 메뉴에 컨트롤을 추가할 수 있습니다. 응용 프로그램을 실행 하면 **파일** 탭에 추가 하는 컨트롤이 **추가 기능**이라는 그룹으로 표시 됩니다.

 Visual Studio의 리본 디자이너를 사용 하 여 기본 제공 컨트롤 전후에 컨트롤을 배치할 수 없습니다. 기본 제공 컨트롤은 Backstage 보기에 이미 표시 된 컨트롤입니다. 기본 제공 컨트롤 전후에 컨트롤을 배치 하려면 리본 XML을 사용 해야 합니다. **리본 (xml)** 에 대 한 자세한 내용은 [리본 XML](../vsto/ribbon-xml.md)을 참조 하세요. Backstage 보기를 사용자 지정 하는 방법에 대 한 자세한 내용은 [개발자를 위한 office 2010 backstage 보기 소개](/previous-versions/office/developer/office-2010/ee691833(v=office.14)) 및 [개발자를 위한 office 2010 Backstage 보기 사용자 지정](/previous-versions/office/developer/office-2010/ee815851(v=office.14))을 참조 하세요.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-add-controls-to-backstage-view"></a>Backstage 보기에 컨트롤을 추가 하려면

1. 디자인 뷰에서 리본 항목을 엽니다.

     **리본 (비주얼 디자이너)** 항목을 프로젝트에 추가 하는 방법에 대 한 자세한 내용은 [방법: 리본 메뉴 사용자 지정 시작](../vsto/how-to-get-started-customizing-the-ribbon.md)을 참조 하세요.

2. 리본 디자이너에서 **파일** 탭을 클릭 합니다.

     메뉴 디자이너가 나타납니다. 이 디자인 화면에는 컨트롤이 포함 되어 있지 않습니다.

3. **도구 상자**의 **Office 리본 컨트롤** 탭에서 다음 컨트롤 중 하나를 메뉴 디자이너로 끌어 옵니다.

    - 단추

    - CheckBox

    - 갤러리

    - 메뉴

    - 구분 기호

    - SplitButton

    - ToggleButton

4. 컨트롤을 끌어 메뉴의 새 위치로 이동 합니다.

## <a name="see-also"></a>참고 항목
- [리본 개요](../vsto/ribbon-overview.md)
- [리본 디자이너](../vsto/ribbon-designer.md)
- [리본 XML](../vsto/ribbon-xml.md)
- [방법: 리본 메뉴 사용자 지정 시작](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [연습: 리본 디자이너를 사용 하 여 사용자 지정 탭 만들기](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
