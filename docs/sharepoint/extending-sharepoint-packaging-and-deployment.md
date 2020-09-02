---
title: SharePoint 패키징 및 배포 확장 | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4bb98e2b1c83ff06570a77dc84ce6a7bf690f81d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62967466"
---
# <a name="extend-sharepoint-packaging-and-deployment"></a>SharePoint 패키징 및 배포 확장
  SharePoint 프로젝트의 패키징 및 배포 프로세스를 확장할 수 있습니다.

## <a name="create-deployment-steps"></a>배포 단계 만들기
 SharePoint 프로젝트를 배포하면 [!INCLUDE[vs_current_short](../sharepoint/includes/vs-current-short-md.md)]에서 일련의 배포 단계를 실행합니다. Visual Studio에는 솔루션 제거 및 추가와 같은 여러 작업에 대한 기본 제공 배포 단계가 포함되어 있지만 고유한 배포 단계를 직접 만들 수도 있습니다.

 배포 단계를 만드는 방법을 보여 주는 연습은 [연습: SharePoint 프로젝트에 대 한 사용자 지정 배포 단계 만들기](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)를 참조 하세요.

## <a name="create-deployment-configurations"></a>배포 구성 만들기
 배포 구성은 지정된 프로젝트에 대해 실행되지만 모든 SharePoint 프로젝트 항목에 영향을 미칠 수 있는 일련의 배포 단계입니다. 각 배포 구성에는 프로젝트 배포 시 실행되는 일련의 단계와 프로젝트 취소 시 실행되는 일련의 단계가 포함되어 있습니다. [!INCLUDE[vs_current_short](../sharepoint/includes/vs-current-short-md.md)] 에는 두 가지 기본 제공 배포 구성이 포함 되어 있지만 직접 만들 수도 있습니다. 배포 구성을 만들 때 기본 제공 배포 단계와 직접 만든 배포 단계를 포함할 수 있습니다.

 배포 구성을 만드는 방법을 보여 주는 연습은 [연습: SharePoint 프로젝트에 대 한 사용자 지정 배포 단계 만들기](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)를 참조 하세요.

## <a name="run-code-when-a-sharepoint-solution-is-deployed-or-retracted"></a>SharePoint 솔루션이 배포 되거나 취소 될 때 코드 실행
 SharePoint 솔루션이 배포되거나 취소될 때 이벤트를 처리하여 추가 작업을 수행할 수 있습니다. Visual Studio에서는 다음 시나리오에서 처리할 수 있는 이벤트를 발생시킵니다.

- SharePoint 프로젝트 항목에 대한 각 배포 단계가 실행되기 전후. 자세한 내용은 [방법: 배포 단계가 실행 될 때 코드 실행](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)을 참조 하세요.

- SharePoint 프로젝트가 배포되거나 취소되기 전후. 자세한 내용은 [방법: SharePoint 프로젝트가 배포 되거나 취소 될 때 코드 실행](../sharepoint/how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted.md)을 참조 하세요.

## <a name="handle-deployment-conflicts"></a>배포 충돌 처리
 모듈, 웹 파트, 목록 인스턴스 및 콘텐츠 형식과 같은 SharePoint 프로젝트 항목의 일부 형식은 배포 충돌 해결을 기본적으로 제공합니다. 이러한 프로젝트 항목 중 하나가 포함된 솔루션을 배포하는 경우 Visual Studio에서는 먼저 배포할 항목의 파일과 같은 이름, URL 또는 ID를 가진 파일이 SharePoint 사이트에 이미 있는지 여부를 확인합니다. 충돌이 있는 경우 Visual Studio에서 자동으로 충돌을 해결할 수 있습니다. 또는 Visual Studio에서 충돌을 해결하거나 배포를 취소하도록 할지를 묻는 메시지가 표시될 수도 있습니다. 자세한 내용은 [Troubleshooting SharePoint Packaging and Deployment](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md)을 참조하세요.

 배포 충돌을 확인하고 해결하는 사용자 고유의 코드를 제공하여 이 기능을 확장할 수 있습니다. 자세한 내용은 [방법: 배포 충돌 처리](../sharepoint/how-to-handle-deployment-conflicts.md)를 참조 하세요.

## <a name="run-command-line-operations-before-or-after-a-project-is-deployed"></a>프로젝트를 배포 하기 전이나 후에 명령줄 작업을 실행 합니다.
 SharePoint 솔루션이 배포될 때 명령줄 작업을 실행하려는 경우 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> 개체의 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.PreDeploymentCommand%2A> 및 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.PostDeploymentCommand%2A> 속성을 설정할 수 있습니다. Visual Studio에서는 프로젝트가 배포되기 전후에 이러한 명령을 실행합니다.

 경우에 따라 배포 충돌이 발생할 수 있습니다. 충돌을 해결하는 방법에는 여러 가지가 있습니다. 자세한 내용은 [SharePoint 패키징 및 배포 문제 해결](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md)을 참조 하세요.

## <a name="customize-validation-rules"></a>유효성 검사 규칙 사용자 지정
 솔루션 패키지(.wsp)를 배포하기 전에 사용자 지정 기능 및 패키지 유효성 검사 규칙을 만들어 기능 또는 패키지가 유효한지 확인할 수 있습니다. 예를 들어, 정보, 경고 또는 오류를 개발자에게 보고하여 개발자가 유효성 검사 문제를 해결하는 데 도움을 줄 수 있습니다. 자세한 내용은 [방법: SharePoint 솔루션에 대 한 사용자 지정 기능 및 패키지 유효성 검사 규칙 만들기](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md)를 참조 하세요.

## <a name="see-also"></a>추가 정보
- [방법: 배포 단계가 실행 될 때 코드 실행](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)
- [연습: SharePoint 프로젝트에 대 한 사용자 지정 배포 단계 만들기](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)
- [방법: SharePoint 솔루션에 대 한 사용자 지정 기능 및 패키지 유효성 검사 규칙 만들기](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md)
- [SharePoint 프로젝트 시스템 확장](../sharepoint/extending-the-sharepoint-project-system.md)
