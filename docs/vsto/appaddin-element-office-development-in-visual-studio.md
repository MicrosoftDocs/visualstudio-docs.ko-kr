---
title: '&lt;appAddin &gt; 요소 (Visual Studio에서 Office 개발)'
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <appAddin> element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1bf9ea990d12bd24adee3f6a24a39fa43c74fb71
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85531640"
---
# <a name="ltappaddingt-element-office-development-in-visual-studio"></a>&lt;appAddin &gt; 요소 (Visual Studio에서 Office 개발)
  네임 스페이스의 **Appaddin** 요소는 `vstov4` VSTO 추가 기능에 대 한 사용자 지정 관련 정보를 저장 합니다.

## <a name="syntax"></a>구문

```xml
<appAddin
  application
  loadBehavior
  keyName>
  <friendlyName>
  <description>
  <formRegions></formRegions>
</appAddin>
```

## <a name="elements-and-attributes"></a>요소 및 특성
 **Appaddin** 요소는 필수 이며 `vstov4` 네임 스페이스에 있습니다. 응용 프로그램 매니페스트에는 **Appaddin** 요소가 하나만 정의 되어 있습니다.

 **Appaddin** 요소에는 다음과 같은 특성이 있습니다.

|특성|설명|
|---------------|-----------------|
|**애플리케이션**|필수 요소. Microsoft Office 애플리케이션을 식별합니다. 값은 Excel, InfoPath, Outlook, PowerPoint, Project, Visio 또는 Word 중 하나입니다.|
|**loadBehavior**|선택 사항입니다. 기본적으로이 값을로 설정 하 여 **loadBehavior** 를 사용 하도록 설정 합니다. 디버깅을 위해서는 이 값을 2로 설정하여 VSTO 추가 기능을 사용하지 않도록 설정할 수 있습니다. 자세한 내용은 [VSTO 추가 기능에 대 한 레지스트리 항목](../vsto/registry-entries-for-vsto-add-ins.md)의 LoadBehavior Values 이라는 표를 참조 하세요.|
|**keyName**|필수 요소. 이 값은 애플리케이션에서 VSTO 추가 기능을 로드할 때 사용할 레지스트리 키 이름입니다. 자세한 내용은 [VSTO 추가 기능에 대 한 레지스트리 항목](../vsto/registry-entries-for-vsto-add-ins.md)을 참조 하세요.|

 **Appaddin** 요소에는 다음과 같은 자식 요소가 있습니다.

### <a name="friendlyname"></a>friendlyName
 선택 사항입니다. **Friendlyname** 요소는 [&#60;friendlyname&#62; 요소 &#40;Visual Studio에서 Office 개발&#41;](../vsto/friendlyname-element-office-development-in-visual-studio.md)에 설명 되어 있습니다.

### <a name="description"></a>description
 선택 사항입니다. **Description** 요소는 [Visual Studio&#41;에서 Office 개발을 &#40;&#62; 요소&#60;설명 ](../vsto/description-element-office-development-in-visual-studio.md)에 설명 되어 있습니다.

### <a name="formregions"></a>formRegions
 양식 영역을 포함하는 Outlook VSTO 추가 기능에 대해서만 필수 요소. **Formregions** 요소는 [Visual Studio&#41;에서 Office 개발 &#40;요소&#62;&#60;formregions ](../vsto/formregions-element-office-development-in-visual-studio.md)에 설명 되어 있습니다.

## <a name="vsto-add-in-example"></a>VSTO 추가 기능 예제

### <a name="description"></a>설명
 다음 코드 예제에서는를 사용 하 여 배포 된 Outlook 솔루션의 **Appaddin** 요소를 보여 줍니다 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . 이 코드 예제는 [Office 솔루션의 응용 프로그램 매니페스트에](../vsto/application-manifests-for-office-solutions.md)제공 된 더 큰 예제의 일부입니다.

### <a name="code"></a>코드

```xml
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
```

## <a name="see-also"></a>참고 항목

- [Office 솔루션의 응용 프로그램 매니페스트](../vsto/application-manifests-for-office-solutions.md)
- [Office 솔루션에 대 한 배포 매니페스트](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce 응용 프로그램 매니페스트](../deployment/clickonce-application-manifest.md)