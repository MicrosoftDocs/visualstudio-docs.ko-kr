---
title: '&lt;M e &gt; 요소 (Visual Studio에서 Office 개발)'
titleSuffix: ''
description: Vstav3 네임 스페이스의 M e 요소에는 특정 Office 솔루션에 대해 지원 되는 Visual Studio Tools for Office 런타임 버전이 포함 되어 있습니다.
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <vstoRuntime> element
- <vstoRuntime> element
- vstoRuntime element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 7c856836bd2ba107a2fa6c3017c5ecb2694fcf6b
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/08/2021
ms.locfileid: "102468574"
---
# <a name="ltvstoruntimegt-element-office-development-in-visual-studio"></a>&lt;M e &gt; 요소 (Visual Studio에서 Office 개발)
  `vstoRuntime` 네임스페이스의 `vstav3` 요소에는 특정 Office 솔루션에 대해 지원되는 Visual Studio Tools for Office Runtime 버전이 포함됩니다.

## <a name="syntax"></a>구문

```xml
<vstoRuntime
    release
    version
    supportUrl />
```

## <a name="elements-and-attributes"></a>요소 및 특성
 `vstoRuntime` 요소는 필수이며 `vstav3` 네임스페이스에 있습니다. Office 솔루션이 Visual Studio Tools for Office Runtime의 두 가지 버전을 지원하는 경우 애플리케이션 매니페스트에는 두 개의 `vstoRuntime` 요소가 있습니다.

 `vstoRuntime` 요소에는 다음 특성이 있습니다.

|attribute|Description|
|---------------|-----------------|
|`release`|필수 요소. Visual Studio Tools for Office Runtime의 릴리스 버전입니다.|
|`version`|필수 요소. Visual Studio Tools for Office Runtime 버전 번호입니다.|
|`supportUrl`|선택 사항입니다. Visual Studio Tools for Office Runtime의 설치 위치에 연결합니다.|

 `vstoRuntime` 에는 요소가 없습니다.

## <a name="example"></a>예제
 다음 코드 예제에서는 `vstoRuntime` 을 사용하여 배포된 Office 솔루션에 대한 애플리케이션 매니페스트의 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]요소를 보여 줍니다. 이 코드 예제는 [Office 솔루션의 응용 프로그램 매니페스트에](../vsto/application-manifests-for-office-solutions.md)제공 된 더 큰 예제의 일부입니다.

```xml
<vstav3:vstoRuntime
    release="VSTOR40Beta1"
    version="10.0.20303"
    supportUrl="http://www.microsoft.com" />
```

## <a name="see-also"></a>참고 항목

- [Office 솔루션의 응용 프로그램 매니페스트](../vsto/application-manifests-for-office-solutions.md)
- [Office 솔루션에 대 한 배포 매니페스트](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce 응용 프로그램 매니페스트](../deployment/clickonce-application-manifest.md)
