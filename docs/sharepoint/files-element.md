---
title: Files 요소 | Microsoft Docs
description: SharePoint 프로젝트 항목 스키마의 요소인 Files 요소에 대 한 참조 정보를 봅니다.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Files element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 03473f40bb78c866f3d93dea11a20b8747afad7b
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94672810"
---
# <a name="files-element"></a>Files 요소
  기능 요소 파일 및 종속 비 SharePoint 프로젝트의 출력과 같은 SharePoint 프로젝트 항목을 사용 하 여 배포할 파일을 지정 합니다.

## <a name="syntax"></a>구문

```xml
<Files>
  <ProjectItemFile.../>
  <ProjectOutputFile.../>
</Files>
```

## <a name="type"></a>유형
 **FileCollectionType**

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성
 없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[ProjectItemFile](../sharepoint/projectitemfile-element.md)|선택적 **ProjectItemFileType** 요소입니다.<br /><br /> SharePoint에 배포 될 때 프로젝트 항목에 포함할 기능 요소 파일 등의 SharePoint 파일을 나타냅니다.|
|[ProjectOutputFile](../sharepoint/projectoutputfile-element.md)|선택적 **Projectoutputfiletype** 요소입니다.<br /><br /> SharePoint에 배포 될 때 프로젝트 항목과 함께 포함할 프로젝트의 출력을 나타냅니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[ProjectItem](../sharepoint/projectitem-element.md)|SharePoint 프로젝트 항목을 나타냅니다. 이 요소는 파일의 필수 루트 요소 `.spdata` 입니다.|

## <a name="element-information"></a>요소 정보

|속성|값|
|-|-|
|**Namespace**|http: \/ \/ schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**스키마 이름**|SharePoint 프로젝트 항목 스키마|
|**유효성 검사 파일**|ProjectItemModelSchema|
|**비워 둘 수 있음**|예|

## <a name="see-also"></a>참고 항목
- [SharePoint 프로젝트 항목 스키마 참조](../sharepoint/sharepoint-project-item-schema-reference.md)
