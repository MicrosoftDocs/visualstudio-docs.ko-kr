---
title: 'Convert: 다른 형식에 대 한 SharePoint 프로젝트 시스템 형식'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project service
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 40ea60a8df5bc0bcd033c60a83d742ed3249cc53
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "66835993"
---
# <a name="convert-between-sharepoint-project-system-types-and-other-visual-studio-project-types"></a>SharePoint 프로젝트 시스템 형식과 기타 Visual Studio 프로젝트 형식 간의 변환
  일부 경우에는 SharePoint 프로젝트 시스템에 개체가 있고 Visual Studio 자동화 개체 모델 또는 통합 개체 모델에서 해당 개체의 기능을 사용 하려는 경우 또는 그 반대의 경우도 있습니다. 이러한 경우 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> SharePoint 프로젝트 서비스의 메서드를 사용 하 여 개체를 다른 개체 모델로 변환할 수 있습니다.

 예를 들어 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> 개체가 있지만 또는 개체에만 사용할 수 있는 메서드를 사용 하려는 경우가 있습니다 <xref:EnvDTE.Project> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> . 이 경우 메서드를 사용 하 여를 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> 또는로 변환할 수 있습니다 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> <xref:EnvDTE.Project> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> .

 Visual Studio 자동화 개체 모델 및 Visual Studio 통합 개체 모델에 대 한 자세한 내용은 [SharePoint 도구 확장의 프로그래밍 모델 개요](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)를 참조 하세요.

## <a name="types-of-conversions"></a>변환 유형
 다음 표에서는이 메서드가 SharePoint 프로젝트 시스템과 다른 Visual Studio 개체 모델 간에 변환할 수 있는 형식을 나열 합니다.

|SharePoint 프로젝트 시스템 유형|자동화 및 통합 개체 모델의 해당 형식|
|------------------------------------|-------------------------------------------------------------------------|
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>|<xref:EnvDTE.Project><br /><br /> 또는<br /><br /> 프로젝트에 대 한 기본 COM 개체에 의해 구현 되는 Visual Studio 통합 개체 모델의 모든 인터페이스입니다. 이러한 인터페이스에는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> , <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> (또는 파생 인터페이스) 및가 포함 됩니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> . 프로젝트에 의해 구현 되는 기본 인터페이스 목록은 [프로젝트 모델 핵심 구성 요소](../extensibility/internals/project-model-core-components.md)를 참조 하세요.|
|<xref:Microsoft.VisualStudio.SharePoint.IMappedFolder><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFile><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeature><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeatureResourceFile><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectPackage>|<xref:EnvDTE.ProjectItem><br /><br /> 또는<br /><br /> 이를 포함 하는의 <xref:System.UInt32> 프로젝트 멤버를 식별 하는 값 (VSITEMID이 라고도 함)입니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> . 이 값은 일부 메서드의 *itemid* 매개 변수에 전달 될 수 있습니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> .|

## <a name="example"></a>예
 다음 코드 예제에서는 메서드를 사용 하 여 개체를로 변환 하는 방법을 보여 줍니다 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> <xref:EnvDTE.Project> .

 [!code-csharp[SPExtensibility.ProjectService.FromDTE#2](../sharepoint/codesnippet/CSharp/spprojectserviceaddin/connect.cs#2)]
 [!code-vb[SPExtensibility.ProjectService.FromDTE#2](../sharepoint/codesnippet/VisualBasic/spprojectserviceaddin/connect.vb#2)]

 이 예제에는 다음 사항이 필요합니다.

- *EnvDTE.dll* 어셈블리에 대 한 참조를 포함 하는 SharePoint 프로젝트 시스템의 확장입니다. 자세한 내용은 [SharePoint 프로젝트 시스템 확장](../sharepoint/extending-the-sharepoint-project-system.md)을 참조 하세요.

- `projectService_ProjectAdded`개체의 이벤트를 처리 하는 메서드를 등록 하는 코드입니다 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectAdded> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> . 예제는 [방법: SharePoint 프로젝트 확장 만들기](../sharepoint/how-to-create-a-sharepoint-project-extension.md)를 참조 하세요.

## <a name="see-also"></a>추가 정보

- [SharePoint 프로젝트 서비스 사용](../sharepoint/using-the-sharepoint-project-service.md)
- [방법: SharePoint 프로젝트 서비스 검색](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md)
- [SharePoint 도구 확장의 프로그래밍 모델 개요](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)
