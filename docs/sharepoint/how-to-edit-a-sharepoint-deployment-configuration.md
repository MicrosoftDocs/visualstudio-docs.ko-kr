---
title: '방법: SharePoint 배포 구성 편집 | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.Project.DeploymentConfig
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deploying
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 74f6377bad0f62aa2c470e72afe64b85b3017ee6
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: ko-KR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016777"
---
# <a name="how-to-edit-a-sharepoint-deployment-configuration"></a>방법: SharePoint 배포 구성 편집
  배포 구성을 만들거나 기존 배포 구성을 수정할 수 있습니다. 예를 들어 단일 단계를 실행 하거나 배포 프로세스의 단계 순서를 변경할 수 있습니다. 기본 제공 되 고 프로그래밍 방식으로 추가 된 구성을 변경할 수 없기 때문에 배포 구성을 만들거나 수정할 수 있습니다.

## <a name="create-a-sharepoint-deployment-configuration"></a>SharePoint 배포 구성 만들기

#### <a name="to-create-a-sharepoint-deployment-configuration"></a>SharePoint 배포 구성을 만들려면

1. **솔루션 탐색기**에서 SharePoint 프로젝트를 선택한 다음 메뉴 모음에서 **프로젝트**, _ProjectName_**속성**을 선택 합니다.

2. **SharePoint** 탭에서 **새로 만들기** 단추를 선택 합니다.

     **새 배포 구성 추가** 대화 상자가 나타납니다.

3. **이름** 텍스트 상자에 배포 구성의 이름을 입력 합니다.

4. **사용 가능한 배포 단계** 창에서 배포 구성에 추가 하려는 단계를 선택 하 고 ( **>** ) 단추를 선택한 다음 **확인** 단추를 선택 합니다.

    > [!NOTE]
    > 배포 전 명령이 나 배포 후 명령을 구성한 경우 이러한 단계는 사용자 지정 배포 구성에 추가 하는 경우에만 실행 됩니다.

## <a name="change-the-active-deployment-configuration"></a>활성 배포 구성 변경

#### <a name="to-change-the-active-deployment-configuration"></a>활성 배포 구성을 변경 하려면

1. **솔루션 탐색기**에서 SharePoint 프로젝트를 선택한 다음 메뉴 모음에서 **프로젝트**  >  ** \<*ProjectName*> 속성**을 선택 합니다.

2. **SharePoint** 탭을 선택 합니다.

3. **활성 배포 구성** 목록 상자에서 사용 하려는 배포 구성의 이름을 선택 합니다.

## <a name="see-also"></a>참고 항목
- [SharePoint 솔루션 패키징 및 배포](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
