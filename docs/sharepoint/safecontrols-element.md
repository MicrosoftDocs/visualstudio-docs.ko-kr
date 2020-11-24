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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c3423d1b6efd106ef7f947bd8573dcd1aa548a66
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/23/2020
ms.locfileid: "95440677"
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

|요소|설명|
|-------------|-----------------|
|[SafeControl](../sharepoint/safecontrol-element.md)|선택적 요소입니다.<br /><br /> 모든 사용자가 SharePoint 사이트의 ASPX 페이지에서 액세스할 수 있도록 보안으로 지정 된 ASPX 컨트롤이 나 웹 파트를 나타냅니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
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
