---
title: 분할 또는 병합 if 문
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
ms.openlocfilehash: a3b42f83faacda6be34b282150cf4fb4c0f379f1
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79093684"
---
# <a name="split-or-merge-if-statements"></a>분할 또는 병합 if 문

이 리팩터링은 다음에 적용됩니다.

- C#

- Visual Basic

**내용:** **내용:** [if](/dotnet/csharp/language-reference/keywords/if-else) 문 분할 또는 병합

**시기:** `&&` 또는 `||` 연산자를 사용하는 `if` 문을 중첩된 `if` 문으로 분할하거나, `if` 문을 외부 `if` 문과 병합하려는 경우

**이유:** 선호하는 스타일과 관련된 리팩터링입니다.  

## <a name="how-to"></a>방법

`if` 문을 분할하려는 경우

1. `&&` 또는 `||` 연산자 옆의 `if` 문에 커서를 놓습니다.

2. 줄의 임의 위치에서 **Ctrl**+ **.** 를 눌러 **빠른 작업 및 리팩터링** 메뉴를 트리거합니다.

    ![If 문 분할](../media/split-if-statement.png)

3. **중첩된 if 문으로 분할**을 선택합니다.

    ![If 문 분할 완료](../media/split-if-statement-complete.png)

내부 `if` 문을 외부 `if` 문과 병합하려는 경우 

1. 내부 `if` 키워드에 커서를 놓습니다.

2. 줄의 임의 위치에서 **Ctrl**+ **.** 를 눌러 **빠른 작업 및 리팩터링** 메뉴를 트리거합니다.

    ![If 문 병합](../media/merge-if-statement.png)

3. **외부 if 문과 병합**을 선택합니다.

    ![If 문 병합 완료](../media/merge-if-statement-complete.png)

## <a name="see-also"></a>참조

- [리팩터링](../refactoring-in-visual-studio.md)