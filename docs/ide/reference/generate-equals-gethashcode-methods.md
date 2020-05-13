---
title: C# Equals 및 GetHashCode 메서드 재정의 생성
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: f9b1a639dd655f4f75b21555396866858b144010
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75569285"
---
# <a name="generate-equals-and-gethashcode-method-overrides-in-visual-studio"></a>Visual Studio에서 Equals 및 GetHashCode 메서드 재정의 생성

이 코드 생성은 다음에 적용됩니다.

- C#

**대상:** **Equals** 및 **GetHashCode** 메서드를 생성할 수 있습니다.

**시기:** 메모리의 개체 위치 대신 하나 이상의 필드에서 비교되어야 하는 형식이 있을 경우 이러한 재정의를 생성합니다.

**이유:**

- 값 형식을 구현하는 경우에는 ValueType에서 **Equals** 메서드의 기본 구현에 대한 성능을 향상시키기 위해 Equals 메서드를 재정의하는 것을 고려해야 합니다.

- 참조 형식을 구현하는 경우에는 형식이 Point, String, BigNumber 등의 기본 형식처럼 보일 경우에는 **Equals** 메서드를 재정의하는 것을 고려해야 합니다.

- 형식이 해시 테이블에서 올바르게 작동할 수 있도록 **GetHashCode** 메서드를 재정의합니다. 자세한 내용은 [같음 연산자](/dotnet/standard/design-guidelines/equality-operators)를 참조하세요.

## <a name="how-to"></a>방법

1. 형식 선언 줄 위에 커서를 놓습니다.

   ![강조 표시된 코드](media/overrides-highlight-cs.png)

   > [!TIP]
   > 형식 이름을 선택하려면 두 번 클릭하지 마세요. 그렇지 않으면 메뉴 옵션을 사용할 수 없습니다. 줄 위에 커서를 놓습니다.

1. 다음 작업 중 하나를 수행합니다.

   - 줄의 임의 위치에서 **Ctrl**+ **.** 를 눌러 **빠른 작업 및 리팩터링** 메뉴를 트리거합니다.

   - 마우스 오른쪽 단추로 클릭하고 **빠른 작업 및 리팩터링** 메뉴를 선택합니다.

   - 텍스트 커서가 이미 구부러진 빨간 곡선이 있는 줄 위에 있으면 왼쪽 여백에 나타나는 ![스크루드라이버](../media/screwdriver-icon.png) 아이콘을 클릭합니다.

   ![재정의 생성 미리 보기](media/overrides-preview-cs.png)

1. 드롭다운 메뉴에서 **Equals(개체) 생성** 또는 **Equals 및 GetHashCode 생성**을 선택합니다.

1. **멤버 선택** 대화 상자에서 메서드를 생성할 멤버를 선택합니다.

    ![재정의 생성 대화 상자](media/overrides-dialog-cs.png)

    > [!TIP]
    > 대화 상자 맨 아래 부근에 있는 확인란을 사용하여 이 대화 상자에서 연산자를 생성하도록 선택할 수도 있습니다.

   기본 구현을 사용하여 `Equals` 및 `GetHashCode` 메서드를 생성합니다.

   ![메서드 생성 결과](media/overrides-result-cs.png)

## <a name="see-also"></a>참고 항목

- [코드 생성](../code-generation-in-visual-studio.md)
- [변경 내용 미리 보기](../../ide/preview-changes.md)
