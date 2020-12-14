---
title: if 문 반전
description: 빠른 작업 및 리팩터링 메뉴를 사용하여 코드의 의미를 변경하지 않고 if 또는 if else 문을 반전하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 71b3a11e053b6a600d0b33db7c52a91c4950bf5b
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2020
ms.locfileid: "96616982"
---
# <a name="invert-if-statement"></a>if 문 반전

이 리팩터링은 다음에 적용됩니다.

- C#
- Visual Basic

**내용:** 코드의 의미를 변경하지 않고 `if` 또는 `if else` 문을 반전시킬 수 있습니다.

**시기:** 반전했을 때 더 잘 이해할 수 있는 `if` 또는 `if else` 문이 있는 경우

**이유:** `if` 또는 `if else` 문을 수동으로 반전하는 것은 더 오래 걸릴 수 있으며 오류가 발생할 수 있습니다. 이 코드 수정은 이 리팩터링을 자동으로 수행할 수 있도록 도와줍니다.

## <a name="invert-if-statement-refactoring"></a>if 문 리택터링 반전

1. `if` 또는 `if else` 문에 커서를 놓습니다.

    ![If else 반전](media/invert-if.png)

2. 줄의 임의 위치에서 **Ctrl**+**.** 를 눌러 **빠른 작업 및 리팩터링** 메뉴를 트리거합니다.

    ![if else 반전 코드 수정](media/invert-if-codefix.png)

3. **if 반전** 을 선택합니다.

    ![if else 결과 반전](media/invert-if-codefix-result.png)

## <a name="see-also"></a>참고 항목

- [리팩터링](../refactoring-in-visual-studio.md)
- [.NET 개발자를 위한 팁](../csharp-developer-productivity.md)
