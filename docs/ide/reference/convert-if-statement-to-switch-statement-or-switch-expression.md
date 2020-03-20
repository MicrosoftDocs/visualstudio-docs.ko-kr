---
title: If 문을 switch 문 또는 switch 식으로 변환
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 93ad96809c77d5644b13e6221a41f0b182fb448f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094129"
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
3. 다음 두 옵션 중에서 선택합니다. 

    **‘switch’ 문으로 변환**을 선택합니다.

   ![if 문을 switch 문으로 변환](media/convert-if-to-switch-statement.png) 

    **'switch' 식으로 변환**을 선택합니다. 

    ![if 문을 switch 식으로 변환](media/convert-if-to-switch-expression.png) 

## <a name="see-also"></a>참조

- [리팩터링](../refactoring-in-visual-studio.md)
