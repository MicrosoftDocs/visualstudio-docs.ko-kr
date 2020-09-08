---
title: Visual Studio의 SharePoint 도구 확장 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86016036"
---
# <a name="extend-the-sharepoint-tools-in-visual-studio"></a>Visual Studio의 SharePoint 도구 확장
  Visual Studio의 SharePoint 도구는 다양한 애플리케이션 개발 시나리오의 요구 사항을 충족합니다. 그러나 본인이나 다른 개발자에게 필요한 기능이 제공되지 않는 경우를 발견할 수도 있습니다. 이 경우에는 SharePoint 도구를 확장하여 필요한 기능을 만들 수 있습니다.

## <a name="how-to-extend-the-sharepoint-tools"></a>SharePoint 도구를 확장하는 방법
 SharePoint 프로젝트 시스템 및 **서버 탐색기** 창의 **SharePoint 연결** 노드를 확장할 수 있습니다.

### <a name="extend-the-sharepoint-project-system"></a>SharePoint 프로젝트 시스템 확장
 Visual Studio에는 SharePoint 솔루션을 만드는 데 사용할 수 있는 프로젝트 템플릿 및 항목 템플릿 세트가 포함되어 있습니다. 예를 들어 이벤트 수신기, 목록 정의, 워크플로, 웹 파트의 템플릿이 있습니다. 그러나 필드 또는 사용자 지정 작업과 같은 SharePoint 구성 요소를 만들기 위해 고유한 종류의 SharePoint 프로젝트 항목을 정의할 수도 있습니다. 또한 Visual Studio에 이미 설치된 SharePoint 프로젝트 항목 종류의 확장을 만들 수 있으며, SharePoint 프로젝트의 확장도 만들 수 있습니다.

 자세한 내용은 [SharePoint 프로젝트 시스템 확장](../sharepoint/extending-the-sharepoint-project-system.md)을 참조하세요.

### <a name="extend-the-sharepoint-connections-node-in-server-explorer"></a>서버 탐색기의 SharePoint 연결 노드 확장
 Visual Studio에서 **서버 탐색기** 창의 **SharePoint 연결** 노드를 사용하여 여러 로컬 SharePoint 사이트의 다양한 구성 요소를 계층적 트리 뷰로 볼 수 있습니다. 다음과 같은 방법으로 **SharePoint 연결** 노드를 확장할 수도 있습니다.

- 사용자 고유의 노드 추가. 이 방법은 기본적으로 표시되지 않는 SharePoint 사이트의 구성 요소를 표시하려는 경우에 유용합니다.

- 기존 노드 확장. 예를 들어 기존 노드에 새 자식 노드를 추가하거나, 노드에 바로 가기 메뉴 항목을 추가하고 개발자가 메뉴 항목을 클릭할 때 작업을 수행할 수 있습니다.

  자세한 내용은 [서버 탐색기의 SharePoint 연결 노드 확장](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)을 참조하세요.

## <a name="development-computer-requirements"></a>개발 컴퓨터 요구 사항
 SharePoint 도구의 확장을 만들려면 개발 컴퓨터가 Visual Studio에서 SharePoint 솔루션을 만들 때와 동일한 요구 사항을 충족해야 합니다.

 또한 [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]를 설치하는 것이 좋습니다. SDK에는 Visual Studio를 확장하는 데 사용할 수 있는 프로젝트 템플릿과 도구가 포함되어 있습니다. 특히, SDK에는 VSIX(Visual Studio 확장) 패키지를 쉽게 만드는 데 사용할 수 있는 프로젝트 템플릿이 포함되어 있습니다. VSIX 패키지는 Visual Studio에 Visual Studio 확장을 배포하는 데 선호되는 방법입니다. 모든 SharePoint 도구 확장은 VSIX 패키지를 사용해서 배포해야 합니다. 이 설명서의 모든 연습에서는 [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]가 설치되어 있다고 가정합니다.

 Visual Studio SDK를 설치하려면 [Visual Studio SDK 설치](../extensibility/installing-the-visual-studio-sdk.md)를 참조하세요. Visual Studio 확장에 대한 자세한 내용은 [Visual Studio 확장 개발 시작](../extensibility/starting-to-develop-visual-studio-extensions.md)을 참조하세요.

## <a name="see-also"></a>추가 정보

- [SharePoint 도구 확장의 프로그래밍 모델 개요](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)
- [SharePoint 프로젝트 시스템 확장](../sharepoint/extending-the-sharepoint-project-system.md)
- [서버 탐색기의 SharePoint 연결 노드 확장](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [SharePoint 도구 확장의 프로그래밍 개념 및 기능](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)
- [참조&#40;SharePoint 도구 확장성&#41;](../sharepoint/reference-sharepoint-tools-extensibility.md)
- [Visual Studio에서 SharePoint 도구 확장 디버그](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)
- [Visual Studio에 SharePoint 도구 확장 배포](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)