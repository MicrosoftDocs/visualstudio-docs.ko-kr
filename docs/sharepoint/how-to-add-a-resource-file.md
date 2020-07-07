---
title: '방법: 리소스 파일 추가 | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- resource files [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, resource files
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 657eb473adcff40a62d2fc9b09518ebe8135eeb4
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: ko-KR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86015186"
---
# <a name="how-to-add-a-resource-file"></a>방법: 리소스 파일 추가
  리소스 파일을 추가 하기 위한 명령은 솔루션 노드의 바로 가기 메뉴와 솔루션 탐색기의 기능 노드에 있습니다. 자세한 내용은 [SharePoint 솔루션 지역화](../sharepoint/localizing-sharepoint-solutions.md)를 참조 하세요.

### <a name="to-add-a-global-resource-file-to-a-sharepoint-solution"></a>SharePoint 솔루션에 전역 리소스 파일을 추가 하려면

1. 에서 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint 솔루션을 엽니다.

2. **솔루션 탐색기**에서 SharePoint 프로젝트 노드를 선택한 다음 메뉴 모음에서 **프로젝트**  >  **새 항목 추가**를 선택 합니다.

3. **새 항목 추가** 대화 상자에서 **전역 리소스 파일** 템플릿을 선택 하 고 **추가** 단추를 선택 합니다.

   > [!NOTE]
   > 전역 리소스 파일 프로젝트 항목 템플릿은 SharePoint 프로젝트 항목을 선택한 경우에만 표시 됩니다.

4. **리소스 추가** 대화 상자에서 리소스 파일의 문화권 (예: 영어 (미국))을 선택 합니다.

    이 단계에서는 Resource_x_ 형식의 전역 리소스 파일을 솔루션에 추가**합니다.** <em>문화권</em><strong>.</strong> *resource1.resx*와 같은 resx입니다.

5. 에서 **리소스 편집기** 가 열리면 리소스 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 파일에 리소스를 추가 합니다.

### <a name="to-add-a-feature-resource-file-to-a-sharepoint-feature"></a>SharePoint 기능에 기능 리소스 파일을 추가 하려면

1. SharePoint 솔루션이에서 아직 열려 있지 않은 경우 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 솔루션을 엽니다.

2. **솔루션 탐색기**의 **기능** 노드에서 기능 이름에 대 한 바로 가기 메뉴를 열고 **기능 리소스 추가**를 선택 합니다.

     이 단계에서는 _ResourceFileName_형식으로 기능에 리소스 파일을 추가**합니다.** Feature1와 같은 _culture_**.RESX**. *-US .resx*.

3. 에서 **리소스 편집기** 가 열리면 리소스 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 파일에 리소스를 추가 합니다.

## <a name="see-also"></a>참고 항목
- [SharePoint 솔루션 개발](../sharepoint/developing-sharepoint-solutions.md)
