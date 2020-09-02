---
title: SharePoint 기능 만들기 | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, features
- features [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8d3f453770dbb389a688db0a9edcc8e97e179858
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62952748"
---
# <a name="create-sharepoint-features"></a>SharePoint 기능 만들기
  SharePoint 기능을 사용 하 여 더 쉽게 배포할 수 있도록 관련 SharePoint 프로젝트 항목을 그룹화 할 수 있습니다. SharePoint 기능 디자이너를 사용 하 여 기능을 만들고, 범위를 설정 하 고, 다른 기능을 종속성으로 표시할 수 있습니다. 또한 디자이너는 각 기능을 설명 하는 XML 파일인 매니페스트를 생성 합니다.

## <a name="add-features-to-the-sharepoint-solution"></a>SharePoint 솔루션에 기능 추가
 솔루션 탐색기 또는 패키징 탐색기를 사용 하 여 SharePoint 솔루션에 기능을 추가할 수 있습니다. 다음 방법 중 하나를 사용 하 여 기능을 추가할 수 있습니다.

- **솔루션 탐색기**에서 **기능**에 대 한 바로 가기 메뉴를 열고 **기능 추가**를 선택 합니다.

- **패키징 탐색기**에서 패키지에 대 한 바로 가기 메뉴를 열고 **기능 추가**를 선택 합니다.

## <a name="using-the-feature-designer"></a>기능 디자이너 사용
 SharePoint 솔루션은 솔루션 탐색기의 기능 노드 아래에 그룹화 된 SharePoint 기능을 하나 이상 포함할 수 있습니다. 각 기능에는 기능 속성을 사용자 지정 하는 데 사용할 수 있는 고유한 **기능 디자이너가** 있습니다. 자세한 내용은 [방법: SharePoint 기능 사용자 지정](../sharepoint/how-to-customize-a-sharepoint-feature.md)을 참조 하세요. 서로 다른 기능을 구분 하기 위해 제목, 설명, 버전, 범위 등의 기능 속성을 구성할 수 있습니다.

### <a name="feature-designer-options"></a>기능 디자이너 옵션
 기능을 만든 후 기능 디자이너를 사용 하 여 기능을 사용자 지정할 수 있습니다.

 다음 표에서는 기능 디자이너에 표시 되는 기능 속성을 설명 합니다.

|속성|설명|
|--------------|-----------------|
|제목|선택 사항입니다. 기능의 기본 제목은 *SolutionName* *FeatureName*로 설정 됩니다.|
|설명|선택 사항입니다. SharePoint 기능에 대 한 설명입니다.|
|범위|필수 요소. **솔루션 탐색기**를 사용 하 여 기능을 만드는 경우 기본적으로 범위가 웹으로 설정 됩니다.<br /><br /> -팜: 전체 서버 팜에 대해 기능을 활성화 합니다.<br /><br /> -사이트: 사이트 모음에 있는 모든 웹 사이트에 대해 기능을 활성화 합니다.<br /><br /> -웹: 특정 웹 사이트에 대 한 기능을 활성화 합니다.<br /><br /> -WebApplication: 웹 응용 프로그램의 모든 웹 사이트에 대해 기능을 활성화 합니다.|
|솔루션의 항목|기능에 추가할 수 있는 모든 SharePoint 항목입니다.|
|기능의 항목|기능에 추가 된 SharePoint 프로젝트 항목입니다.|

## <a name="add-and-remove-sharepoint-project-items"></a>SharePoint 프로젝트 항목 추가 및 제거
 배포를 위해 SharePoint 기능을 추가 하려는 SharePoint 프로젝트 항목을 선택할 수 있습니다. 기능 **디자이너** 를 사용 하 여 기능에 항목을 추가 및 제거 하 고 기능 매니페스트를 확인 합니다. 자세한 내용은 [방법: SharePoint 기능에 항목 추가 및 제거](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)를 참조 하세요.

## <a name="add-feature-dependencies"></a>기능 종속성 추가
 기능이 활성화 되기 전에 SharePoint 서버가 특정 기능을 활성화 하도록 기능 매니페스트를 구성할 수 있습니다. 예를 들어 SharePoint 기능이 기능 또는 데이터에 대 한 다른 기능에 종속 되는 경우 SharePoint 서버는 먼저 기능이 종속 된 기능을 활성화할 수 있습니다. 자세한 내용은 [방법: 기능 종속성 추가 및 제거](../sharepoint/how-to-add-and-remove-feature-dependencies.md)를 참조 하세요.

## <a name="see-also"></a>추가 정보
- [방법: SharePoint 기능 사용자 지정](../sharepoint/how-to-customize-a-sharepoint-feature.md)
- [방법: SharePoint 기능에 항목 추가 및 제거](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)
- [방법: 기능 종속성 추가 및 제거](../sharepoint/how-to-add-and-remove-feature-dependencies.md)
