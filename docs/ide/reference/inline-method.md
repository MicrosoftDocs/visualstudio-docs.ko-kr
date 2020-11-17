---
title: 인라인 메서드
ms.date: 11/03/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 0cc619ea61a7fd4d7f4bc542b946e298933a8f73
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93403537"
---
# <a name="inline-method"></a>인라인 메서드

이 리팩터링은 다음에 적용됩니다.

- C#

- Visual Basic

**내용:** 인라인 메서드 리팩터링입니다. 

**시기:** 단일 문 본문 내의 정적, 인스턴스 및 확장 메서드 사용을 원래 메서드 선언을 제거하는 옵션으로 바꾸려고 합니다.

**이유:**  이 리팩터링은 보다 명확한 구문을 제공합니다.

## <a name="how-to"></a>방법

1. 메서드 사용에 캐럿을 배치합니다.

2. 줄의 임의 위치에서 **Ctrl**+ **.** 를 눌러 **빠른 작업 및 리팩터링** 메뉴를 트리거합니다.

3. 다음 옵션 중 하나를 선택합니다. 
    
   인라인 메서드 선언을 제거하려면 **Inline `<QualifiedMethodName>`** (`<QualifiedMethodName>` 인라인)을 선택합니다. 

    ![클래스를 추상으로 설정](media/inline-method-remove-declaration.png)

   원래 메서드 선언을 유지하려면 **Inline and keep `<QualifiedMethodName>`** (`<QualifiedMethodName>` 인라인 및 유지)을 선택합니다. 

    ![클래스를 추상으로 설정](media/inline-method-preserve-declaration.png)

## <a name="see-also"></a>참조

- [리팩터링](../refactoring-in-visual-studio.md)
