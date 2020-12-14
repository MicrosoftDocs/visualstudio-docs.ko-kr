---
title: 구조체에 대한 IEquatable 연산자 생성
description: 빠른 작업 및 리팩터링 메뉴를 사용하여 구조체에 대한 Equals 및 IEquatable 연산자를 생성하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 05/12/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 28d70c0ea95c9373eb87e6199d53f1b43fadd508
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2020
ms.locfileid: "96617203"
---
# <a name="generate-iequatable-operators-when-generating-equals-for-structs"></a>구조체에 대한 Equals를 생성할 때 IEquatable 연산자를 생성합니다.

이 코드 생성은 다음에 적용됩니다.

- C#

**내용:** [구조체](/dotnet/csharp/language-reference/builtin-types/struct)에 대한 **Equals** 및 **IEquatable** 연산자를 생성할 수 있습니다.

**시기:** 구조체가 있으면 IEquatable뿐만 아니라 equals 및 not equals 연산자도 자동으로 추가됩니다.

**이유:**

- 값 형식을 구현하는 경우에는 ValueType에서 **Equals** 메서드의 기본 구현에 대한 성능을 향상시키기 위해 Equals 메서드를 재정의하는 것을 고려해야 합니다.

- IEquatable 구현 인터페이스는 형식 관련 Equals() 메서드를 구현합니다.

## <a name="how-to"></a>방법

1. 구조체 선언 줄 위에 커서를 놓습니다.

2. 다음 작업 중 하나를 수행합니다.

   - 줄의 임의 위치에서 **Ctrl**+ **.** 를 눌러 **빠른 작업 및 리팩터링** 메뉴를 트리거합니다.

   - 마우스 오른쪽 단추로 클릭하고 **빠른 작업 및 리팩터링** 메뉴를 선택합니다.

   - 텍스트 커서가 이미 구부러진 빨간 곡선이 있는 줄 위에 있으면 왼쪽 여백에 나타나는 ![스크루드라이버](../media/screwdriver-icon.png) 아이콘을 클릭합니다.

   ![구조체에 대한 IEquatable 및 Equals 생성](media/generate-equals-structs.png)

3. 드롭다운 메뉴에서 **Equals(object) 생성** 을 선택합니다.

## <a name="see-also"></a>참조

- [코드 생성](../code-generation-in-visual-studio.md)
- [변경 내용 미리 보기](../../ide/preview-changes.md)