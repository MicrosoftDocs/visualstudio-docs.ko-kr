---
title: FeatureProperties 요소 | Microsoft Docs
description: SharePoint 프로젝트 항목 스키마의 요소인 FeatureProperties 요소에 대 한 참조 정보를 봅니다.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- FeatureProperties element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9ee2bddec02263a889fb1f69088a8a50b3d8b57d
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94672602"
---
# <a name="featureproperties-element"></a>FeatureProperties 요소
  SharePoint에 배포 될 때 기능과 함께 포함 되는 속성 값의 컬렉션입니다. 기능이 배포 된 후 코드에서 속성 값에 액세스할 수 있습니다.

## <a name="syntax"></a>구문

```xml
<FeatureProperties>
  <FeatureProperty.../>
</FeatureProperties>
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성
 없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[FeatureProperty](../sharepoint/featureproperty-element.md)|선택적 요소입니다.<br /><br /> 키/값 형식의 사용자 지정 속성을 나타냅니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[ProjectItem](../sharepoint/projectitem-element.md)|SharePoint 프로젝트 항목을 나타냅니다. 이 요소는 파일의 필수 루트 요소 `.spdata` 입니다.|

## <a name="remarks"></a>설명
 기능 속성에 대 한 자세한 내용은 [프로젝트 항목에 패키징 및 배포 정보 제공](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)을 참조 하세요.

## <a name="element-information"></a>요소 정보

|요소|설명|
|-------------|-----------------|
|**Namespace**|http: \/ \/ schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**스키마 이름**|SharePoint 프로젝트 항목 스키마|
|**유효성 검사 파일**|ProjectItemModelSchema|
|**비워 둘 수 있음**|예|

## <a name="see-also"></a>참고 항목
- [SharePoint 프로젝트 항목 스키마 참조](../sharepoint/sharepoint-project-item-schema-reference.md)
- [프로젝트 항목에 패키징 및 배포 정보 제공](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
