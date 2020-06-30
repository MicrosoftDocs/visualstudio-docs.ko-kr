---
title: '&lt;n &gt; 요소 (Visual Studio에서 Office 개발)'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <formRegion> element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9e13576ef673728d673d0351cf289a80944584bd
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85543534"
---
# <a name="ltformregiongt-element-office-development-in-visual-studio"></a>&lt;n &gt; 요소 (Visual Studio에서 Office 개발)
  `formRegion`네임 스페이스의 요소는 `vstov4` VSTO 추가 기능에 연결 된 Microsoft Office Outlook 양식 영역을 식별 합니다.

## <a name="syntax"></a>구문

```xml
<formRegion
  name>
  <messageClass
    name/>
</formRegion>
```

## <a name="elements-and-attributes"></a>요소 및 특성
 `formRegion` 네임스페이스의 `vstov4` 요소는 Outlook VSTO 추가 기능과 관련된 양식 영역을 식별합니다. 양식 영역을 포함하는 Outlook VSTO 추가 기능에만 필요합니다.

 단일 VSTO 추가 기능에 대해 `formRegion` 요소 내에 정의된 여러 `formRegions` 요소가 있을 수 있습니다.

 `formRegion` 요소에는 다음 특성이 있습니다.

|특성|설명|
|---------------|-----------------|
|`name`|필수 사항입니다. 양식 영역 이름을 식별합니다.|

 `formRegion` 요소에는 다음 자식 요소가 있습니다.

### <a name="messageclass"></a>messageClass
 `messageClass` 요소는 양식 영역과 관련된 Outlook 양식을 식별합니다.

 `messageClass` 요소에는 다음 특성이 있습니다.

|특성|설명|
|---------------|-----------------|
|`name`|필수 사항입니다. 양식 영역과 관련된 양식을 식별합니다.|

## <a name="example"></a>예제
 다음 코드 예제에서는 `formRegion` 을 사용하여 배포된 Outlook VSTO 추가 기능에 대한 애플리케이션 매니페스트의 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]요소를 보여 줍니다. 이 양식 영역과 관련된 세 개의 메시지 클래스가 있습니다. 이 코드 예제는 [Office 솔루션의 응용 프로그램 매니페스트에](../vsto/application-manifests-for-office-solutions.md)제공 된 더 큰 예제의 일부입니다.

```xml
<vstov4:formRegion
    name="OutlookAddIn1.FormRegion1">
  <vstov4:messageClass name="IPM.Note" />
  <vstov4:messageClass name="IPM.Contact" />
  <vstov4:messageClass name="IPM.Appointment" />
</vstov4:formRegion>
```

## <a name="see-also"></a>참고 항목

- [Outlook 양식 영역 만들기](../vsto/creating-outlook-form-regions.md)
- [Office 솔루션의 응용 프로그램 매니페스트](../vsto/application-manifests-for-office-solutions.md)
- [Office 솔루션에 대 한 배포 매니페스트](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce 응용 프로그램 매니페스트](../deployment/clickonce-application-manifest.md)