---
title: '&lt;사용자 지정 &gt; 요소 (Visual Studio에서 Office 개발)'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <customization> element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1239c6749f25bf4bce7a1f5cc89a2a8430c98a4d
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544874"
---
# <a name="ltcustomizationgt-element-office-development-in-visual-studio"></a>&lt;사용자 지정 &gt; 요소 (Visual Studio에서 Office 개발)
  `customization` 네임스페이스의 `vstov4` 요소는 특정 Office 솔루션에 대해 설명합니다. 문서 수준 사용자 지정 및 VSTO 추가 기능에 대한 자식 요소가 서로 다릅니다.

## <a name="syntax-for-document-level-customizations"></a>문서 수준 사용자 지정 구문

```xml
<customization
  id
  <document
    solutionId
  />
</customization>
```

## <a name="syntax-for-vsto-add-ins"></a>VSTO 추가 기능에 대한 구문

```xml
<customization
  id
  <appAddin
    application
    loadBehavior
    keyName>
  <friendlyName></friendlyName>
  <description></description>
  <formRegions></formRegions>
</customization>
```

## <a name="elements-and-attributes"></a>요소 및 특성
 `customization` 요소에는 사용자 지정 관련 정보가 포함됩니다. 이 요소는 `vstov4=urn:schemas-microsoft-com:vsto.v4`네임스페이스에 있어야 합니다. 각 Office 솔루션에 대해 하나의 `customization` 요소가 있습니다. 예를 들어 다중 프로젝트 배포에서 세 개의 Office 솔루션을 배포하면 애플리케이션 매니페스트에 세 개의 `customization` 요소가 있습니다.

 어셈블리의 자식 요소도 이 네임스페이스에 있어야 합니다.

 `customization` 요소에는 다음 특성이 있습니다.

|특성|설명|
|---------------|-----------------|
|`id`|다중 프로젝트 배포의 경우 필수 요소입니다. `id` 요소는 Office 솔루션을 고유하게 식별합니다.|

### <a name="document-level-customizations"></a>문서 수준 사용자 지정
 `customization` 요소에는 다음 자식 요소가 있습니다.

#### <a name="document"></a>문서
 `document`네임 스페이스의 요소는 `vstov4` [Visual Studio&#41;에서 Office 개발 &#40;&#60;문서&#62; 요소 ](../vsto/document-element-office-development-in-visual-studio.md)에 정의 되어 있습니다.

### <a name="vsto-add-ins"></a>VSTO 추가 기능
 `customization` 요소에는 다음 자식 요소가 있습니다.

#### <a name="appaddin"></a>appAddin
 `appAddin`네임 스페이스의 요소는 `vstov4` [Visual Studio&#41;에서 Office 개발 &#40;&#60;appaddin&#62; 요소 ](../vsto/appaddin-element-office-development-in-visual-studio.md)에 정의 되어 있습니다.

## <a name="example-of-a-document-level-customization"></a>문서 수준 사용자 지정 예제

### <a name="description"></a>설명
 다음 코드 예제에서는 문서 수준 사용자 지정의 `customization` 요소를 보여 줍니다. 이 코드 예제는 [Office 솔루션의 응용 프로그램 매니페스트에](../vsto/application-manifests-for-office-solutions.md)제공 된 더 큰 예제의 일부입니다.

### <a name="code"></a>코드

```xml
<vstov4:customization>
  <vstov4:document
    solutionId="73e" />
</vstov4:customization>
```

## <a name="example-of-a-vsto-add-in"></a>VSTO 추가 기능의 예

### <a name="description"></a>설명
 다음 코드 예제에서는 VSTO 추가 기능의 요소를 보여 줍니다 `customization` . 양식 영역을 포함하는 Outlook VSTO 추가 기능입니다. 이 코드 예제는 [Office 솔루션의 응용 프로그램 매니페스트에](../vsto/application-manifests-for-office-solutions.md)제공 된 더 큰 예제의 일부입니다.

### <a name="code"></a>코드

```xml
<vstov4:customization>
  <vstov4:appAddIn
    application="Outlook"
    loadBehavior="3"
    keyName="ContosoOutlookAddIn">
    <vstov4:friendlyName>
      ContosoOutlookAddIn
    </vstov4:friendlyName>
    <vstov4:description>
      ContosoOutlookAddIn - Outlook VSTO Add-in
      created with Visual Studio Tools for Office
    </vstov4:description>
    <vstov4:formRegions>
      <vstov4:formRegion
          name="OutlookAddIn1.FormRegion1">
        <vstov4:messageClass name="IPM.Note" />
        <vstov4:messageClass name="IPM.Contact" />
        <vstov4:messageClass name="IPM.Appointment" />
      </vstov4:formRegion>
    </vstov4:formRegions>
  </vstov4:appAddIn>
</vstov4:customization>
```

## <a name="see-also"></a>참고 항목

- [Office 솔루션의 응용 프로그램 매니페스트](../vsto/application-manifests-for-office-solutions.md)
- [Office 솔루션에 대 한 배포 매니페스트](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce 응용 프로그램 매니페스트](../deployment/clickonce-application-manifest.md)