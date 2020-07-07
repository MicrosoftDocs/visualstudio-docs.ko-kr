---
title: '방법: SharePoint 기능에 항목 추가 및 제거 | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.RAD.FeatureDesigner
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, features
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 27c6ebfb0b0cdbff0a184859ffa2a73acab809c1
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: ko-KR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86014528"
---
# <a name="how-to-add-and-remove-items-to-sharepoint-features"></a>방법: SharePoint 기능에 항목 추가 및 제거
  SharePoint 솔루션을 만들 때 Visual Studio는 기능에 기본 SharePoint 프로젝트 항목을 추가 합니다. 배포 하기 전에 sharepoint 프로젝트 항목을 추가 및 제거 하 여 SharePoint 기능을 수정할 수 있습니다.

## <a name="add-sharepoint-project-items-to-a-feature"></a>기능에 SharePoint 프로젝트 항목 추가

#### <a name="to-add-sharepoint-project-items-with-the-feature-designer"></a>기능 디자이너를 사용 하 여 SharePoint 프로젝트 항목을 추가 하려면

1. 기능 디자이너를 엽니다.

    자세한 내용은 [방법: SharePoint 기능 사용자 지정](../sharepoint/how-to-customize-a-sharepoint-feature.md)을 참조 하세요.

2. 다음 단계 중 하나 이상을 수행 하 여 **솔루션** 목록의 항목에서 기능 목록의 **항목** 에 하나 이상의 항목을 추가 합니다.

   - 추가할 각 항목을 두 번 클릭합니다.

   - 추가 하려는 항목을 선택한 다음 **추가** 단추 (>)를 선택 합니다.

   - **모두 추가** 단추 (>>)를 선택 합니다.

     SharePoint 프로젝트 항목은 **기능 목록의 항목** 에 표시 됩니다.

## <a name="remove-sharepoint-project-items-from-a-feature"></a>기능에서 SharePoint 프로젝트 항목 제거

#### <a name="to-remove-sharepoint-items-with-the-feature-designer"></a>기능 디자이너를 사용 하 여 SharePoint 항목을 제거 하려면

1. **기능 목록의 항목** 에서 하나 이상의 항목을 선택 합니다.

2. **제거** 단추 (<)를 선택 하 여 한 번에 한 항목을 제거 하거나 **모두 제거** 단추 (<<)를 선택 하 여 모든 항목을 제거 합니다.

     SharePoint 프로젝트 항목은 **솔루션 목록의 항목** 에 표시 됩니다.

## <a name="see-also"></a>참고 항목
- [SharePoint 기능 만들기](../sharepoint/creating-sharepoint-features.md)
- [SharePoint 솔루션 패키징 및 배포](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
