---
title: LINQ 식 간소화
description: 이 리팩터링은 Where 메서드에 대한 Enumerable 불필요한 호출을 제거하는 데 사용됩니다.
ms.date: 08/12/2020
ms.topic: reference
author: m-redding
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 20a3524d786b1f03fc3e221d1b257892d9439a0b
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/08/2021
ms.locfileid: "102466169"
---
# <a name="simplify-linq-expression"></a>LINQ 식 간소화

이 리팩터링은 다음에 적용됩니다.

- C#

**내용:** `SomeEnumerableType.Where(<LambdaExpression>).Single()` 인스턴스를 `SomeEnumerable.Single(<LambdaExpression>)`로 리팩터링합니다. 이는 `Enumerable.Single()`뿐만 아니라 `SingleOrDefault()`, `Last()`, `LastOrDefault()`, `Any()`, `Count()`, `First()`, `FirstOrDefault()` 등의 Enumerable 메서드에도 적용됩니다.

**시기:**  `Single()`, `SingleOrDefault()` 등의 메서드 호출이 인수를 포함하지 않으며 `Where()` 식 뒤에 오는 모든 인스턴스. `Where()` 식에 대한 입력은 식 트리로 생성될 수 없습니다.

**이유:** `.Where()` 메서드에 대한 불필요한 Enumerable 호출을 제거하면 성능과 가독성이 향상됩니다.

## <a name="how-to"></a>방법

1. Visual Studio에서 `SomeEnumerableType.Where(<LambdaExpression>).Single()` 인스턴스 내에 커서를 놓습니다.
2. 줄의 임의 위치에서 **Ctrl**+ **.** 를 눌러 **빠른 작업 및 리팩터링** 메뉴를 트리거합니다.
3. **LINQ 식 간소화** 를 선택합니다.

   ![typeof를 nameof로 변환](media/simplify-linq-expression.png)

## <a name="see-also"></a>참고 항목

- [리팩터링](../refactoring-in-visual-studio.md)
