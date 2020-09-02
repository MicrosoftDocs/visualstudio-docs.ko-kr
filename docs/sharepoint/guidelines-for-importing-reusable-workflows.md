---
title: 재사용 가능한 워크플로를 가져오기 위한 지침 | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing items
- SharePoint development in Visual Studio, reusable workflows
- importing items [SharePoint development in Visual Studio]
- reusable workflows [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: bb386a2d80931ece415b0b3939f2947678808261
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62557190"
---
# <a name="guidelines-for-importing-reusable-workflows"></a>재사용 가능한 워크플로를 가져오기 위한 지침
  SharePoint Designer에서 만든 다시 사용할 수 있는 워크플로를 가져오려면 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]에서 다시 사용할 수 있는 SharePoint 2010 워크플로 가져오기 프로젝트 템플릿을 사용합니다. 이 템플릿은 *선언적* *워크플로* (전용)를 가져와서 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] *코드 워크플로*로 변환 합니다 .이 워크플로는 또는 코드를 사용 하 여 향상 시킬 수 있습니다 [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)] . [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)][연습: Visual Studio에 SharePoint Designer의 재사용 가능한 워크플로를 가져옵니다](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md).

 그러나 다시 사용할 수 있는 SharePoint 2010 워크플로 가져오기 템플릿은 팜 솔루션만 가져올 수 있습니다. 워크플로를 샌드박스 솔루션으로 배포하려면 SharePoint 2010 솔루션 패키지 가져오기 템플릿을 사용하여 워크플로를 가져옵니다. 그러나 이렇게 하면 워크플로를 코드 워크플로로 변환할 수 없고 코드 워크플로로 수정할 수도 없습니다.

## <a name="import-reusable-workflows-by-using-the-import-reusable-workflow-template"></a>재사용 가능한 워크플로 가져오기 템플릿을 사용 하 여 다시 사용할 수 있는 워크플로 가져오기
 다시 사용할 수 있는 SharePoint 2010 워크플로 가져오기 템플릿을 사용하여 다시 사용할 수 있는 워크플로를 가져오는 경우 솔루션을 다른 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint 솔루션과 마찬가지로 실행하거나 변경할 수 있지만 일부 항목은 수동으로 수정해야 할 수 있습니다.

### <a name="import-task-forms"></a>작업 폼 가져오기
 다시 사용할 수 있는 SharePoint 2010 워크플로 가져오기 프로젝트 템플릿은 모든 시작 양식과 연결 양식을 가져오지만 코드 워크플로 스키마에서 하나의 작업 양식만 허용하기 때문에 작업 양식은 하나만 가져옵니다. 원본 워크플로 솔루션의 추가 작업 양식은 **솔루션 탐색기**의 **다른 가져온 파일** 폴더에 저장 됩니다.

## <a name="import-reusable-workflows-by-using-the-import-sharepoint-2010-solution-package-template"></a>SharePoint 2010 솔루션 패키지 가져오기 템플릿을 사용 하 여 다시 사용할 수 있는 워크플로 가져오기
 SharePoint 2010 솔루션 패키지 가져오기 템플릿을 사용하여 다시 사용할 수 있는 워크플로를 가져오는 경우 다음 문제점을 고려해야 합니다.

- 워크플로를 가져온 후에 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 는 **F5** 키를 선택 하 여 워크플로를 즉시 배포 하 고 실행할 수 있습니다. 그러나 가져온 솔루션에서 워크플로의 모든 항목을 변경 하는 경우 워크플로를 배포 및 실행 하기 전에 프로젝트에서 요소를 수동으로 수정 해야 할 수 있습니다.

- 워크플로는 선언적 이므로 코드를 코드에 추가할 수 없습니다. 워크플로를 코드 워크플로로 변환 하려면 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 다시 사용할 수 있는 SharePoint 2010 워크플로 가져오기 템플릿을 사용 하 여 워크플로를로 가져와야 합니다.

- Workflow designer (xoml) 파일을 디자인 뷰에서 편집할 수 있지만 workflow designer에 거짓 오류가 표시 되기 때문에 원본 뷰에서 편집 하는 것이 좋습니다.

- 워크플로의 디버깅은 선언 내용에 대해 작동 하지 않습니다. 에 설정 된 중단점이 [!INCLUDE[wfd2](../sharepoint/includes/wfd2-md.md)] 적중 되지 않습니다.

## <a name="import-globally-reusable-workflow-solutions"></a>전역적으로 재사용 가능한 워크플로 솔루션 가져오기
 전역적으로 다시 사용할 수 있는 워크플로는 다시 사용할 수 있는 SharePoint 2010 워크플로 가져오기 템플릿을 사용하여 가져올 수 없습니다. 전역적으로 다시 사용할 수 있는 워크플로를 가져오려면 워크플로를 전역적으로 다시 사용할 수 없는 워크플로로 변환하거나 SharePoint 2010 솔루션 패키지 가져오기 템플릿을 사용해야 합니다.

 워크플로를 변환 하려면 워크플로를 위한 바로 가기 메뉴를 연 다음 **복사본으로 저장**을 선택 하 여 SharePoint Designer에서 전역적으로 재사용 가능한 워크플로 복사본을 만듭니다. 그런 다음 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]에서 다시 사용할 수 있는 SharePoint 2010 워크플로 가져오기 템플릿을 사용하여 다시 사용할 수 있는 새로운 워크플로를 가져옵니다.

 전역적으로 다시 사용할 수 있는 워크플로를 수정하지 않고 가져오려면 SharePoint 2010 솔루션 패키지 가져오기 템플릿을 사용합니다. 이 방법을 사용하면 워크플로가 코드 워크플로로 변환되지 않고 선언적 워크플로로 유지됩니다.

## <a name="see-also"></a>추가 정보
- [기존 SharePoint 사이트에서 항목 가져오기](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)
- [연습: Visual Studio에 SharePoint Designer의 다시 사용 가능한 워크플로 가져오기](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)
