---
title: '&lt;formRegions &gt; 요소 (Visual Studio에서 Office 개발)'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- formRegions element
- <formRegions> element
- application manifests [Office development in Visual Studio], <formRegions> element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6f98c74c2df998f0e79f5b95a316a7917304e029
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85538361"
---
# <a name="ltformregionsgt-element-office-development-in-visual-studio"></a>&lt;formRegions &gt; 요소 (Visual Studio에서 Office 개발)
  `formRegions`네임 스페이스의 요소는 `vstov4` VSTO 추가 기능에 연결 된 Microsoft Office Outlook 양식 영역을 포함 합니다.

## <a name="syntax"></a>Syntax

```xml
<formRegions>
  <formRegion>
  </formRegion>
</formRegions>
```

## <a name="elements-and-attributes"></a>요소 및 특성
 `formRegions` 네임스페이스의 `vstov4` 요소에는 Outlook VSTO 추가 기능에 대한 모든 `formRegion` 요소가 포함됩니다. 양식 영역을 포함하는 Outlook VSTO 추가 기능에만 필요합니다.

 하나의 애플리케이션 매니페스트에서는 하나의 `formRegions` 요소만 정의할 수 있습니다.

 `formRegions` 요소에는 특성이 없습니다.

 `formRegions` 요소에는 다음 요소가 있습니다.

### <a name="formregion"></a>formRegion
 양식 영역을 포함하는 Outlook VSTO 추가 기능에 필요합니다. `formRegion`요소는 [Visual Studio&#41;에서 Office 개발 &#40;&#60;n&#62; 요소 ](../vsto/formregion-element-office-development-in-visual-studio.md)에 정의 됩니다.

## <a name="vsto-add-in-example"></a>VSTO 추가 기능 예제

### <a name="description"></a>설명
 다음 코드 예제에서는 `formRegions` 을 사용하여 배포된 애플리케이션 수준의 Office 솔루션에 대한 애플리케이션 매니페스트의 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]요소를 보여 줍니다. 이 코드 예제는 [Office 솔루션의 응용 프로그램 매니페스트에](../vsto/application-manifests-for-office-solutions.md)제공 된 더 큰 예제의 일부입니다.

### <a name="code"></a>코드

```xml
<vstov4:formRegions>
  <vstov4:formRegion
      name="OutlookAddIn1.FormRegion1">
    <vstov4:messageClass name="IPM.Note" />
    <vstov4:messageClass name="IPM.Contact" />
    <vstov4:messageClass name="IPM.Appointment" />
  </vstov4:formRegion>
</vstov4:formRegions>
```

## <a name="see-also"></a>참조

- [Office 솔루션의 응용 프로그램 매니페스트](../vsto/application-manifests-for-office-solutions.md)
- [Office 솔루션에 대 한 배포 매니페스트](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce 응용 프로그램 매니페스트](../deployment/clickonce-application-manifest.md)