---
title: SafeControls 요소 | Microsoft Docs
description: SafeControls 요소에 대 한 정보를 가져옵니다 .이 요소는 SharePoint 사이트의 ASPX 페이지에서 액세스 하기 위해 보안으로 표시 된 ASPX 컨트롤 또는 웹 파트의 컬렉션을 포함 합니다.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SafeControls element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 23e31e3df59d6d580ac94ffcb83f7a17e186a267
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99889449"
---
# <a name="safecontrols-element"></a>SafeControls 요소
  모든 사용자가 SharePoint 사이트의 ASPX 페이지에서 액세스할 수 있도록 보안으로 지정 된 ASPX 컨트롤 및 웹 파트의 컬렉션입니다.

## <a name="syntax"></a>구문

```xml
<SafeControls>
  <SafeControl.../>
</SafeControls>
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성
 없음

### <a name="child-elements"></a>자식 요소

|요소|Description|
|-------------|-----------------|
|[SafeControl](../sharepoint/safecontrol-element.md)|선택적 요소입니다.<br /><br /> 모든 사용자가 SharePoint 사이트의 ASPX 페이지에서 액세스할 수 있도록 보안으로 지정 된 ASPX 컨트롤이 나 웹 파트를 나타냅니다.|

### <a name="parent-elements"></a>부모 요소

|요소|Description|
|-------------|-----------------|
|[ProjectItem](../sharepoint/projectitem-element.md)|SharePoint 프로젝트 항목을 나타냅니다. 이 요소는 *.spdata* 파일의 필수 루트 요소입니다.|

## <a name="remarks"></a>설명
 안전 컨트롤에 대 한 자세한 내용은 [프로젝트 항목에 패키징 및 배포 정보 제공](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)을 참조 하세요.

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
