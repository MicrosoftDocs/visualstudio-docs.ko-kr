---
title: If 문을 switch 문 또는 switch 식으로 변환
ms.date: 02/12/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: cb0c06fe0493f973ea9cf0a566ffda45a49eeeff
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/15/2020
ms.locfileid: "77283462"
---
# <a name="convert-if-statement-to-switch-statement-or-switch-expression"></a>If 문을 switch 문 또는 switch 식으로 변환

이 리팩터링은 다음에 적용됩니다.

- C#

**내용:** if 문을 [switch 문](/dotnet/csharp/language-reference/keywords/switch) 또는 C# 8.0 [switch 식](/dotnet/csharp/whats-new/csharp-8#switch-expressions)으로 변환합니다.

**시기:** `if` 문을 `switch` 문 또는`switch` 식으로 변환하거나 그 반대로 변환하려는 경우입니다. 

**이유:** `if` 문을 사용하는 경우 이 리팩터링을 통해 `switch` 문이나 `switch` 식으로 쉽게 전환할 수 있습니다.

## <a name="how-to"></a>방법

1. 커서를 `if` 키워드에 놓습니다.
2. 줄의 임의 위치에서 **Ctrl**+ **.** 를 눌러 **빠른 작업 및 리팩터링** 메뉴를 트리거합니다.
3. **‘switch’ 문으로 변환**을 선택합니다.

   ![If 문을 switch 문 또는 switch 식으로 변환](media/convert-if-statement-to-switch-statement-or-switch-expression.png) 

## <a name="see-also"></a>참조

- [리팩터링](../refactoring-in-visual-studio.md)
