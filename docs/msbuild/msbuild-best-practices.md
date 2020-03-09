---
title: MSBuild 모범 사례 | Microsoft Docs
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
ms.openlocfilehash: 91b2e157ee64f5e4d91bc75a5d6f8d65d4312862
ms.sourcegitcommit: 3ed59ce39692124fe61c484df4348c0b9abee9b9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78263151"
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
