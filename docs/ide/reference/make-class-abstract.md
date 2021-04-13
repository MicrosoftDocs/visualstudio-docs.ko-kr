---
title: 클래스를 추상으로 설정
description: 추상 메서드를 작성한 후 클래스를 추상으로 만드는 방법을 알아봅니다.
ms.date: 11/03/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: ac3d6b9cef8d20d85049da830dfb830321faab75
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/02/2021
ms.locfileid: "106214540"
---
# <a name="make-class-abstract"></a>클래스를 추상으로 설정

이 리팩터링은 다음에 적용됩니다.

- C#

- Visual Basic

**내용:** 클래스를 추상으로 설정 리팩터링입니다.

**시기:** 추상이 아닌 클래스에서 추상 메서드를 작성합니다.

**이유:**  추상 메서드를 작성한 후 클래스를 추상으로 지정하도록 코드를 수정하면 시간이 절약됩니다.

## <a name="how-to"></a>방법

1. 추상 메서드에 캐럿을 배치합니다.

2. 줄의 임의 위치에서 **Ctrl**+ **.** 를 눌러 **빠른 작업 및 리팩터링** 메뉴를 트리거합니다.

3. **클래스를 ‘추상’으로 지정** 을 선택합니다.

    ![클래스를 추상으로 설정](media/make-class-abstract.png)

## <a name="see-also"></a>참조

- [리팩터링](../refactoring-in-visual-studio.md)
