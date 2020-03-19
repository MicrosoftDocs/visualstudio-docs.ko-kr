---
title: for 루프를 foreach 문으로 변환하는 코드 리팩터링
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
ms.openlocfilehash: af52761f5cb199c7f842d01589c35501898b09aa
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094600"
---
# <a name="refactoring-to-convert-between-a-for-loop-and-a-foreach-statement"></a>for 루프와 foreach 문 사이를 변환하는 리팩터링

이 문서에서는 두 개의 루프 구조 간에 변환되는 빠른 작업 리팩터링에 대해 설명합니다. 코드에는 [for](/dotnet/csharp/language-reference/keywords/for) 루프와 [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) 문 간에 전환할 수 있는 몇 가지 이유가 포함됩니다.

## <a name="convert-a-for-loop-to-a-foreach-statement"></a>for 루프를 foreach 문으로 변환

코드에 [for](/dotnet/csharp/language-reference/keywords/for) 루프가 있는 경우 이 리팩토링을 사용하여 [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) 문으로 변환할 수 있습니다.

이 리팩터링은 다음에 적용됩니다.

- C#

- Visual Basic

> [!NOTE]
> **foreach로 변환** 빠른 작업 리팩터링은 세 가지 파트인 이니셜라이저, 조건 및 반복기가 모두 포함된 [for](/dotnet/csharp/language-reference/keywords/for) 루프에만 사용할 수 있습니다.

### <a name="why-convert"></a>변환 이유

[for](/dotnet/csharp/language-reference/keywords/for) 루프를 [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) 문으로 변환하려는 이유는 다음과 같습니다.

- 항목에 액세스하기 위한 인덱스로 사용하는 경우를 제외하고는 루프 내에서 지역 루프 변수를 사용하지 않습니다.

- 코드를 단순화하고 이니셜라이저, 조건 및 반복기 섹션에서 논리 오류의 가능성을 줄이려 합니다.

### <a name="how-to-use-it"></a>사용 방법

1. `for` 키워드에 캐럿을 배치합니다.

1. 줄의 임의 위치에서 **Ctrl**+ **.** 를 눌러 또는 코드 파일의 여백에 있는 스크루드라이버![스크루드라이버 아이콘](../media/screwdriver-icon.png) 아이콘을 클릭합니다.

   ![foreach로 변환 메뉴](media/convert-to-foreach.png)

1. **'foreach'로 변환**을 선택합니다. 또는 **변경 사항 미리 보기**를 선택하여 [변경 사항 미리 보기](../../ide/preview-changes.md) 대화 상자를 연 다음, **적용**을 선택합니다.

## <a name="convert-a-foreach-statement-to-a-for-loop"></a>foreach 문을 for 루프로 변환

코드에 [foreach(C#)](/dotnet/csharp/language-reference/keywords/foreach-in) 또는 [For Each...Next(Visual Basic)](/dotnet/visual-basic/language-reference/statements/for-each-next-statement) 문이 있는 경우 이 리팩터링을 사용하여 [for](/dotnet/csharp/language-reference/keywords/for) 루프로 변환할 수 있습니다.

이 리팩터링은 다음에 적용됩니다.

- C#

- Visual Basic

### <a name="why-convert"></a>변환 이유

[foreach](/dotnet/csharp/language-reference/keywords/foreach-in) 문을 [for](/dotnet/csharp/language-reference/keywords/for) 루프로 변환하려는 이유는 다음과 같습니다.

- 항목에 단순히 액세스하는 것보다 루프 내에서 지역 루프 변수를 사용하고자 합니다.

- [다차원 배열을 반복](/dotnet/csharp/programming-guide/arrays/using-foreach-with-arrays)하여 배열 요소에 대한 더 많은 제어권을 가지려 합니다.

### <a name="how-to-use-it"></a>사용 방법

1. `foreach` 또는 `For Each` 키워드에 캐럿을 배치합니다.

1. 줄의 임의 위치에서 **Ctrl**+ **.** 를 눌러 또는 코드 파일의 여백에 있는 스크루드라이버![스크루드라이버 아이콘](../media/screwdriver-icon.png) 아이콘을 클릭합니다.

   ![for로 변환 메뉴](media/convert-to-for.png)

1. **'for'로 변환**을 선택합니다. 또는 **변경 사항 미리 보기**를 선택하여 [변경 사항 미리 보기](../../ide/preview-changes.md) 대화 상자를 연 다음, **적용**을 선택합니다.

1. 리팩터링이 새로운 반복 횟수 변수를 도입하기 때문에 **이름 바꾸기** 상자가 편집기의 오른쪽 상단에 나타납니다. 변수에 다른 이름을 선택하려면 여기에 입력한 다음, **Enter**를 누르거나 **이름 바꾸기** 상자에서 **적용**을 선택합니다. 새 이름을 선택하지 않으려면 **Esc**를 누르거나 **적용**을 선택하여 **이름 바꾸기** 상자를 닫습니다.

> [!NOTE]
> C#의 경우 이러한 리팩터링에서 생성된 코드는 컬렉션의 항목 형식에 대해 명시적 형식 또는 [var](/dotnet/csharp/language-reference/keywords/var)을 사용합니다. 생성된 코드가 명시적 또는 암시적 형식인지 여부는 범위에 있는 코드 스타일 설정에 따라 다릅니다. 이러한 특정 코드 스타일 설정은 **도구** > **옵션** > **텍스트 편집기** > **C#**  > **코드 스타일** > **일반** >  **\'var' 기본 설정** 아래 컴퓨터 수준 또는 [EditorConfig](../../ide/editorconfig-language-conventions.md#implicit-and-explicit-types) 파일의 솔루션 수준에서 구성됩니다. **옵션**에서 코드 스타일 설정을 변경하는 경우 변경 내용을 적용하려면 코드 파일을 다시 엽니다.

## <a name="see-also"></a>참고 항목

- [리팩터링](../refactoring-in-visual-studio.md)
- [변경 내용 미리 보기](../../ide/preview-changes.md)
