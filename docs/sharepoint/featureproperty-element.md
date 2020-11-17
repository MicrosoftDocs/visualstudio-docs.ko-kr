---
title: FeatureProperty 요소 | Microsoft Docs
description: SharePoint 프로젝트 항목 스키마의 요소인 FeatureProperty 요소에 대 한 참조 정보를 봅니다.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- FeatureProperty element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8e6010ac45d0b760325c73c4bd754fbb0b422a77
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94672758"
---
# <a name="featureproperty-element"></a>FeatureProperty 요소
  SharePoint에 배포 될 때 기능에 포함 되는 사용자 지정 속성을 나타냅니다. 기능이 배포 된 후에는 코드에서 속성에 액세스할 수 있습니다.

## <a name="syntax"></a>구문

```xml
<FeatureProperty Key = "Key of the property value"
    Value = "Property value" />
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

|attribute|설명|
|---------------|-----------------|
|**키**|필수 **xs: string** 특성입니다.<br /><br /> 속성 값을 저장 하 고 검색 하는 데 사용 되는 키입니다. 각 속성에는 기능 내에서 고유한 키가 있어야 합니다.|
|**값**|필수 **xs: string** 특성입니다.<br /><br /> 속성 값입니다.|

### <a name="child-elements"></a>자식 요소
 없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[FeatureProperties](../sharepoint/featureproperties-element.md)|SharePoint에 배포 될 때 기능에 포함 된 속성 값의 컬렉션을 나타냅니다.|

## <a name="remarks"></a>설명
 기능 속성에 대 한 자세한 내용은 [프로젝트 항목에서 패키지 및 배포 정보 제공](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)을 참조 하세요.

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
