---
title: '&lt;customHostSpecified 된 &gt; 요소 (Visual Studio에서 Office 개발)'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <customHostSpecified> element
- <customHostSpecified> element
- customHostSpecified element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 689848f14b4540a54489b4ea5bbad67e493fe276
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544913"
---
# <a name="ltcustomhostspecifiedgt-element-office-development-in-visual-studio"></a>&lt;customHostSpecified 된 &gt; 요소 (Visual Studio에서 Office 개발)
  `customHostSpecified`요소는이 솔루션이 독립 실행형 응용 프로그램이 아님을 나타냅니다. Office 솔루션에는 Microsoft Office 응용 프로그램 내에서 호스팅되는 구성 요소가 포함 되어 있습니다.

## <a name="syntax"></a>구문

```xml
<customHostSpecified />
```

## <a name="elements-and-attributes"></a>요소 및 특성
 `customHostSpecified`요소는 Office 솔루션에 필요 합니다. 이 요소는 `co.v1` 네임 스페이스에 있으며,이 배포에는 사용자 지정 호스트 내에 배포 되 고 독립 실행형 응용 프로그램이 아닌 구성 요소가 포함 되도록 지정 합니다.

 이 요소는 `<entrypoint>` 응용 프로그램 매니페스트에서 첫 번째 요소의 자식입니다. 해당 요소에 다른 자식 요소가 없을 수도 있고 `<entrypoint>` 설치 하는 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 동안 유효성 검사 오류를 발생 시킬 수도 있습니다.

 이 요소에는 특성이 없고 자식 요소가 없습니다.

## <a name="example"></a>예제
 다음 코드 예제에서는 `customHostSpecified` Office 솔루션에 대 한 응용 프로그램 매니페스트의 요소를 보여 줍니다. 이 코드 예제는 [Office 솔루션의 응용 프로그램 매니페스트에](../vsto/application-manifests-for-office-solutions.md)제공 된 더 큰 예제의 일부입니다.

```xml
<entryPoint>
    <co.v1:customHostSpecified />
</entryPoint>
```

## <a name="see-also"></a>참고 항목

- [Office 솔루션의 응용 프로그램 매니페스트](../vsto/application-manifests-for-office-solutions.md)
- [Office 솔루션에 대 한 배포 매니페스트](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce 응용 프로그램 매니페스트](../deployment/clickonce-application-manifest.md)