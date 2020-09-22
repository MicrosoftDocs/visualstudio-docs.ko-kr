---
title: 비즈니스 데이터 연결 모델 만들기 | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], model
- BDC [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], creating a model
- SharePoint development in Visual Studio, Business Data Connectivity service
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9f3da13858507a3ff176aaa0a44051674fd5285f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841479"
---
# <a name="create-a-business-data-connectivity-model"></a>비즈니스 데이터 연결 모델 만들기
  Visual Studio를 사용 하 여 BDC (비즈니스 데이터 연결) 모델을 만들거나 기존 BDC 모델을 사용자 지정할 수 있습니다. 각 SharePoint 프로젝트는 하나의 모델만 포함할 수 있습니다. 자세한 내용은 [SharePoint에 비즈니스 데이터 통합](../sharepoint/integrating-business-data-into-sharepoint.md)을 참조 하세요.

## <a name="create-a-new-model"></a>새 모델 만들기
 새 모델을 만들려면 **비즈니스 데이터 연결 모델** 프로젝트를 만들거나 **빈 SharePoint 프로젝트**에 **비즈니스 데이터 연결 모델** 항목을 추가 합니다.

> [!NOTE]
> 컴퓨터에가 설치 되어 있어야 합니다 [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] .

 Visual Studio에서 프로젝트에 폴더를 추가 합니다. 이 폴더에는 **새 항목 추가** 대화 상자에서 **비즈니스 데이터 연결 모델** 항목에 대해 지정한 이름이 지정 됩니다. 새 **비즈니스 데이터 연결 모델** 프로젝트를 만드는 경우 Visual Studio에서 폴더 이름을 **BdcModel1**로 합니다.

 Visual Studio에서 새 폴더에 다음 파일을 추가 합니다.

|파일|Description|
|----------|-----------------|
|모델 정의 파일|모델을 설명 하는 엔터티, 메서드, LOB (기간 업무) 시스템 개체 및 기타 메타 데이터를 정의 하는 XML을 포함 합니다.<br /><br /> BDC 디자이너, **Bdc 탐색기**, **Bdc 메서드 세부 정보** 창 및 **속성** 창을 사용 하 여이 파일의 메타 데이터를 수정 합니다.|
|엔터티 서비스 코드 파일|기본 엔터티의 인스턴스를 검색, 업데이트 및 삭제 하는 메서드를 포함 합니다.|

 엔터티의 속성을 정의 하려면 엔터티 코드 파일을 편집 합니다. 자세한 내용은 [방법: 모델에 엔터티 추가](../sharepoint/how-to-add-an-entity-to-a-model.md)를 참조 하세요.

 엔터티 인스턴스를 검색, 업데이트 및 삭제 하려면 엔터티 서비스 코드 파일에 코드를 추가 합니다. 자세한 내용은 [비즈니스 데이터 연결 모델 디자인](../sharepoint/designing-a-business-data-connectivity-model.md)을 참조 하세요.

 프로젝트를 컴파일하면 Visual Studio에서 어셈블리를 만듭니다. 프로젝트 어셈블리에 코드를 추가 하는 기타 항목 (예: **순차 워크플로** 항목 또는 **웹 파트** 항목)을 프로젝트에 추가 하지 않도록 합니다. 솔루션 패키지는 어셈블리를 전역 어셈블리 캐시에 복사 하지 않으므로 해당 항목에 대 한 코드는 솔루션을 배포할 때 실행 되지 않습니다.  솔루션 패키지는 SharePoint의 BDC 데이터베이스에만 어셈블리를 배포 합니다.

> [!NOTE]
> Visual Studio는 프로젝트를 디버그할 때 로컬 컴퓨터의 두 위치에 어셈블리를 복사 합니다.

## <a name="add-an-existing-model"></a>기존 모델 추가
 SharePoint 디자이너와 같은 다른 도구를 사용 하 여 만든 모델을 가져올 수 있습니다. 다음과 같은 상황에서 기존 모델을 프로젝트로 가져오도록 선택할 수 있습니다.

- 이미 SharePoint 서버 팜에 배포 된 모델을 사용자 지정 하려면

- 여러 SharePoint 서버 팜에 기존 모델을 패키지 하 고 배포 합니다.

  두 경우 모두 가져오는 모델에 정의 된 LOB 시스템은 영향을 받지 않으며 계속 예상 대로 작동 합니다. 기존 모델을 SharePoint 프로젝트에 추가 하려면 Visual Studio **기존 항목 추가** 대화 상자를 사용 합니다. 자세한 내용은 [방법: SharePoint 프로젝트에 기존 BDC 모델 파일 추가](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)를 참조 하세요.

  **.Net 어셈블리 추가 LobSystem**에서 옵션을 선택 하 여 가져온 모델에 .NET Framework ASSEMBLY 형식의 LOB 시스템을 추가할 수 있습니다. 이렇게 하면 사용자 지정 코드를 작성 하 고 디자이너를 사용 하 여 가져온 모델에 대 한 메타 데이터를 정의할 수 있습니다.

## <a name="related-topics"></a>관련 항목

|제목|Description|
|-----------|-----------------|
|[방법: BDC 모델 만들기](../sharepoint/how-to-create-a-bdc-model.md)|새 BDC 모델을 만드는 방법을 보여 줍니다.|
|[방법: SharePoint 프로젝트에 기존 BDC 모델 파일 추가](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)|기존 모델을 SharePoint 프로젝트로 가져오는 방법을 보여 줍니다.|
|[방법: 리소스 파일을 사용하여 지역화된 이름, 속성, 사용 권한 지정](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)|모델이 웹 파트 또는 웹 페이지에서 사용 되는 경우 모델 메타 데이터와 병합 되는 문자열을 제공 하는 방법을 설명 합니다.|
|[방법: BDC 기능에 사용자 지정 어셈블리 포함](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)|기능에 사용자 지정 어셈블리를 포함 하는 방법을 보여 줍니다.|
