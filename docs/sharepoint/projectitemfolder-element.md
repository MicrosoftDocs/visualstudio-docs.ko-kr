---
title: ProjectItemFolder 요소 | Microsoft Docs
description: ProjectItemFolder 요소에 대 한 참조 정보를 가져옵니다 .이 요소는 SharePoint 프로젝트 항목 XML 스키마 참조의 매핑된 폴더를 나타냅니다.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectItemFolder element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: d1a5b5086ef90b9d8399a6f0f76bdee77c07288e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99950577"
---
# <a name="projectitemfolder-element"></a>ProjectItemFolder 요소
  매핑된 폴더를 나타냅니다.

## <a name="syntax"></a>구문

```xml
<ProjectItemFolder Target = "Path of SharePoint folder the mapped folder corresponds to"
    Type = "Type of deployment for the mapped folder" />
```

## <a name="type"></a>Type
 **ProjectItemFolderType**

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

|attribute|Description|
|---------------|-----------------|
|**대상**|필수 **xs: string** 특성입니다.<br /><br /> 배포 루트 폴더에 상대적인, 매핑된 폴더가 해당 하는 SharePoint 설치의 폴더 경로입니다. 배포 루트 폴더는 **type** 특성으로 지정 된 배포 유형에 따라 결정 됩니다.<br /><br /> 자세한 내용은 [sharepoint 솔루션 개발](../sharepoint/developing-sharepoint-solutions.md)에서 sharepoint 프로젝트 항목의 **배포 경로** 및 **배포 루트** 속성에 대 한 설명을 참조 하세요.|
|**유형**|필수 **xs: string** 특성입니다.<br /><br /> 매핑된 폴더의 배포 유형입니다. 가능한 값에 대 한 자세한 내용은 [sharepoint 솔루션 개발](../sharepoint/developing-sharepoint-solutions.md)에서 sharepoint 프로젝트 항목의 **배포 유형** 속성에 대 한 설명을 참조 하세요.|

### <a name="child-elements"></a>자식 요소
 없음

### <a name="parent-elements"></a>부모 요소

|요소|Description|
|-------------|-----------------|
|[ProjectItem](../sharepoint/projectitem-element.md)|SharePoint 프로젝트 항목을 나타냅니다. 이 요소는 *.spdata* 파일의 필수 루트 요소입니다.|

## <a name="remarks"></a>설명
 매핑된 폴더에 대 한 자세한 내용은 [방법: 매핑된 폴더 추가 및 제거](../sharepoint/how-to-add-and-remove-mapped-folders.md)를 참조 하세요.

## <a name="element-information"></a>요소 정보

|속성|값|
|-|-|
|**Namespace**|http: \/ \/ schemas.microsoft.com/VisualStudio/2010/<br>SharePointTools/SharePointProjectItemModel|
|**스키마 이름**|SharePoint 프로젝트 항목 스키마|
|**유효성 검사 파일**|ProjectItemModelSchema|
|**비워 둘 수 있음**|예|

## <a name="see-also"></a>참고 항목
- [SharePoint 프로젝트 항목 스키마 참조](../sharepoint/sharepoint-project-item-schema-reference.md)
- [방법: 매핑된 폴더 추가 및 제거](../sharepoint/how-to-add-and-remove-mapped-folders.md)
