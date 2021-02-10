---
title: ProjectItemFile 요소 | Microsoft Docs
description: SharePoint 프로젝트 항목 XML 스키마 참조의 프로젝트 항목 파일을 나타내는 ProjectItemFile 요소에 대 한 참조 정보를 가져옵니다.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectItemFile element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: a7c6dd7fc46dc8616eddc164bcf2ec801657cb00
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955140"
---
# <a name="projectitemfile-element"></a>ProjectItemFile 요소
  SharePoint에 배포 될 때 프로젝트 항목에 포함할 기능 요소 파일 등의 SharePoint 파일을 나타냅니다.

## <a name="syntax"></a>구문

```xml
<ProjectItemFile Source = "Name of the file"
    Target = "Deployment path of the file"
    Type = "Type of deployment for the file" />
```

## <a name="type"></a>Type
 **ProjectItemFileType**

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

|attribute|Description|
|---------------|-----------------|
|**원본**|필수 **xs: string** 특성입니다.<br /><br /> 프로젝트 항목과 함께 배포할 파일의 이름입니다.|
|**대상**|선택적 **xs: string** 특성입니다.<br /><br /> 배포 루트 폴더를 기준으로 SharePoint에 파일이 배포 될 경로입니다. 배포 루트 폴더는 **type** 특성으로 지정 된 배포 유형에 따라 결정 됩니다. **대상** 특성이 지정 되지 않은 경우 파일은 **원본** 특성에 지정 된 이름의 폴더에 배포 됩니다.<br /><br /> 자세한 내용은 [sharepoint 솔루션 개발](../sharepoint/developing-sharepoint-solutions.md)에서 sharepoint 프로젝트 항목의 **배포 경로** 및 **배포 루트** 속성에 대 한 설명을 참조 하세요.|
|**유형**|필수 **xs: string** 특성입니다.<br /><br /> 파일에 대 한 배포 유형입니다. 가능한 값에 대 한 자세한 내용은 [sharepoint 솔루션 개발](../sharepoint/developing-sharepoint-solutions.md)에서 sharepoint 프로젝트 항목의 **배포 유형** 속성에 대 한 설명을 참조 하세요.|

### <a name="child-elements"></a>자식 요소
 없음

### <a name="parent-elements"></a>부모 요소

|요소|Description|
|-------------|-----------------|
|[파일](../sharepoint/files-element.md)|Sharepoint에 배포 될 때 SharePoint 프로젝트 항목에 포함할 파일을 지정 합니다.|

## <a name="remarks"></a>설명
 **ProjectItemFile** 요소에서 일반적으로 참조 되는 SharePoint 파일에는 기능 요소 파일 (*Elements.xml*), 목록 정의에 대 한 스키마 파일 (*Schema.xml*) 및 웹 파트 (*webpart*)의 웹 파트 정의 파일이 포함 됩니다.

## <a name="element-information"></a>요소 정보

|속성|값|
|-|-|
|**Namespace**|http: \/ \/ schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**스키마 이름**|SharePoint 프로젝트 항목 스키마|
|**유효성 검사 파일**|ProjectItemModelSchema|
|**비워 둘 수 있음**|예|

## <a name="see-also"></a>참고 항목
- [SharePoint 프로젝트 항목 스키마 참조](../sharepoint/sharepoint-project-item-schema-reference.md)
