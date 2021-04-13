---
title: 패턴 일치 사용
description: C# 패턴 일치를 사용하는 방법을 알아봅니다.
ms.date: 11/03/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: f8ae039144d0c66f362b88cbbace142ccff77281
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/02/2021
ms.locfileid: "106217985"
---
# <a name="use-pattern-matching"></a>패턴 일치 사용

이 리팩터링은 다음에 적용됩니다.

- C#

**내용:** 패턴 일치를 사용합니다.

**시기:** 새로운 [C# 패턴 일치](https://docs.microsoft.com/dotnet/csharp/whats-new/csharp-9#pattern-matching-enhancements) 기능을 사용하려고 합니다.

**이유:** 이 리팩터링은 코드를 더욱 명확하고 간결하게 만듭니다.

## <a name="how-to"></a>방법

1. 문 내에 캐럿을 배치합니다.

2. 줄의 임의 위치에서 **Ctrl**+ **.** 를 눌러 **빠른 작업 및 리팩터링** 메뉴를 트리거합니다.

3. ‘패턴 일치 사용’을 선택합니다.

    ![클래스를 추상으로 설정](media/use-pattern-matching-not-syntax.png)

## <a name="see-also"></a>참조

- [리팩터링](../refactoring-in-visual-studio.md)
