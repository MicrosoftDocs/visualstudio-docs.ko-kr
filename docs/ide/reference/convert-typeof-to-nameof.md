---
title: typeof를 nameof로 변환
description: Visual Studio의 빠른 작업 및 리팩터링 메뉴를 사용하여 typeof를 C#의 nameof로 변환하고 GetType을 Visual Basic의 NameOf로 변환하는 방법을 알아봅니다.
ms.date: 08/12/2020
ms.topic: reference
author: m-redding
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: ce76b82e2ebc68634be7cf4d463f6b8216d81e06
ms.sourcegitcommit: 3c571f44bfd6402efea5187af43df287bac5b6ac
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/24/2020
ms.locfileid: "97761201"
---
# <a name="convert-typeof-to-nameof"></a>`typeof`를 `nameof`로 변환

이 리팩터링은 다음에 적용됩니다.

- C#
- Visual Basic

**내용:** `typeof(<QualifiedType>).Name`의 인스턴스를 `nameof(<QualifiedType>)`(C#)로 변환하고 `GetType(<QualifiedType>).Name`의 인스턴스를 `NameOf(<QualifiedType>)`(Visual Basic)로 변환할 수 있습니다.

**시기:**  `someType`이 제네릭 형식이 아닌 모든 `typeof(<QualifiedType>).Name` 인스턴스. 이러한 제외가 필요한 것은 이 경우 `nameof(<QualifiedType>)`와 동일한 문자열 값을 반환하지 않기 때문입니다. Visual Basic 인스턴스의 경우에도 마찬가지입니다.

**이유:** `type`의 이름 대신 `nameof`를 사용하면 `type` 개체 검색과 관련된 리플렉션이 방지되며 보다 실용적인 방식으로 개체를 작성할 수 있습니다.

## <a name="how-to"></a>방법

1. `typeof(<QualifiedType>).Name` 인스턴스(C#) 또는 `GetType(<QualifiedType>).Name` 인스턴스(Visual Basic) 내에 커서를 놓습니다.

2. 줄의 임의 위치에서 **Ctrl**+ **.** 를 눌러 **빠른 작업 및 리팩터링** 메뉴를 트리거합니다.

3. 다음 옵션 중 하나를 선택합니다.

    - C#
      <br>**‘typeof’를 ‘nameof’로 변환** 을 선택합니다. ![‘typeof’를 ‘nameof’로 변환이 선택되고 C# 코드 변경 내용이 표시된 Visual Studio의 빠른 작업 및 리팩터링 메뉴 스크린샷](media/convert-type-of.PNG)

    - Visual Basic
      <br>**‘GetType’을 ‘NameOf’로 변환** 을 선택합니다. ![‘GetType’을 ‘NameOf’로 변환이 선택되고 Visual Basic 코드 변경 내용이 표시된 Visual Studio의 빠른 작업 및 리팩터링 메뉴 스크린샷](media/convert-get-type.PNG)

## <a name="see-also"></a>참조

- [리팩터링](../refactoring-in-visual-studio.md)
