---
title: '방법: 리본 그룹에 대화 상자 표시 아이콘 추가'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- dialog box launcher [Office development in Visual Studio]
- Ribbon [Office development in Visual Studio], dialog box launcher
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 29b260929d0478749296496db5b454326497d3ad
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85541622"
---
# <a name="how-to-add-a-dialog-box-launcher-to-a-ribbon-group"></a>방법: 리본 그룹에 대화 상자 표시 아이콘 추가
  리본 메뉴의 그룹에 대화 상자 표시 아이콘을 추가할 수 있습니다. 대화 상자 표시 아이콘은 그룹에 표시 되는 작은 아이콘입니다. 사용자가이 아이콘을 클릭 하면 그룹과 관련 된 추가 옵션을 제공 하는 관련 대화 상자 또는 작업창을 열 수 있습니다.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-add-a-dialog-box-launcher-to-a-ribbon-group"></a>리본 그룹에 대화 상자 표시 아이콘을 추가 하려면

1. **솔루션 탐색기**에서 리본 코드 파일 (*.vb* 또는 *.cs* 파일)을 선택 합니다.

2. **보기** 메뉴에서 **디자이너**를 클릭 합니다.

3. 리본 디자이너에서 그룹을 마우스 오른쪽 단추로 클릭 한 다음 **DialogBoxLauncher 아이콘 추가**를 클릭 합니다.

     그룹의 이벤트에 코드를 추가 <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup.DialogLauncherClick> 하 여 사용자 지정 또는 기본 제공 대화 상자를 엽니다.

## <a name="see-also"></a>참조
- [리본 개요](../vsto/ribbon-overview.md)
- [런타임에 리본 메뉴에 액세스](../vsto/accessing-the-ribbon-at-run-time.md)
- [Office 개발 샘플 및 연습](../vsto/office-development-samples-and-walkthroughs.md)
- [리본 디자이너](../vsto/ribbon-designer.md)
- [리본 개체 모델 개요](../vsto/ribbon-object-model-overview.md)
- [리본 XML](../vsto/ribbon-xml.md)
- [방법: 리본 디자이너에서 리본 XML로 리본 내보내기](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)
- [방법: 리본의 탭 위치 변경](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)
- [방법: 기본 제공 탭 사용자 지정](../vsto/how-to-customize-a-built-in-tab.md)
- [방법: backstage 보기에 컨트롤 추가](../vsto/how-to-add-controls-to-the-backstage-view.md)
- [Outlook에 대 한 리본 사용자 지정](../vsto/customizing-a-ribbon-for-outlook.md)
- [방법: 리본 메뉴 사용자 지정 시작](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [방법: 추가 기능 사용자 인터페이스 오류 표시](../vsto/how-to-show-add-in-user-interface-errors.md)
- [연습: 리본 디자이너를 사용 하 여 사용자 지정 탭 만들기](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [연습: 런타임에 리본 메뉴의 컨트롤 업데이트](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)
- [연습: 리본 XML을 사용 하 여 사용자 지정 탭 만들기](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
