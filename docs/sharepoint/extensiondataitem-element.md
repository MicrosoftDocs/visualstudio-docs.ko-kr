---
title: ExtensionDataItem 요소 | Microsoft Docs
description: SharePoint 프로젝트 항목 스키마의 요소인 ExtensionDataItem 요소에 대 한 참조 정보를 봅니다.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ExtensionDataItem element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: add1a119283635f9cfd9bebddfe18228f1976703
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99876825"
---
# <a name="extensiondataitem-element"></a>ExtensionDataItem 요소
  SharePoint 프로젝트 항목과 연결 된 사용자 지정 데이터 항목으로, 키/값 형식으로 되어 있습니다. 키와 값은 모두 문자열 이어야 합니다.

## <a name="syntax"></a>구문

```xml
<ExtensionDataItem Key = "Key of the data item"
    Value = "Value of the data item" />
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

|attribute|Description|
|---------------|-----------------|
|**키**|필수 **xs: string** 특성입니다.<br /><br /> 데이터 항목을 저장 하 고 검색 하는 데 사용 되는 키입니다.|
|**값**|필수 **xs: string** 특성입니다.<br /><br /> 데이터 항목의 값입니다.|

### <a name="child-elements"></a>자식 요소
 없음

### <a name="parent-elements"></a>부모 요소

|요소|Description|
|-------------|-----------------|
|[ExtensionData](../sharepoint/extensiondata-element.md)|SharePoint 프로젝트 항목과 연결 된 사용자 지정 데이터 항목의 컬렉션을 나타냅니다.|

## <a name="remarks"></a>설명
 개체의 속성을 사용 하 여 사용자 지정 데이터를 SharePoint 프로젝트 항목과 연결 하면 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> Visual Studio에서 프로젝트 항목에 대 한 파일의 새 **extensiondataitem** 요소에 데이터를 저장 합니다 `.spdata` . 자세한 내용은 [SharePoint 프로젝트 시스템의 확장에 데이터 저장](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)을 참조 하세요.

## <a name="element-information"></a>요소 정보

|속성|값|
|-|-|
|**Namespace**|http: \/ \/ schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**스키마 이름**|SharePoint 프로젝트 항목 스키마|
|**유효성 검사 파일**|ProjectItemModelSchema|
|**비워 둘 수 있음**|예|

## <a name="see-also"></a>참고 항목
- [SharePoint 프로젝트 항목 스키마 참조](../sharepoint/sharepoint-project-item-schema-reference.md)
