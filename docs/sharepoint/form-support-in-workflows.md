---
title: 워크플로에서 양식 지원 | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, workflows
- workflows [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b064df6729b914af7758cde86b03b886fd0e5d26
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72986257"
---
# <a name="form-support-in-workflows"></a>워크플로의 폼 지원
  워크플로에서는 연결, 시작, 작업 및 수정과 같은 네 가지 형식의 폼을 사용할 수 있습니다. 이러한 양식 유형은 ASPX 양식 또는 InfoPath 양식 중 하나를 기반으로 할 수 있습니다. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]특정 양식에 대해 제공 하는 지원 수준은 다음 표에 설명 된 여러 가지 요인에 따라 달라 집니다. 워크플로 양식 형식에 대 한 자세한 내용은 [워크플로 양식 개요](/previous-versions/office/developer/sharepoint-2010/ms457061(v=office.14))를 참조 하세요.

## <a name="xml-refactoring"></a>XML 리팩터링
 워크플로 프로젝트 항목에 ASPX 연결 또는 초기화 양식을 추가 하는 경우 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 양식 이름이 나 배포 경로를 업데이트 하거나 양식을 삭제할 때마다에서 연결 또는 시작 폼을 참조 하는 특성을 동기화 된 상태로 유지 하기 위해에서 자동으로 리팩터링 파일 *Elements.xml* 의 XML을 합니다. 그러나 워크플로에서 다른 양식 유형을 사용 하는 경우 (예: 작업 또는 수정 양식) *Elements.xml* 파일을 리팩터링할 수 없습니다.

## <a name="form-support-in-new-visual-studio-workflows"></a>새 Visual Studio 워크플로에서 양식 지원
 다음 표에서는 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 에서 만든 워크플로의 ASPX 또는 InfoPath 양식에서 다양 한 양식 형식에 대 한 지원을 보여 줍니다 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

|양식 형식|ASPX 폼을 사용 하 여 Visual Studio에서 만든 워크플로|InfoPath 폼을 사용 하 여 Visual Studio에서 만든 워크플로|
|---------------|---------------------------------------------------------|-----------------------------------------------------------------|
|연결|- **워크플로 연결 양식** 항목 템플릿을 사용 하 여 워크플로에 ASPX 연결 양식을 추가할 수 있습니다.<br />-폼을 추가, 이름 변경 또는 삭제 하거나 배포 경로가 변경 되 면 워크플로의 *Elements.xml* 파일을 리팩터링할 수 있습니다.<br />-자세한 내용은 [연습: 연결 및 초기화 폼이 있는 워크플로 만들기](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)를 참조 하세요.|-에 InfoPath 연결 양식 템플릿이 없습니다 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .<br />-와 InfoPath 디자이너 간의 통합은 없습니다 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .<br />-워크플로의 *Elements.xml* 파일을 리팩터링할 수 없습니다.|
|시작|- **워크플로 시작 양식** 항목 템플릿을 사용 하 여 워크플로에 ASPX 시작 양식을 추가할 수 있습니다.<br />-폼을 추가, 이름 변경 또는 삭제 하거나 배포 경로가 변경 되 면 워크플로의 *Elements.xml* 파일을 리팩터링할 수 있습니다.<br />-자세한 내용은 [연습: 연결 및 초기화 폼이 있는 워크플로 만들기](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)를 참조 하세요.|-에 InfoPath 연결 양식 템플릿이 없습니다 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .<br />-와 InfoPath 디자이너 간의 통합은 없습니다 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .<br />-워크플로의 *Elements.xml* 파일을 리팩터링할 수 없습니다.|
|Task|-에서 사용할 수 있는 ASPX 작업 폼 템플릿이 없습니다 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . 응용 프로그램 페이지를 만들고 여기에 코드를 추가 해야 합니다.<br />-워크플로의 *Elements.xml* 파일을 리팩터링할 수 없습니다.<br />-자세한 내용은 [워크플로 작업 양식 (SharePoint Foundation)](/previous-versions/office/developer/sharepoint-2010/ms438856(v=office.14)) 을 참조 하세요.|-에 InfoPath 작업 양식 템플릿이 없습니다 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .<br />-와 InfoPath 디자이너 간의 통합은 없습니다 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .<br />-워크플로의 *Elements.xml* 파일을 리팩터링할 수 없습니다.|
|수정|-에서 사용할 수 있는 ASPX 수정 양식 템플릿이 없습니다 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . 수정 양식을 추가 하려면 응용 프로그램 페이지를 만들고 여기에 코드를 추가 해야 합니다.<br />-워크플로의 *Elements.xml* 파일을 리팩터링할 수 없습니다. 필요에 따라 수동으로 편집 해야 합니다.<br />-자세한 내용은 [워크플로 수정 양식 (SharePoint Foundation)](/previous-versions/office/developer/sharepoint-2010/ms480794(v=office.14)) 을 참조 하세요.|-에 InfoPath 수정 양식 템플릿이 없습니다 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .<br />-와 InfoPath 디자이너 간의 통합은 없습니다 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .<br />-워크플로의 *Elements.xml* 파일을 리팩터링할 수 없습니다.|

## <a name="form-support-in-imported-sharepoint-reusable-workflows"></a>가져온 SharePoint 재사용 가능한 워크플로에서 양식 지원
 다음 표에서는 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 로 가져온 SharePoint 재사용 가능한 워크플로의 ASPX 또는 InfoPath 양식에서 다양 한 양식 형식에 대 한 지원을 나열 합니다 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

|양식 형식|SharePoint Designer에서 가져온 ASPX 양식이 있는 재사용 가능한 워크플로|SharePoint Designer에서 가져온 InfoPath 양식이 있는 재사용 가능한 워크플로|
|---------------|-------------------------------------------------------------------------------| - |
|연결|-폼은 워크플로의 *Elements.xml* 파일에서 참조 됩니다.<br />-양식의 이름이 바뀌거나 삭제 되거나 배포 경로가 변경 되 면 워크플로의 *Elements.xml* 파일이 리팩터링 됩니다.|-폼을 가져오지만 워크플로의 *Elements.xml* 에서 참조 하지 않습니다.<br />-워크플로의 *Elements.xml* 파일을 리팩터링할 수 없습니다.|
|시작|-워크플로에서 워크플로의 *Elements.xml* 파일에 있는 형식으로 참조 됩니다.<br />-양식의 이름이 바뀌거나 삭제 되거나 배포 경로가 변경 되 면 워크플로의 *Elements.xml* 파일이 리팩터링 됩니다.|-폼을 가져오지만 워크플로의 *Elements.xml* 에서 참조 하지 않습니다.<br />-워크플로의 *Elements.xml* 파일을 리팩터링할 수 없습니다. **참고:**  이 시나리오가 작동 하려면 규칙 및 속성을 추가 하 고 변경 해야 합니다.|
|Task|-폼은 워크플로의 *Elements.xml* 파일에서 참조 됩니다.<br />-워크플로의 *Elements.xml* 파일을 리팩터링할 수 없습니다.|-폼을 가져오지만 워크플로의 *Elements.xml* 에서 참조 하지 않습니다.<br />-워크플로의 *Elements.xml* 파일을 리팩터링할 수 없습니다. **참고:**  이 시나리오가 작동 하려면 규칙 및 속성을 추가 하 고 변경 해야 합니다.|
|수정|해당 사항 없음 SharePoint 디자이너에서는 ASPX 수정 양식을 만들 수 없습니다.|해당 사항 없음 SharePoint 디자이너에서는 SharePoint 디자이너에서 InfoPath 수정 양식을 만들 수 없습니다. 단, 워크플로를 내보낼 때 .wsp 파일에 포함 되지 않은 기본 제공 SharePoint 서버 워크플로는 제외 됩니다.|

## <a name="see-also"></a>참고 항목
- [연습: 연결 및 초기화 폼이 있는 워크플로 만들기](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)
- [SharePoint 워크플로 솔루션 만들기](../sharepoint/creating-sharepoint-workflow-solutions.md)
- [기존 SharePoint 사이트에서 항목 가져오기](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)
