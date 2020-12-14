---
title: 접근할 수 없는 리팩터링 제거
description: 빠른 작업 및 리팩터링 메뉴를 사용하여 실행되지 않는 코드를 제거하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 3af9d0a14b600773c5025fcaad68380c7bb82b29
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2020
ms.locfileid: "96616709"
---
# <a name="remove-unreachable-code-refactoring"></a>접근할 수 없는 리팩터링 제거

이 리팩터링은 다음에 적용됩니다.

- C#

- Visual Basic

**대상:** 실행되지 않는 코드를 제거합니다.

**시기:** 프로그램에 코드 조각 경로가 없어 코드 조각이 불필요합니다.

**이유:** 불필요하고 실행되지 않을 코드를 제거하여 가독성 및 유지 관리 편의성을 개선합니다.

## <a name="how-to"></a>방법

1. 접근할 수 없는 페이드 아웃된 코드의 아무 곳에나 커서를 놓습니다.

![페이드된 접근할 수 없는 코드](media/unreachablecode-faded-cs.png)

1. 다음 작업 중 하나를 수행합니다.

   - **키보드**
      - 줄의 임의 위치에서 **Ctrl**+ **.** 를 눌러 **빠른 작업 및 리팩터링** 메뉴를 트리거하고 [미리 보기] 창 팝업에서 **접근할 수 없는 코드 제거** 를 선택합니다.
   - **마우스**
      - 코드를 마우스 오른쪽 단추로 클릭하고, **빠른 작업 및 리팩터링** 메뉴를 선택하고, [미리 보기] 창 팝업에서 **접근할 수 없는 코드 제거** 를 선택합니다.

1. 변경 내용에 만족할 경우 **Enter** 키를 누르거나 메뉴에서 수정을 클릭하면 변경 내용이 커밋됩니다.

예:

```csharp
// Before
private void Method()
{
    throw new Exception(nameof(Method));
    Console.WriteLine($"Exception for method {nameof(Method)}");
}

// Remove unreachable code

// After
private void Method()
{
    throw new Exception(nameof(Method));
}
```

## <a name="see-also"></a>참고 항목

- [리팩터링](../refactoring-in-visual-studio.md)
- [변경 내용 미리 보기](../../ide/preview-changes.md)
