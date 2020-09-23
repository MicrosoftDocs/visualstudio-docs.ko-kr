---
title: 문자열 보간 간소화
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 5e801d417280d5d9ce8225c2185b582544fe2cef
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810339"
---
# <a name="simplify-string-interpolation-refactoring"></a>문자열 보간 리팩터링 간소화

이 리팩터링은 다음에 적용됩니다.

- C#

- Visual Basic

**내용:** [문자열 보간](/dotnet/csharp/tutorials/string-interpolation)을 간소화할 수 있습니다.

**시기:** 간소화할 수 있는 문자열 보간이 있습니다.

**이유:** 문자열 보간을 간소화하면 더욱 명확하고 간결한 구문을 제공할 수 있습니다. 이 리팩터링 도구는 작업을 수동으로 수행하지 않고 자동 수행합니다.

## <a name="how-to"></a>방법

1. 다음 문자열 보간에 캐럿을 놓습니다.

2. 줄의 임의 위치에서 **Ctrl**+ **.** 를 눌러 **빠른 작업 및 리팩터링** 메뉴를 트리거합니다.

3. **보간 간소화** 선택

    ![문자열 보간 간소화](media/simplify-string-interpolation.png)

## <a name="see-also"></a>참조

- [리팩터링](../refactoring-in-visual-studio.md)