---
title: '&lt;document &gt; 요소 (Visual Studio에서 Office 개발)'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- document element
- application manifests [Office development in Visual Studio], <document> element
- <document> element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 36d822d60d1a28d48f660f6d358b75bf4a913048
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "63000031"
---
# <a name="ltdocumentgt-element-office-development-in-visual-studio"></a>&lt;document &gt; 요소 (Visual Studio에서 Office 개발)
  `document`네임 스페이스의 요소는 `vstov4` 문서 수준 사용자 지정에 대 한 사용자 지정 관련 정보를 저장 합니다.

## <a name="syntax"></a>Syntax

```xml
<document solutionId />
```

## <a name="elements-and-attributes"></a>요소 및 특성
 문서 수준 사용자 지정에만 필요 합니다. `document` 요소는 `vstov4` 네임스페이스에 있습니다. `document` 요소에는 다음 특성이 있습니다.

|특성|설명|
|---------------|-----------------|
|`solutionId`|필수 요소. Visual Studio Tools for Office 런타임에서 문서 수준 솔루션을 고유 하 게 식별 하는 데 사용 되는 GUID입니다. 이 값은 _AssemblyLocation 사용자 지정 문서 속성으로 저장 됩니다. 자세한 내용은 [사용자 지정 문서 속성 개요](../vsto/custom-document-properties-overview.md)를 참조 하세요.|

 `document` 에는 자식 요소가 없습니다.

## <a name="document-level-customization-example"></a>문서 수준 사용자 지정 예제

### <a name="description"></a>설명
 다음 코드 예제에서는를 `document` 사용 하 여 배포 된 문서 수준 Office 솔루션의 요소를 보여 줍니다 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . 이 코드 예제는 [Office 솔루션의 응용 프로그램 매니페스트에](../vsto/application-manifests-for-office-solutions.md)제공 된 더 큰 예제의 일부입니다.

### <a name="code"></a>코드

```xml
<vstov4:document
  solutionId="73e" />
```

## <a name="see-also"></a>참조

- [Office 솔루션의 응용 프로그램 매니페스트](../vsto/application-manifests-for-office-solutions.md)
- [Office 솔루션에 대 한 배포 매니페스트](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce 응용 프로그램 매니페스트](../deployment/clickonce-application-manifest.md)