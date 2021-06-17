---
title: '방법: BDC 모델 만들기 | Microsoft Docs'
description: 해당 종류의 항목에 대해 Visual Studio 템플릿을 사용 하 여 BDC (비즈니스 데이터 연결) 모델을 만든 다음 SharePoint 프로젝트에 모델을 추가 합니다.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], creating a model
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: fd5184f87cf3895e1519a91e6f7e6661702f1181
ms.sourcegitcommit: 1f27f33852112702ee35fbc0c02fba37899e4cf5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2021
ms.locfileid: "112112413"
---
# <a name="how-to-create-a-bdc-model"></a>방법: BDC 모델 만들기

  해당 종류의 항목에 대 한 템플릿을 사용 하 고 SharePoint 프로젝트에 모델을 추가 하 여 BDC (비즈니스 데이터 연결) 모델을 만들 수 있습니다. 자세한 내용은 [비즈니스 데이터 연결 모델 만들기](../sharepoint/creating-a-business-data-connectivity-model.md)를 참조하세요. 모델을 디자인 하는 방법에 대 한 자세한 내용은 [비즈니스 데이터 연결 모델 디자인](../sharepoint/designing-a-business-data-connectivity-model.md)을 참조 하세요.

## <a name="to-create-a-bdc-project"></a>BDC 프로젝트를 만들려면

1. 메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트** 를 선택합니다.
::: moniker range="=vs-2017"
   > [!NOTE]
   > IDE가 Visual Basic 개발 설정을 사용 하도록 설정 된 경우 **파일**  >  **새로 만들기 프로젝트** 를 선택 합니다.

  **새 프로젝트** 대화 상자가 열립니다.

2. **Visual Basic** 또는 **Visual c #** 에서 **Office/sharepoint**, **sharepoint 솔루션** 을 선택 합니다.

3. **템플릿** 창에서 **SharePoint 2013-빈 프로젝트** 항목을 선택 하 고 **확인** 단추를 선택 합니다.

     **SharePoint 사용자 지정 마법사** 가 열립니다.
::: moniker-end
::: moniker range=">=vs-2019"
2. **새 프로젝트 만들기** 대화 상자에서 설치 된 sharepoint의 특정 버전에 대해 *sharepoint 빈 프로젝트**를 선택 합니다. 예를 들어 SharePoint 2019을 설치한 경우 **sharepoint 2019-빈 프로젝트** 템플릿을 선택 합니다.
    [!INCLUDE[new-project-dialog-search](../sharepoint/includes/new-project-dialog-search-md.md)]

3. 원하는 경우 프로젝트 이름을 변경한 다음 **만들기** 단추를 선택 합니다.

::: moniker-end
4. **디버깅에 사용할 사이트 및 보안 수준 지정** 페이지에서 로컬 컴퓨터에 있는 SharePoint 사이트의 URL을 지정 하 고 **팜 솔루션으로 배포** 옵션 단추를 선택한 다음 **마침** 단추를 선택 합니다.

     지정한 SharePoint 사이트에서 모델을 테스트 합니다.

    > [!IMPORTANT]
    > BDC 모델은 팜 솔루션만 지원 하므로 팜 솔루션으로 프로젝트를 배포 해야 합니다.

     빈 SharePoint 프로젝트가 생성 됩니다.

5. 메뉴 모음에서 **프로젝트** > **새 항목 추가** 를 선택합니다.

6. **새 항목 추가** 대화 상자에서 **Office/SharePoint** 노드를 선택 합니다.

7. SharePoint 템플릿 목록에서 **비즈니스 데이터 연결 모델 (팜 솔루션에만 해당)** 을 선택 합니다.

8. **이름** 상자에서 BDC 모델의 이름을 지정한 다음 **추가** 단추를 선택 합니다.

     **비즈니스 데이터 연결 모델** 항목이 프로젝트에 추가 됩니다. 기본적으로 모델은 BDC 디자이너에 표시 됩니다. 자세한 내용은 [비즈니스 데이터 연결 모델 만들기](../sharepoint/creating-a-business-data-connectivity-model.md)를 참조하세요.

## <a name="see-also"></a>참조

- [비즈니스 데이터 연결 모델 만들기](../sharepoint/creating-a-business-data-connectivity-model.md)
- [방법: SharePoint 프로젝트에 기존 BDC 모델 파일 추가](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)
- [방법: 리소스 파일을 사용하여 지역화된 이름, 속성, 사용 권한 지정](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)
- [방법: BDC 기능에 사용자 지정 어셈블리 포함](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)
- [SharePoint에 비즈니스 데이터 통합](../sharepoint/integrating-business-data-into-sharepoint.md)
