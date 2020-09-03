---
title: '&lt;description &gt; 요소 (Visual Studio에서 Office 개발)'
titleSuffix: ''
ms.custom: secdec18
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- description element
- <description> element
- application manifests [Office development in Visual Studio], <description> element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4c8b54f8ccf2181a053ae5d2fe221b49840cd72c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85520269"
---
# <a name="ltdescriptiongt-element-office-development-in-visual-studio"></a>&lt;description &gt; 요소 (Visual Studio에서 Office 개발)
  `description` 네임스페이스의 `vstov4` 요소는 Microsoft Office 애플리케이션의 COM 추가 기능 대화 상자에 나타나는 Office 솔루션에 대한 설명을 저장합니다.

## <a name="syntax"></a>구문

```xml
<description>
</description>
```

## <a name="elements-and-attributes"></a>요소 및 특성
 선택 사항입니다. `description` 요소는 `vstov4` 네임스페이스에 있습니다. Microsoft Office 애플리케이션의 COM 추가 기능 대화 상자에 표시되는 추가 기능에 대한 설명이 포함됩니다.

 `description` 요소에는 특성 또는 요소가 없습니다.

## <a name="vsto-add-in-example"></a>VSTO 추가 기능 예제

### <a name="description"></a>설명
 다음 코드 예제에서는 `description` 를 사용하여 배포된 애플리케이션 수준 솔루션의 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]요소를 보여 줍니다. 이 코드 예제는 [Office 솔루션의 응용 프로그램 매니페스트에](../vsto/application-manifests-for-office-solutions.md)제공 된 더 큰 예제의 일부입니다.

### <a name="code"></a>코드

```xml
<vstov4:description>
  ContosoOutlookAddIn - Outlook add-in
  created with Visual Studio Tools for Office
</vstov4:description>
```

## <a name="see-also"></a>참조

- [Office 솔루션의 응용 프로그램 매니페스트](../vsto/application-manifests-for-office-solutions.md)
- [Office 솔루션에 대 한 배포 매니페스트](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce 응용 프로그램 매니페스트](../deployment/clickonce-application-manifest.md)