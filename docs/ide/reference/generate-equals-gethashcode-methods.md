---
title: C# Equals 및 GetHashCode 메서드 재정의 생성
description: 빠른 작업 및 리팩터링 메뉴를 사용하여 Equals 및 GetHashCode 메서드를 생성하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 03/08/2021
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 6a9d0ea6f6cb0aedc4fa13a8014b1a8bd66ccca0
ms.sourcegitcommit: 6ed6ae5a1693607dce57923a78d01eea3d88b29a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/09/2021
ms.locfileid: "102514960"
---
# <a name="generate-equals-and-gethashcode-method-overrides-in-visual-studio"></a>Visual Studio에서 Equals 및 GetHashCode 메서드 재정의 생성

이 코드 생성은 다음에 적용됩니다.

- C#

**대상:****Equals** 및 **GetHashCode** 메서드를 생성할 수 있습니다.

**시기:** 메모리의 개체 위치 대신 하나 이상의 필드에서 비교되어야 하는 형식이 있을 경우 이러한 재정의를 생성합니다.

**이유:**

- 값 형식을 구현하는 경우 **Equals** 메서드의 재정의를 고려해야 합니다. 이 경우 ValueType에서 Equals 메서드의 기본 구현에 대한 성능을 향상시킬 수 있습니다.

- 참조 형식을 구현하는 경우에는 형식이 Point, String, BigNumber 등의 기본 형식처럼 보일 경우에는 **Equals** 메서드를 재정의하는 것을 고려해야 합니다.

- 형식이 해시 테이블에서 올바르게 작동할 수 있도록 **GetHashCode** 메서드를 재정의합니다. 자세한 내용은 [같음 연산자](/dotnet/standard/design-guidelines/equality-operators)를 참조하세요.

## <a name="how-to"></a>방법

1. 형식 선언 줄 위에 커서를 놓습니다.

    ```csharp
    public class ImaginaryNumber
    {
        public double RealNumber { get; set; }
        public double ImaginaryUnit { get; set; }
    }
    ```

   코드가 다음 스크린샷과 유사하게 표시될 것입니다.

   ![생성된 메서드를 적용할 코드가 강조 표시된 스크린샷](media/overrides-highlight-cs.png)

   > [!TIP]
   > 형식 이름을 선택하려면 두 번 클릭하지 마세요. 그렇지 않으면 메뉴 옵션을 사용할 수 없습니다. 줄 위에 커서를 놓습니다.

1. 다음으로 작업 중 하나를 선택합니다.

   - 줄의 임의 위치에서 **Ctrl**+ **.** 를 눌러 **빠른 작업 및 리팩터링** 메뉴를 트리거합니다.

   - 마우스 오른쪽 단추로 클릭하고 **빠른 작업 및 리팩터링** 메뉴를 선택합니다.

   - 텍스트 커서가 이미 구부러진 빨간 곡선이 있는 줄 위에 있으면 왼쪽 여백에 나타나는 ![Visual Studio의 빠른 작업 스크루 드라이버 아이콘 스크린샷](../media/screwdriver-icon.png) 아이콘을 클릭합니다.

1. 드롭다운 메뉴에서 **Equals(개체) 생성** 또는 **Equals 및 GetHashCode 생성** 을 선택합니다.

   ![재정의 생성 드롭다운 메뉴의 스크린샷](media/overrides-preview-cs.png)

1. **멤버 선택** 대화 상자에서 메서드를 생성할 멤버를 선택합니다.

    ![재정의 생성 대화 상자](media/overrides-dialog-cs.png)

    > [!TIP]
    > 대화 상자 맨 아래 부근에 있는 확인란을 사용하여 이 대화 상자에서 연산자를 생성하도록 선택할 수도 있습니다.

   다음 코드에서 표시되는 것과 같이 기본 구현을 사용하여 `Equals` 및 `GetHashCode` 메서드가 생성됩니다.

    ```csharp
   public class ImaginaryNumber : IEquatable<ImaginaryNumber>
    {
        public double RealNumber { get; set; }
        public double ImaginaryUnit { get; set; }

        public override bool Equals(object obj)
        {
            return Equals(obj as ImaginaryNumber);
        }

        public bool Equals(ImaginaryNumber other)
        {
            return other != null &&
                   RealNumber == other.RealNumber &&
                   ImaginaryUnit == other.ImaginaryUnit;
        }

        public override int GetHashCode()
        {
            return HashCode.Combine(RealNumber, ImaginaryUnit);
        }
    }
    ```

   코드가 다음 스크린샷과 유사하게 표시될 것입니다.

   ![생성된 메서드의 결과 스크린샷](media/overrides-result-cs.png)

## <a name="see-also"></a>참조

- [코드 생성](../code-generation-in-visual-studio.md)
- [변경 내용 미리 보기](../../ide/preview-changes.md)
