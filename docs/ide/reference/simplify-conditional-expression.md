---
title: 조건식 단순화
ms.date: 06/08/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: d0571c01217441d4a39fbfe6fb58ccfe95fd0c5a
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85290957"
---
# <a name="simplify-conditional-expression-refactoring"></a>조건식 단순화 리팩터링

이 리팩터링은 다음에 적용됩니다.

- C#

**내용:** [조건식](https://docs.microsoft.com/dotnet/csharp/language-reference/operators/conditional-operator)을 단순화할 수 있습니다.

**시기:** 불필요한 코드를 제거하여 더 명확하게 지정하려고 합니다.

**이유:** 조건식을 단순화하면 보다 명확하고 간결한 구문을 제공할 수 있습니다. 이 리팩터링 도구는 작업을 수동으로 수행하지 않고 자동 수행합니다.

## <a name="how-to"></a>방법

1. 조건식에 캐럿을 배치합니다.

2. 줄의 임의 위치에서 **Ctrl**+ **.** 를 눌러 **빠른 작업 및 리팩터링** 메뉴를 트리거합니다.

3. **조건식 단순화**를 선택합니다.

    ![조건식 단순화](media/simplify-conditional-expression.png)

## <a name="see-also"></a>참조

- [리팩터링](../refactoring-in-visual-studio.md)