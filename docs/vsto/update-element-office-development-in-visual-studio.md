---
title: '&lt;update &gt; 요소 (Visual Studio에서 Office 개발)'
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- update element
- <update> element
- application manifests [Office development in Visual Studio], <update> element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 241bddb8c79a01bb1ba6921486a4dc46d99940cc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85537386"
---
# <a name="ltupdategt-element-office-development-in-visual-studio"></a>&lt;update &gt; 요소 (Visual Studio에서 Office 개발)
  `update`요소는 솔루션에서 업데이트를 확인 하는 간격을 지정 합니다.

## <a name="syntax"></a>Syntax

```xml
<update
  enabled>
  <expiration
    maximumAge
    unit
  />
</update>
```

## <a name="elements-and-attributes"></a>요소 및 특성
 `update` 요소는 필수이며 `vstav3` 네임스페이스에 있습니다.

 `update` 요소에는 다음 특성이 있습니다.

|특성|설명|
|---------------|-----------------|
|`enabled`|필수 요소. 사용을 다음 값 중 하나로 설정 합니다.<br /><br /> -   업데이트를 확인 하려면 **true로 설정** 합니다.<br />-   **false로 설정** 하면 업데이트를 확인할 수 없습니다.|

 `update` 요소에는 다음 자식 요소가 있습니다.

### <a name="expiration"></a>expiration
 `expiration` 요소는 필수이며 `vstav3` 네임스페이스에 있습니다. 이 요소는 솔루션이 업데이트를 확인 하는 간격을 지정 합니다.

 `expiration` 요소에는 다음 특성이 있습니다.

|특성|설명|
|---------------|-----------------|
|`maximumAge`| 필수 요소. 이 값을 정수로 설정 합니다.|
|`unit`|필수 요소. `unit`을 다음 값 중 하나로 설정 합니다.<br /><br /> -   **시간의**<br />-   **일별로**<br />-   **걸릴**|

## <a name="example-of-always-checking-for-updates"></a>업데이트를 항상 확인 하는 예

### <a name="description"></a>설명
 다음 코드 예제에서는 `update` Office 솔루션에서 항상 업데이트를 확인 하도록 설정 된 요소를 보여 줍니다.

### <a name="code"></a>코드

```xml
<vstav3:update enabled="true" />
```

## <a name="example-of-setting-a-default-update-interval"></a>기본 업데이트 간격을 설정 하는 예

### <a name="description"></a>설명
 다음 코드 예제에서는 `update` Office 솔루션에 대 한 응용 프로그램 매니페스트의 요소를 보여 줍니다. 이 코드 예제는 [Office 솔루션의 응용 프로그램 매니페스트에](../vsto/application-manifests-for-office-solutions.md)제공 된 더 큰 예제의 일부입니다.

### <a name="code"></a>코드

```xml
<vstav3:update enabled="true">
    <vstav3:expiration maximumAge="7" unit="days" />
</vstav3:update>
```

## <a name="see-also"></a>참조

- [ClickOnce를 사용 하 여 Office 솔루션 배포](../vsto/deploying-an-office-solution-by-using-clickonce.md)
- [Office 솔루션의 응용 프로그램 매니페스트](../vsto/application-manifests-for-office-solutions.md)
- [Office 솔루션에 대 한 배포 매니페스트](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce 응용 프로그램 매니페스트](../deployment/clickonce-application-manifest.md)
