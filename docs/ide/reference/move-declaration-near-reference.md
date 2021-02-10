---
title: 참조 근처로 변수 선언 이동
description: 빠른 작업 및 리팩터링 메뉴를 사용하여 변수 선언을 해당 사용에 더 가깝게 이동하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: ce731da61c0c119869c1c1b85a87ebe44fabf273
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99927927"
---
# <a name="move-declaration-near-reference-refactoring"></a>참조 리팩터링 근처로 선언 이동

이 리팩터링은 다음에 적용됩니다.

- C#

- Visual Basic

**대상:** 변수 선언을 해당 사용에 더 가깝게 이동할 수 있습니다.

**시기:** 범위를 좁힐 수 있는 변수 선언이 있습니다.

**이유:** 그대로 둘 수 있지만 가독성 문제가 발생하거나 정보가 숨겨질 수 있습니다. 이를 통해 가독성을 개선하기 위해 리팩터링 할 수 있습니다.

## <a name="how-to"></a>방법

1. 변수 선언에 커서를 놓습니다.

1. 다음 작업 중 하나를 수행합니다.

   - **키보드**
      - 줄의 임의 위치에서 **Ctrl**+ **.** 를 눌러 **빠른 작업 및 리팩터링** 메뉴를 트리거하고 [미리 보기] 창 팝업에서 **참조 근처로 선언 이동** 을 선택합니다.
   - **마우스**
      - 코드를 마우스 오른쪽 단추로 클릭하고, **빠른 작업 및 리팩터링** 메뉴를 선택하고, [미리 보기] 창 팝업에서 **참조 근처로 선언 이동** 을 선택합니다.

1. 변경 내용에 만족할 경우 **Enter** 키를 누르거나 메뉴에서 수정을 클릭하면 변경 내용이 커밋됩니다.

예:

```csharp
// Before
int x;
if (condition)
{
    x = 1;
    Console.WriteLine(x);
}

// Move declaration near reference

// After
if (condition)
{
    int x = 1;
    Console.WriteLine(x);
}
```

## <a name="see-also"></a>참고 항목

- [리팩터링](../refactoring-in-visual-studio.md)
- [변경 내용 미리 보기](../../ide/preview-changes.md)
