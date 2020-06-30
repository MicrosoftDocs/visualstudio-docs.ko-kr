---
title: SafeControl 요소 | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SafeControl element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6c9936054c5cc622e6f335d81d1568ebed16518f
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547929"
---
# <a name="safecontrol-element"></a>SafeControl 요소
  모든 사용자가 SharePoint 사이트의 ASPX 페이지에서 액세스할 수 있도록 보안으로 지정 된 ASPX 컨트롤이 나 웹 파트를 나타냅니다.

## <a name="syntax"></a>구문

```xml
<SafeControl Assembly = "Name of assembly that contains the safe control"
    IsSafe = "true/false"
    IsSafeAgainstScript = "true/false"
    Name = "Name of this safe control entry"
    Namespace = "Namespace of the safe control"
    TypeName = "Type of the safe control" />
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

|특성|설명|
|---------------|-----------------|
|**어셈블리**|선택적 **xs: string** 특성입니다.<br /><br /> ASPX 컨트롤이 나 웹 파트가 정의 된 어셈블리의 이름입니다. 기본적으로이 특성은 어셈블리 이름에 대해 **$SharePoint. AssemblyFullName $** 대체 (fullname) 매개 변수를 사용 합니다. 자세한 내용은 [대체 가능 매개 변수](../sharepoint/replaceable-parameters.md)를 참조 하세요.|
|**IsSafe**|선택적 **xs: boolean** 특성입니다.<br /><br /> 신뢰할 수 없는 사용자가 액세스할 수 있도록 ASPX 컨트롤이 나 웹 파트를 안전 하 게 보호 하는지 여부를 지정 합니다.|
|**Issafeagas 스크립트**|선택적 **xs: boolean** 특성입니다.<br /><br /> 신뢰할 수 없는 사용자가 ASPX 컨트롤이 나 웹 파트의 속성을 보거나 편집할 수 있는지 여부를 지정 합니다.|
|**이름**|선택적 **xs: string** 특성입니다.<br /><br /> 컬렉션에 있는이 안전 컨트롤 항목의 이름입니다.|
|**네임스페이스**|선택적 **xs: string** 특성입니다.<br /><br /> ASPX 컨트롤 또는 웹 파트의 네임 스페이스입니다.|
|**T**|선택적 **xs: string** 특성입니다.<br /><br /> ASPX 컨트롤 또는 웹 파트의 형식 이름입니다.|

### <a name="child-elements"></a>자식 요소
 없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[SafeControls](../sharepoint/safecontrols-element.md)|사용자가 SharePoint 사이트의 ASPX 페이지에서 액세스할 수 있도록 보안으로 지정 된 ASPX 컨트롤 및 웹 파트의 컬렉션을 나타냅니다.|

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
