---
title: Office UI 사용자 지정
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- menus [Office development in Visual Studio], customizing
- actions panes [Office development in Visual Studio], creating
- WPF [Office development in Visual Studio]
- toolbars [Office development in Visual Studio], customizing
- Office applications [Office development in Visual Studio], UI customization
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 257f87aedf5d4337e81fb6f251cc8df07f4e577c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "88041066"
---
# <a name="office-ui-customization"></a>Office UI 사용자 지정
  Visual Studio에서 Office 개발자 도구를 사용하여 Microsoft Office 애플리케이션의 UI(사용자 인터페이스)를 사용자 지정할 수 있습니다. 이 항목에서는 다음 섹션에서 사용자 지정할 수 있는 UI 기능에 대해 설명합니다.

- [UI 기능 비교](#Comparison)

- [작업 창 및 사용자 지정 작업창](#Actions)

- [사용자 지정 리본 UI](#Ribbon)

- [Backstage 보기](#Backstage)

- [Outlook 양식 영역](#FormRegion)

- [문서에 대 한 컨트롤](#Controls)

- [바로 가기 메뉴](#Shortcut)

## <a name="comparison-of-ui-features"></a><a name="Comparison"></a> UI 기능 비교
 다음 표에서는 Microsoft Office 프로젝트에서 사용자 지정할 수 있는 주요 UI 기능을 비교합니다.

|기능|지원되는 프로젝트 형식|지원되는 Microsoft Office 애플리케이션|
|-------------|-----------------------------|---------------------------------------------|
|작업 창|문서 수준 사용자 지정|Excel<br /><br /> Word|
|사용자 지정 작업창|VSTO 추가 기능|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)]<br /><br /> [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)]<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Word|
|사용자 지정 리본 UI|문서 수준 사용자 지정<br /><br /> VSTO 추가 기능|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)]<br /><br /> [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)]<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Project<br /><br /> Word<br /><br /> Visio|
|Backstage 보기|문서 수준 사용자 지정<br /><br /> VSTO 추가 기능|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)].<br /><br /> [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)]<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Project<br /><br /> Word<br /><br /> Visio|
|Outlook 양식 영역|VSTO 추가 기능|Outlook|
|문서의 컨트롤|문서 수준 사용자 지정<br /><br /> VSTO 추가 기능|Excel<br /><br /> Word|
|바로 가기 메뉴|문서 수준 사용자 지정<br /><br /> VSTO 추가 기능|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)]<br /><br /> [!INCLUDE[InfoPath_14_short](../vsto/includes/infopath-14-short-md.md)]<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Project<br /><br /> Word<br /><br /> Visio<br /><br /> Excel|

## <a name="actions-panes-and-custom-task-panes"></a><a name="Actions"></a> 작업 창 및 사용자 지정 작업창
 작업창은 일반적으로 Microsoft Office 애플리케이션에서 창의 한쪽에 도킹된 사용자 인터페이스 패널입니다. 거의 모든 Microsoft Office 애플리케이션에는 기본 제공 작업창이 포함되어 있습니다. 작업창의 예는 Word의 도움말 작업창입니다.

 Visual Studio의 Office 개발 도구에서는 두 가지 방법으로 작업창을 사용자 지정할 수 있습니다.

- 문서 수준 사용자 지정에 작업창을 추가할 수 있습니다. 기본적으로 작업창은 애플리케이션의 오른쪽에서 문서의 오른쪽에 표시됩니다. 그러나 작업창은 문서의 왼쪽, 위쪽 또는 아래쪽에도 표시될 수 있습니다.

- VSTO 추가 기능에 사용자 지정 작업창을 추가할 수 있습니다. 사용자는 애플리케이션 창의 원하는 쪽에 사용자 지정 작업창을 도킹하거나 창에서 임의의 위치로 사용자 지정 작업창을 끌 수 있습니다.

  작업창과 사용자 지정 작업창은 데이터 입력과 같은 작업에 유용한 다양한 컨트롤을 호스트하여 기능을 제공합니다. 리본 그룹에 비해 작업창과 사용자 지정 작업창은 텍스트와 컨트롤을 포함할 훨씬 더 큰 영역을 제공합니다.

  작업 창에 대 한 자세한 내용은 [작업 창 개요](../vsto/actions-pane-overview.md)를 참조 하세요. 사용자 지정 작업창에 대 한 자세한 내용은 [사용자 지정 작업 창](../vsto/custom-task-panes.md)을 참조 하세요.

## <a name="custom-ribbon-ui"></a><a name="Ribbon"></a> 사용자 지정 리본 UI
 Office에서 애플리케이션에 추가하는 기능을 노출하기 위해 리본 UI를 사용자 지정할 수 있습니다. 리본은 쉽게 찾을 수 있도록 관련된 명령을 컨트롤의 형태로 구성하는 방법입니다. 사용자가 솔루션에서 제공하는 기능에 액세스할 수 있도록 하기 위해 사용자 고유의 리본 탭 및 그룹을 만들 수 있습니다. 이전 버전의 Microsoft Office system에서 메뉴와 도구 모음을 사용하여 액세스하는 대부부분의 기능에 이제 리본을 사용하여 액세스할 수 있습니다.

 자세한 내용은 [리본 개요](../vsto/ribbon-overview.md)를 참조 하세요.

## <a name="backstage-view"></a><a name="Backstage"></a> Backstage 보기
 Office 응용 프로그램에서 **파일** 탭을 클릭 하면 Backstage 보기가 열립니다. Backstage 보기는 파일 수준 작업 및 동작을 결합하고 2007 Microsoft Office system의 Microsoft Office 단추에서 사용할 수 있는 유사한 기능을 대체하는 UI를 제공합니다. Backstage 보기는 XML을 사용하여 완전히 확장 가능합니다.

 Visual Studio에서는 Backstage 보기를 사용자 지정하기 위한 디자이너나 API를 제공하지 않습니다. 그러나 Office 프로젝트에 **리본 (xml)** 항목을 추가 하는 경우 리본 xml 파일에 xml을 추가 하 여 Backstage 보기를 사용자 지정할 수 있습니다. **리본 (xml)** 항목에 대 한 자세한 내용은 [리본 XML](../vsto/ribbon-xml.md)을 참조 하세요.

 Backstage 보기를 사용자 지정 하는 방법에 대 한 자세한 내용은 [개발자를 위한 office 2010 backstage 보기 소개](/previous-versions/office/developer/office-2010/ee691833(v=office.14)) 및 [개발자를 위한 office 2010 Backstage 보기 사용자 지정](/previous-versions/office/developer/office-2010/ee815851(v=office.14))을 참조 하세요.

## <a name="outlook-form-regions"></a><a name="FormRegion"></a> Outlook 양식 영역
 양식 영역을 사용하여 사용자 지정 기능을 표준 Microsoft Office Outlook 양식에 추가할 수 있습니다. 추가 필드나 컨트롤을 사용하여 기존 양식을 확장하는 양식 영역을 만들 수 있습니다. Visual Studio에서 Office 개발 도구를 사용하여 새 양식 영역을 만드는 경우 양식 영역에서 Windows Forms 컨트롤만 사용할 수 있습니다. Outlook에서 설계된 양식 영역을 가져오면 네이티브 Outlook 컨트롤만 사용할 수 있습니다.

 Outlook UI의 다양한 영역을 차지하는 양식 영역을 만들 수 있습니다. 예를 들어 인접 양식 영역은 양식의 첫 페이지 아래쪽에 표시되며 각 인접 양식 영역은 축소 가능합니다. 또한 전체 추가 양식 페이지로 표시되고 기존 표준 양식 또는 사용자 지정 양식에 나타날 수 있는 별도의 양식 영역을 추가할 수도 있습니다.

 자세한 내용은 [Outlook 양식 영역 만들기](../vsto/creating-outlook-form-regions.md)를 참조 하세요.

## <a name="controls-on-documents"></a><a name="Controls"></a> 문서에 대 한 컨트롤
 다양한 컨트롤을 Word 문서와 Excel 워크시트에 추가할 수 있습니다. 예를 들어 사용자가 표준 형식으로 날짜를 입력하거나 데이터베이스에 데이터를 보내기 위해 워크시트에 단추를 배치할 수 있도록 날짜 선택 컨트롤을 문서에 추가하려고 할 수 있습니다.

 Excel 또는 Word의 문서 수준 프로젝트를 개발하는 경우 디자인 타임에 Visual Studio 디자이너를 사용하여 프로젝트의 문서나 통합 문서에 컨트롤을 추가하거나 런타임에 프로그래밍 방식으로 컨트롤을 추가할 수 있습니다. Excel 또는 Word의 VSTO 추가 기능 프로젝트를 개발하는 경우 런타임에 열려 있는 문서나 통합 문서에 프로그래밍 방식으로 컨트롤을 추가할 수 있습니다.

 자세한 내용은 [호스트 항목 및 호스트 컨트롤 개요](../vsto/host-items-and-host-controls-overview.md) 및 [Office 문서의 Windows forms 컨트롤 개요](../vsto/windows-forms-controls-on-office-documents-overview.md)를 참조 하세요.

## <a name="shortcut-menus"></a><a name="Shortcut"></a> 바로 가기 메뉴
 바로 가기 메뉴는 문서 또는 애플리케이션 창에서 마우스 오른쪽 단추를 클릭할 때 나타납니다. 사용자가 문서, 통합 문서 또는 호스트 컨트롤을 마우스 오른쪽 단추로 클릭할 때와 같이 이벤트가 발생한 후 나타나도록 바로 가기 메뉴를 설정할 수 있습니다. 바로 가기 메뉴에 다양한 수의 메뉴 명령 또는 컨트롤을 추가할 수 있습니다. XML을 사용하여 바로 가기 메뉴를 만들 수 있습니다. Office 프로젝트에 **리본 (xml)** 항목을 추가 하는 경우 리본 xml 파일에 xml을 추가 하 여 바로 가기 메뉴를 만들 수 있습니다. XML을 사용 하 여 바로 가기 메뉴를 만드는 방법에 대 한 자세한 내용은 [방법: 바로 가기 메뉴에 명령 추가](../vsto/how-to-add-commands-to-shortcut-menus.md)를 참조 하세요.

## <a name="see-also"></a>추가 정보
- [리본 개요](../vsto/ribbon-overview.md)
- [Office 문서의 Windows forms 컨트롤 개요](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [작업 창 개요](../vsto/actions-pane-overview.md)
- [Outlook 양식 영역 만들기](../vsto/creating-outlook-form-regions.md)
- [사용자 지정 작업 창](../vsto/custom-task-panes.md)
- [Office 솔루션에서 WPF 컨트롤 사용](../vsto/using-wpf-controls-in-office-solutions.md)
- [방법: 리본 메뉴에 개발자 탭 표시](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)
- [방법: 추가 기능 사용자 인터페이스 오류 표시](../vsto/how-to-show-add-in-user-interface-errors.md)
- [연습: Windows form을 사용 하 여 데이터 수집](../vsto/walkthrough-collecting-data-using-a-windows-form.md)
