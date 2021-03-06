---
description: Vstov4 네임 스페이스의 friendlyName 요소는 설치 된 프로그램 목록에 표시 되는 이름을 저장 합니다.
title: '&lt;friendlyName &gt; 요소 (Visual Studio에서 Office 개발)'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <friendlyName> element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: adcf46a2c232176026181283549c0c59fc713603
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102223448"
---
# <a name="ltfriendlynamegt-element-office-development-in-visual-studio"></a>&lt;friendlyName &gt; 요소 (Visual Studio에서 Office 개발)
  `friendlyName` 네임스페이스의 `vstov4` 요소는 설치된 프로그램 목록에 표시되는 이름을 저장합니다.

## <a name="syntax"></a>구문

```xml
<friendlyName>
</friendlyName>
```

## <a name="elements-and-attributes"></a>요소 및 특성
 `friendlyName` 요소는 `vstov4` 네임스페이스에 있습니다. 값이 컴퓨터에 설치된 프로그램 목록 및 Microsoft Office 애플리케이션의 COM VSTO 추가 기능 대화 상자에 표시됩니다.

 `friendlyName` 요소에는 특성 또는 자식 요소가 없습니다.

## <a name="vsto-add-in-example"></a>VSTO 추가 기능 예제

### <a name="description"></a>설명
 다음 코드 예제에서는 `friendlyName` 을 사용하여 배포된 애플리케이션 수준 솔루션의 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]요소를 보여 줍니다. 이 코드 예제는 [Office 솔루션의 응용 프로그램 매니페스트에](../vsto/application-manifests-for-office-solutions.md)제공 된 더 큰 예제의 일부입니다.

### <a name="code"></a>코드

```xml
<vstov4:friendlyName>
  ContosoOutlookAddIn
</vstov4:friendlyName>
```

## <a name="see-also"></a>참조

- [Office 솔루션의 응용 프로그램 매니페스트](../vsto/application-manifests-for-office-solutions.md)
- [Office 솔루션에 대 한 배포 매니페스트](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce 응용 프로그램 매니페스트](../deployment/clickonce-application-manifest.md)
