---
title: Visual Studio에서 SharePoint 도구 확장 | Microsoft Docs
ms.date: 02/02/2017
ms.topic: overview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Studio, extending tools
- extensibility [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, extending tools
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7dc0cc0d0af73d032d870629877b62c94e6b347b
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: ko-KR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016036"
---
# <a name="extend-the-sharepoint-tools-in-visual-studio"></a>Visual Studio에서 SharePoint 도구 확장
  Visual Studio의 SharePoint 도구는 다양 한 응용 프로그램 개발 시나리오의 요구 사항을 충족 합니다. 그러나 사용자나 다른 개발자가 필요로 하는 기능을 제공 하지 않는 경우를 발견할 수 있습니다. 이러한 경우 SharePoint 도구를 확장 하 여 필요한 기능을 만들 수 있습니다.

## <a name="how-to-extend-the-sharepoint-tools"></a>SharePoint 도구를 확장 하는 방법
 **서버 탐색기** 창에서 sharepoint 프로젝트 시스템 및 **sharepoint 연결** 노드를 확장할 수 있습니다.

### <a name="extend-the-sharepoint-project-system"></a>SharePoint 프로젝트 시스템 확장
 Visual Studio에는 SharePoint 솔루션을 만드는 데 사용할 수 있는 프로젝트 템플릿 및 항목 템플릿 집합이 포함 되어 있습니다. 예를 들어 이벤트 수신자, 목록 정의, 워크플로 및 웹 파트에 대 한 템플릿이 있습니다. 그러나 필드 또는 사용자 지정 작업과 같은 SharePoint 구성 요소를 만들기 위해 고유한 형식의 SharePoint 프로젝트 항목을 정의할 수도 있습니다. 또한 Visual Studio에 이미 설치 되어 있는 SharePoint 프로젝트 항목 형식에 대 한 확장을 만들 수 있으며, SharePoint 프로젝트용 확장을 만들 수 있습니다.

 자세한 내용은 [SharePoint 프로젝트 시스템 확장](../sharepoint/extending-the-sharepoint-project-system.md)을 참조 하세요.

### <a name="extend-the-sharepoint-connections-node-in-server-explorer"></a>서버 탐색기에서 SharePoint 연결 노드 확장
 Visual Studio에서는 **서버 탐색기** 창의 **sharepoint 연결** 노드를 사용 하 여 하나 이상의 로컬 sharepoint 사이트의 여러 구성 요소를 계층적 트리 보기에서 볼 수 있습니다. 다음과 같은 방법으로 **SharePoint 연결** 노드를 확장할 수도 있습니다.

- 사용자 고유의 노드를 추가 합니다. 이 기능은 기본적으로 표시 되지 않는 SharePoint 사이트의 구성 요소를 표시 하려는 경우에 유용 합니다.

- 기존 노드를 확장 합니다. 예를 들어 기존 노드에 새 자식 노드를 추가 하거나, 개발자가 메뉴 항목을 클릭할 때 노드에 바로 가기 메뉴 항목을 추가 하 고 작업을 수행할 수 있습니다.

  자세한 내용은 [서버 탐색기에서 SharePoint 연결 노드 확장](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)을 참조 하세요.

## <a name="development-computer-requirements"></a>개발 컴퓨터 요구 사항
 SharePoint 도구에 대 한 확장을 만들려면 개발 컴퓨터가 Visual Studio에서 SharePoint 솔루션을 만들 때와 동일한 요구 사항을 충족 해야 합니다.

 또한를 설치 하는 것이 좋습니다 [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)] . SDK에는 Visual Studio를 확장 하는 데 사용할 수 있는 프로젝트 템플릿과 도구가 포함 되어 있습니다. 특히 SDK에는 VSIX (Visual Studio Extension) 패키지를 쉽게 만드는 데 사용할 수 있는 프로젝트 템플릿이 포함 되어 있습니다. VSIX 패키지는 visual studio에서 visual Studio 확장을 배포 하는 데 선호 되는 방법입니다. 모든 SharePoint 도구 확장은 VSIX 패키지를 사용 하 여 배포 해야 합니다. 이 설명서의 모든 연습에서는가 설치 되어 있다고 가정 합니다 [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)] .

 Visual Studio SDK를 설치 하려면 [Visual STUDIO Sdk 설치](../extensibility/installing-the-visual-studio-sdk.md)를 참조 하세요. Visual Studio 확장에 대 한 자세한 내용은 [Visual Studio 확장 개발 시작](../extensibility/starting-to-develop-visual-studio-extensions.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목

- [SharePoint 도구 확장의 프로그래밍 모델 개요](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)
- [SharePoint 프로젝트 시스템 확장](../sharepoint/extending-the-sharepoint-project-system.md)
- [서버 탐색기에서 SharePoint 연결 노드 확장](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [SharePoint 도구 확장의 프로그래밍 개념 및 기능](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)
- [SharePoint 도구 확장성&#41;참조 &#40;](../sharepoint/reference-sharepoint-tools-extensibility.md)
- [Visual Studio의 SharePoint 도구에 대 한 디버그 확장](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)
- [Visual Studio에서 SharePoint 도구에 대 한 확장 배포](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)