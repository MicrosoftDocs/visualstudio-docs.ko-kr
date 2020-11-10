---
title: MSBuild 모범 사례 | Microsoft Docs
description: 와일드 카드를 사용하지 않고 Condition 특성을 사용하는 것과 같은 MSBuild 스크립트 작성 모범 사례에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- best practices, MSBuild
- MSBuild, best practices
ms.assetid: 90ef8693-e921-410a-a377-fe4d13f58c48
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2742324f737a4e70221e3cbe4c78cff56fa7e7ca
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93047655"
---
# <a name="msbuild-best-practices"></a>MSBuild 모범 사례

MSBuild 스크립트를 작성할 때는 다음 모범 사례를 따르는 것이 좋습니다.

- 기본 속성 값은 명령줄에서 기본값을 재정의할 수 있는 속성을 선언하는 대신 `Condition` 특성을 사용하여 처리하는 것이 가장 효율적입니다. 예를 들어 다음과 같은 코드를 사용합니다.

```xml
<MyProperty Condition="'$(MyProperty)' == ''">
   MyDefaultValue
</MyProperty>
```

- 일반적으로 항목을 선택할 때 와일드카드를 사용하지 않는 것이 좋습니다. 대신 파일을 명시적으로 지정합니다. 대부분의 프로젝트 형식에서 MSBuild가 항목을 추가하거나 제거할 때와 같이 다양한 때에 와일드카드를 확장하여 예기치 않은 동작이 발생할 수 있기 때문입니다. 이에 대한 예외는 와일드카드를 올바르게 처리하는 .NET Core SDK 스타일의 프로젝트에 있습니다.

## <a name="see-also"></a>참조

- [고급 개념](../msbuild/msbuild-advanced-concepts.md)
