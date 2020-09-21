---
title: Office 응용 프로그램 및 프로젝트 형식에 따라 사용 가능한 기능
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio]
- Office development in Visual Studio, features
- Ribbon [Office development in Visual Studio]
- Office applications [Office development in Visual Studio], features available
- document-level customizations [Office development in Visual Studio]
- Office projects [Office development in Visual Studio], features available
- add-ins [Office development in Visual Studio]
- form regions [Office development in Visual Studio], features available
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 24344a643e9ec2b4a7bb90dc62df67209b3eb183
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90808183"
---
# <a name="features-available-by-office-application-and-project-type"></a>Office 응용 프로그램 및 프로젝트 형식에 따라 사용 가능한 기능
  Visual Studio에는 다음과 같은 형식을 비롯하여 Microsoft Office 애플리케이션에 대한 다양한 비즈니스 시나리오를 지원하는 몇 가지 프로젝트 템플릿 형식이 있습니다.

- 문서 수준 사용자 지정

- VSTO 추가 기능

  모든 애플리케이션이 모든 프로젝트 형식을 사용할 수 있는 것은 아닙니다. 예를 들어 문서 수준 프로젝트는 Microsoft Office Word 및 Microsoft Office Excel에만 사용할 수 있습니다. 마찬가지로 일부 기능은 특정 프로젝트 또는 애플리케이션 형식에만 사용할 수 있습니다. 예를 들어 작업창은 문서 수준 프로젝트에서만 사용할 수 있으며 리본 확장은 일부 애플리케이션에만 사용할 수 있습니다. 다양 한 프로젝트 형식에 대 한 자세한 내용은 [Office 솔루션 개발 개요 &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)를 참조 하세요.

> [!NOTE]
> Office 프로젝트 템플릿은 일부 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 버전에서만 사용할 수 있습니다. 자세한 내용은 [Office 솔루션을 개발할 수 있도록 컴퓨터 구성](../vsto/configuring-a-computer-to-develop-office-solutions.md)을 참조 하세요.

## <a name="project-types-available-for-different-microsoft-office-applications"></a>다양 한 Microsoft Office 응용 프로그램에 사용할 수 있는 프로젝트 형식
 다음 표에서는 각 프로젝트 형식과 함께 사용할 수 있는 애플리케이션을 보여 줍니다.

|프로젝트 형식|Microsoft Office 애플리케이션|
|-------------------|----------------------------------|
|문서 수준 사용자 지정|Excel<br /><br /> Word|
|VSTO 추가 기능|Excel<br /><br /> InfoPath(InfoPath 2013 및 InfoPath 2010만 해당)<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Project<br /><br /> Visio<br /><br /> Word<br /><br /> Excel|

## <a name="features-available-in-different-project-types"></a>다양 한 프로젝트 형식에서 사용할 수 있는 기능
 다음 표에서는 각 기능을 제공하는 프로젝트 형식을 보여 줍니다.

|기능|기능을 제공하는 프로젝트 형식|추가 정보|
|-------------|--------------------------------------------|---------------------|
|작업창|문서 수준 프로젝트|[작업 창 개요](../vsto/actions-pane-overview.md)|
|ClickOnce 배포.|VS 및 문서 수준 프로젝트|[Office 솔루션 배포](../vsto/deploying-an-office-solution.md)|
|사용자 지정 작업창|다음 애플리케이션의 VSTO 추가 기능 프로젝트:<br /><br /> -Excel<br />-InfoPath (InfoPath 2013 및 InfoPath 2010에만 해당)<br />-Outlook<br />-PowerPoint<br />-Word|[사용자 지정 작업 창](../vsto/custom-task-panes.md)|
|사용자 지정 XML 부분|문서 수준 프로젝트<br /><br /> 다음 애플리케이션의 애플리케이션 수준 프로젝트:<br /><br /> -Excel<br />-PowerPoint<br />-Word|[사용자 지정 XML 부분 개요](../vsto/custom-xml-parts-overview.md)|
|데이터 캐시|문서 수준 프로젝트|[문서 수준 사용자 지정의 캐시 된 데이터](../vsto/cached-data-in-document-level-customizations.md)|
|VSTO 추가 기능의 개체를 다른 Microsoft Office 솔루션에 노출 합니다.|VSTO 추가 기능 프로젝트|[다른 Office 솔루션에서 VSTO 추가 기능의 코드 호출](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)|
|다음 호스트 컨트롤:<br /><br /> -차트<br />-ListObject<br />-NamedRange<br />-콘텐츠 컨트롤<br />-책갈피|문서 수준 프로젝트<br /><br /> Word 및 Excel의 VSTO 추가 기능 프로젝트|[호스트 항목 및 호스트 컨트롤 개요](../vsto/host-items-and-host-controls-overview.md)|
|다음 호스트 컨트롤:<br /><br /> -XMLMappedRange<br />-XMLNode<br />-XMLNodes|문서 수준 프로젝트|[호스트 항목 및 호스트 컨트롤 개요](../vsto/host-items-and-host-controls-overview.md)|
|다중 프로젝트 배포|문서 수준 프로젝트<br /><br /> VSTO 추가 기능 프로젝트|[연습: 단일 ClickOnce 설치 관리자에서 여러 Office 솔루션 배포](/previous-versions/dd465290(v=vs.110))|
|Outlook 양식 영역|Outlook의 VSTO 추가 기능 프로젝트|[Outlook 양식 영역 만들기](../vsto/creating-outlook-form-regions.md)|
|배포 후 작업|문서 수준 프로젝트<br /><br /> VSTO 추가 기능 프로젝트|[연습: ClickOnce 설치 후 최종 사용자 컴퓨터에 문서 복사](/previous-versions/dd465291(v=vs.110))|
|리본 사용자 지정|문서 수준 프로젝트<br /><br /> 다음 애플리케이션의 VSTO 추가 기능 프로젝트:<br /><br /> -Excel<br />-InfoPath (InfoPath 2013 및 InfoPath 2010에만 해당)<br />-Outlook<br />-PowerPoint<br />-프로젝트<br />-Visio<br />-Word|[리본 개요](../vsto/ribbon-overview.md)|
|시각적 문서 디자이너|문서 수준 프로젝트|[Visual Studio 환경의 Office 프로젝트](../vsto/office-projects-in-the-visual-studio-environment.md)|

## <a name="see-also"></a>추가 정보
- [Visual Studio에서 Office 개발 &#40;시작&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Office 솔루션 개발 개요 &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [작업 창 개요](../vsto/actions-pane-overview.md)
- [리본 개요](../vsto/ribbon-overview.md)
- [Outlook 양식 영역 만들기](../vsto/creating-outlook-form-regions.md)
- [호스트 항목 및 호스트 컨트롤 개요](../vsto/host-items-and-host-controls-overview.md)
- [문서 수준 사용자 지정의 캐시 된 데이터](../vsto/cached-data-in-document-level-customizations.md)
- [Office 솔루션 배포](../vsto/deploying-an-office-solution.md)