---
title: ProjectOutputFile 요소 | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectOutputFile element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 12f399b7a09c18c77482475575ca387a11955762
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85542391"
---
# <a name="projectoutputfile-element"></a>ProjectOutputFile 요소
  SharePoint에 배포 될 때 프로젝트 항목과 함께 포함할 개별 프로젝트의 출력을 나타냅니다.

## <a name="syntax"></a>구문

```xml
<ProjectOutputFile ProjectId = "GUID of the project"
    ProjectPath = "Relative path of the project"
    Target = "Deployment path of the project output"
    Type = "Type of deployment for the project output" />
```

## <a name="type"></a>Type
 **ProjectOutputFileType**

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

|특성|설명|
|---------------|-----------------|
|**ProjectId**|필수 **xs: string** 특성입니다.<br /><br /> 포함 하려는 출력이 있는 종속 프로젝트의 GUID입니다. 이는 종속 프로젝트 파일의 **Projectguid** 요소에 해당 합니다.|
|**ProjectPath**|필수 **xs: string** 특성입니다.<br /><br /> 포함 하려는 출력이 있는 종속 프로젝트의 프로젝트 파일 이름을 포함 한 상대 경로입니다. 이 경로는 SharePoint 프로젝트 항목을 포함 하는 SharePoint 프로젝트의 루트 폴더를 기준으로 합니다.|
|**Target**|선택적 **xs: string** 특성입니다.<br /><br /> 배포 루트 폴더를 기준으로 SharePoint 서버에 종속 프로젝트 출력을 배포할 경로입니다. 배포 루트 폴더는 **type** 특성으로 지정 된 배포 유형에 따라 결정 됩니다.<br /><br /> 자세한 내용은 [sharepoint 솔루션 개발](../sharepoint/developing-sharepoint-solutions.md)에서 sharepoint 프로젝트 항목의 **배포 경로** 및 **배포 루트** 속성에 대 한 설명을 참조 하세요.|
|**형식**|필수 **xs: string** 특성입니다.<br /><br /> 종속 프로젝트의 출력에 사용할 배포 형식입니다. 가능한 값에 대 한 자세한 내용은 [sharepoint 솔루션 개발](../sharepoint/developing-sharepoint-solutions.md)에서 sharepoint 프로젝트 항목의 **배포 유형** 속성에 대 한 설명을 참조 하세요.|

### <a name="child-elements"></a>자식 요소
 없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[파일만](../sharepoint/files-element.md)|Sharepoint에 배포 될 때 SharePoint 프로젝트 항목에 포함할 파일을 지정 합니다.|

## <a name="remarks"></a>설명
 **ProjectOutputFile** 요소를 사용 하 여 SharePoint 프로젝트 항목의 배포에 프로젝트의 출력을 포함 합니다. 다른 프로젝트 또는 프로젝트 항목을 포함 하는 동일한 프로젝트를 지정할 수 있습니다. 자세한 내용은 [프로젝트 항목에 패키징 및 배포 정보 제공](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)을 참조 하세요.

## <a name="element-information"></a>요소 정보

|속성|값|
|-|-|
|**Namespace**|http: \/ \/ schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**스키마 이름**|SharePoint 프로젝트 항목 스키마|
|**유효성 검사 파일**|ProjectItemModelSchema|
|**비워 둘 수 있음**|예|

## <a name="see-also"></a>참고 항목
- [SharePoint 프로젝트 항목 스키마 참조](../sharepoint/sharepoint-project-item-schema-reference.md)
- [프로젝트 항목에 패키징 및 배포 정보 제공](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
- [SharePoint 솔루션 개발](../sharepoint/developing-sharepoint-solutions.md)
