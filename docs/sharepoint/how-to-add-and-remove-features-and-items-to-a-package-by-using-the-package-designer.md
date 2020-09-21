---
title: '패키지 디자이너: 패키지에 기능 및 항목 추가 & 제거'
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.RAD.PackageDesignerDesign
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: cd712eafb6061da89367c247475904886579d2de
ms.sourcegitcommit: 7a46232242783ebe23f2527f91eac8eb84b3ae05
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90740086"
---
# <a name="how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer"></a>방법: 패키지 디자이너를 사용 하 여 패키지에 기능과 항목 추가 및 제거
  SharePoint 솔루션을 만들 때 Visual Studio는 솔루션의 패키지에 기본 SharePoint 기능을 추가 합니다. 최종 배포 전에 sharepoint 프로젝트 항목 및 기능을 추가 및 제거 하 여 SharePoint 패키지를 수정할 수 있습니다.

 또는 패키징 탐색기를 사용 하 여 SharePoint 프로젝트 항목을 추가 하 고 제거할 수 있습니다. 또한 패키지 (.wsp)에 배치 된 SharePoint 프로젝트 항목 및 기능의 계층 구조를 보고 변경할 수 있습니다. 자세한 내용은 [방법: 패키징 탐색기를 사용 하 여 패키지에 기능 및 항목 추가 및 제거](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md)를 참조 하세요.

## <a name="add-features-to-a-sharepoint-package"></a>SharePoint 패키지에 기능 추가
 패키지 디자이너를 사용 하 여 SharePoint 패키지에 기능을 추가할 수 있습니다.

#### <a name="to-add-sharepoint-features-with-the-package-designer"></a>패키지 디자이너를 사용 하 여 SharePoint 기능을 추가 하려면

1. **패키지 디자이너**를 엽니다.

    자세한 내용은 [방법: SharePoint 솔루션 패키지 사용자 지정](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)을 참조 하세요.

2. 다음 단계 중 하나 이상을 수행 하 여 하나 이상의 SharePoint 기능을 추가 합니다.

   1. 추가 하려는 **솔루션 목록의 항목** 에서 각 항목을 두 번 클릭 합니다.

   2. 추가 하려는 항목을 선택한 다음 **추가** 단추 (>)를 선택 합니다.

   3. 모든 항목을 한 번에 추가 하려면 **모두 추가** 단추 (>>)를 선택 합니다.

      예를 들어 **솔루션** 목록의 항목에서 항목을 두 번 클릭 하 여 **패키지 목록의 항목** 에 추가할 수 있습니다.

      SharePoint 프로젝트 항목 및 기능이 **패키지 목록의 항목** 에 표시 됩니다.

## <a name="remove-features-from-a-sharepoint-package"></a>SharePoint 패키지에서 기능 제거
 패키지 디자이너를 사용 하 여 SharePoint 패키지의 기능을 제거할 수 있습니다.

#### <a name="to-remove-sharepoint-features-with-the-package-designer"></a>패키지 디자이너를 사용 하 여 SharePoint 기능을 제거 하려면

1. 패키지 목록 **에서** 항목을 선택 하 고 제거 하려는 항목을 선택한 다음 **제거** (<) 단추를 선택 하거나 **모두 제거** 단추 (<<)를 선택 하 여 모든 항목을 제거 합니다.

     SharePoint 항목은 **솔루션 목록의 항목** 에 표시 됩니다.

## <a name="see-also"></a>추가 정보
- [SharePoint 솔루션 패키지 만들기](../sharepoint/creating-sharepoint-solution-packages.md)
- [방법: SharePoint 솔루션 패키지 사용자 지정](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)
- [방법: 패키지 만들기](/previous-versions/ee231585(v=vs.110))