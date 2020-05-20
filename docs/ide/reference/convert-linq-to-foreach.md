---
title: LINQ 쿼리를 foreach 문으로 변환하도록 코드 리팩터링
description: 쿼리 구문으로 작성된 모든 LINQ 쿼리를 foreach 문으로 변환합니다.
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
ms.openlocfilehash: 6e1b24cb8406ff29659eb79d1d9fa856db628b89
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094082"
---
# <a name="refactoring-to-convert-linq-to-a-foreach-statement"></a>LINQ를 foreach 문으로 변환하도록 리팩터링

이 리팩터링을 사용하여 [LINQ 쿼리 구문](/dotnet/csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq)을 [foreach](/dotnet/csharp/language-reference/keywords/foreach-in) 문으로 변환합니다.

이 리팩터링은 다음에 적용됩니다.

- C#

- Visual Basic

## <a name="how-to-use-it"></a>사용 방법

1. `from`으로 시작하는 전체 LINQ 쿼리를 선택합니다.

   > [!NOTE]
   > 이 리팩터링은 메서드 구문이 아니라 쿼리 구문으로 표시되는 LINQ 쿼리를 변환하는 데에만 사용할 수 있습니다.

1. 줄의 임의 위치에서 **Ctrl**+ **.** 를 눌러 또는 코드 파일의 여백에 있는 스크루드라이버 ![스크루드라이버 아이콘](../media/screwdriver-icon.png) 아이콘을 클릭합니다.

   ![LINQ를 foreach 빠른 작업 메뉴로 변환](media/convert-linq-to-foreach.png)

1. **'foreach'로 변환**을 선택합니다. 또는 **변경 사항 미리 보기**를 선택하여 [변경 사항 미리 보기](../../ide/preview-changes.md) 대화 상자를 연 다음, **적용**을 선택합니다.

> [!NOTE]
> C#의 경우 이러한 리팩터링에서 생성된 코드는 `foreach` 루프의 반복 변수에 대해 명시적 형식 또는 [var](/dotnet/csharp/language-reference/keywords/var)을 사용합니다. 생성된 코드가 명시적 또는 암시적 형식인지 여부는 범위에 있는 코드 스타일 설정에 따라 다릅니다. 이러한 특정 코드 스타일 설정은 **도구** > **옵션** > **텍스트 편집기** > **C#**  > **코드 스타일** > **일반** >  **\'var' 기본 설정** 아래 컴퓨터 수준 또는 [EditorConfig](../../ide/editorconfig-language-conventions.md#implicit-and-explicit-types) 파일의 솔루션 수준에서 구성됩니다. **옵션**에서 코드 스타일 설정을 변경하는 경우 변경 내용을 적용하려면 코드 파일을 다시 엽니다.

## <a name="see-also"></a>참고 항목

- [LINQ](/dotnet/standard/using-linq)
- [리팩터링](../refactoring-in-visual-studio.md)
- [변경 내용 미리 보기](../../ide/preview-changes.md)
