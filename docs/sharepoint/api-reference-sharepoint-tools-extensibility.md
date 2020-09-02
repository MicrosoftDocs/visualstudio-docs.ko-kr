---
title: API 참조 (SharePoint 도구 확장성) | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, reference for project and tools extensibility
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 37639068b74b5d99864871355a8b9ef36906f6cd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62987992"
---
# <a name="api-reference-sharepoint-tools-extensibility"></a>API 참조 (SharePoint 도구 확장성)
  이 섹션에는 Visual Studio에서 SharePoint 도구를 확장 하기 위한 API 참조 설명서가 포함 되어 있습니다.

## <a name="in-this-section"></a>섹션 내용
 <xref:Microsoft.VisualStudio.SharePoint>

 SharePoint 프로젝트 시스템을 확장 하는 데 사용 하는 형식을 포함 합니다. 예를 들어 기본 제공 SharePoint 프로젝트 및 프로젝트 항목을 확장하거나, 고유한 프로젝트 항목을 만들 수 있습니다.

 <xref:Microsoft.VisualStudio.SharePoint.Commands>

 사용자 지정 *SharePoint 명령을*만드는 데 사용할 수 있는 형식을 포함 합니다. SharePoint 명령은 SharePoint 도구 확장에서 SharePoint 서버 개체 모델을 호출하는 메서드입니다.

 <xref:Microsoft.VisualStudio.SharePoint.Deployment>

 SharePoint 프로젝트에 대 한 배포 프로세스를 확장 하는 데 사용 하는 형식을 포함 합니다.

 <xref:Microsoft.VisualStudio.SharePoint.Explorer>

 **서버 탐색기** 에서 SharePoint 노드를 확장 하거나 고유한 노드 유형을 정의 하는 데 사용 하는 형식을 포함 합니다.

 <xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions>

 목록, 필드 또는 콘텐츠 형식을 나타내는 노드와 같이 SharePoint 사이트의 개별 구성 요소를 나타내는 기본 제공 **서버 탐색기** 노드에 대 한 정보를 가져오는 데 사용할 수 있는 형식을 포함 합니다.

 <xref:Microsoft.VisualStudio.SharePoint.Features>

 SharePoint 프로젝트의 기능에 대한 정의에 액세스하는 데 사용하는 형식을 포함합니다.

 <xref:Microsoft.VisualStudio.SharePoint.Packages>

 SharePoint 프로젝트의 패키지 정의에 액세스 하는 데 사용 하는 형식을 포함 합니다.

 <xref:Microsoft.VisualStudio.SharePoint.Remote.Authentication>

 원격 SharePoint 사이트에 배포된 SharePoint용 응용 프로그램을 인증하고 통신하는 데 사용하는 형식을 포함합니다.

 <xref:Microsoft.VisualStudio.SharePoint.Remote.Commands>

 원격 SharePoint 사이트에 배포된 SharePoint용 응용 프로그램과 함께 사용되는 SharePoint 원격 명령을 만드는 데 사용하는 형식을 포함합니다.

 <xref:Microsoft.VisualStudio.SharePoint.Tasks>

 SharePoint 프로젝트, Office용 응용 프로그램 및 SharePoint용 응용 프로그램을 패키지하고 디버깅하기 위한 빌드 작업으로 Visual Studio에서 사용하는 형식을 포함합니다. 이 API는 Office 및 SharePoint 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

 <xref:Microsoft.VisualStudio.SharePoint.Validation>

 SharePoint 프로젝트의 기능 및 패키지 유효성 검사 동작을 사용자 지정하는 데 사용하는 형식을 포함합니다.

## <a name="see-also"></a>추가 정보
- [SharePoint 도구 확장성&#41;참조 &#40;](../sharepoint/reference-sharepoint-tools-extensibility.md)
- [SharePoint 도구 확장의 프로그래밍 모델 개요](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)
- [SharePoint 프로젝트 시스템 확장](../sharepoint/extending-the-sharepoint-project-system.md)
- [서버 탐색기에서 SharePoint 연결 노드 확장](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [SharePoint 패키징 및 배포 확장](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
- [SharePoint 개체 모델 호출](../sharepoint/calling-into-the-sharepoint-object-models.md)
