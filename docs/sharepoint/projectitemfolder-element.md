---
title: ProjectItemFolder 요소 | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectItemFolder element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 38f8f70cc6480554441809e33c4083735600fbbb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85539817"
---
# <a name="projectitemfolder-element"></a>ProjectItemFolder 요소
  매핑된 폴더를 나타냅니다.

## <a name="syntax"></a>Syntax

```xml
<ProjectItemFolder Target = "Path of SharePoint folder the mapped folder corresponds to"
    Type = "Type of deployment for the mapped folder" />
```

## <a name="type"></a>형식
 **ProjectItemFolderType**

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

|특성|설명|
|---------------|-----------------|
|**대상**|필수 **xs: string** 특성입니다.<br /><br /> 배포 루트 폴더에 상대적인, 매핑된 폴더가 해당 하는 SharePoint 설치의 폴더 경로입니다. 배포 루트 폴더는 **type** 특성으로 지정 된 배포 유형에 따라 결정 됩니다.<br /><br /> 자세한 내용은 [sharepoint 솔루션 개발](../sharepoint/developing-sharepoint-solutions.md)에서 sharepoint 프로젝트 항목의 **배포 경로** 및 **배포 루트** 속성에 대 한 설명을 참조 하세요.|
|**유형**|필수 **xs: string** 특성입니다.<br /><br /> 매핑된 폴더의 배포 유형입니다. 가능한 값에 대 한 자세한 내용은 [sharepoint 솔루션 개발](../sharepoint/developing-sharepoint-solutions.md)에서 sharepoint 프로젝트 항목의 **배포 유형** 속성에 대 한 설명을 참조 하세요.|

### <a name="child-elements"></a>자식 요소
 없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
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
