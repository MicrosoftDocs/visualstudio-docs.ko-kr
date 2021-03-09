---
title: '&lt;postAction &gt; 요소 (Visual Studio에서 Office 개발)'
description: Vstav3 네임 스페이스의 postAction 요소에는 진입점 요소 및 배포 후 작업과 관련 된 모든 postActionData 요소가 포함 됩니다 .이 요소는 Office 솔루션이 설치 된 후 실행 됩니다.
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <postAction> element
- <postAction> element
- postAction element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 04f8c92c52aeee9f7f1dd5ab67b3dcef3a295474
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/08/2021
ms.locfileid: "102470055"
---
# <a name="ltpostactiongt-element-office-development-in-visual-studio"></a>&lt;postAction &gt; 요소 (Visual Studio에서 Office 개발)
  `postAction` 네임스페이스의 `vstav3` 요소에는 `entrypoint` 요소 및 배포 후 작업과 관련된 모든 `postActionData` 요소가 포함되며 Office 솔루션 설치 후 실행됩니다.

## <a name="syntax"></a>구문

```xml
<postAction>
  <entryPoint>
  </entryPoint>
  <postActionData>
  </postActionData>
</postAction>
```

## <a name="elements-and-attributes"></a>요소 및 특성
 `postAction` 요소는 선택적이며 `vstav3` 네임스페이스에 있습니다. 하나의 애플리케이션 매니페스트에서는 각 배포 후 작업에 대해 하나의 `postAction` 요소만 정의할 수 있습니다.

 `postAction` 요소에는 특성이 없습니다.

 `postAction` 에는 다음 요소가 있습니다.

### <a name="entrypoint"></a>entryPoint
 선택 사항입니다. `entryPoint`네임 스페이스에 있는 요소의 역할은 `vstav3` [Visual Studio&#41;에서 Office 개발 &#40;&#60;진입점&#62; 요소 ](../vsto/entrypoints-element-office-development-in-visual-studio.md)에 정의 됩니다.

### <a name="postactiondata"></a>postActionData
 선택 사항입니다. `postActionData`네임 스페이스에 있는 요소의 역할은 `vstav3` [Visual Studio&#41;에서 Office 개발 &#40;&#60;postactiondata&#62; 요소 ](../vsto/postactiondata-element-office-development-in-visual-studio.md)에 정의 됩니다.

## <a name="post-deployment-action-example"></a>배포 후 작업 예제

### <a name="description"></a>Description
 다음 코드 예제에서는 `postAction` 을 사용하여 배포된 Office 솔루션에 대한 애플리케이션 매니페스트의 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]요소를 보여 줍니다. 이 코드 예제는 [Office 솔루션의 응용 프로그램 매니페스트에](../vsto/application-manifests-for-office-solutions.md)제공 된 더 큰 예제의 일부입니다.

### <a name="code"></a>코드

```xml
<vstav3:postAction>
  <vstav3:entryPoint
    class="PostDeploymentAction.PostDeploymentActionSample">
    <assemblyIdentity
      name="PostDeploymentAction"
      version="1.0.0.0"
      language="neutral"
      processorArchitecture="msil" />
  </vstav3:entryPoint>
  <vstav3:postActionData>
  </vstav3:postActionData>
</vstav3:postAction>
```

## <a name="see-also"></a>참조

- [Office 솔루션의 응용 프로그램 매니페스트](../vsto/application-manifests-for-office-solutions.md)
- [Office 솔루션에 대 한 배포 매니페스트](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce 응용 프로그램 매니페스트](../deployment/clickonce-application-manifest.md)
