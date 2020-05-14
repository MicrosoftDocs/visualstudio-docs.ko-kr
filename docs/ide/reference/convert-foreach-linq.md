---
title: foreach 루프를 LINQ로 변환
descritpion: Convert any foreach loop that uses an IEnumerable to a LINQ query or a LINQ call form (also known as a LINQ method).
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
ms.openlocfilehash: 12c03830ccd37e0970e3c74bc78cdd9c8a8732b7
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094222"
---
# <a name="convert-a-foreach-loop-to-linq"></a>foreach 루프를 LINQ로 변환

이 리팩터링은 다음에 적용됩니다.

- C#

- Visual Basic

**내용:** IEnumerable을 사용하는 *foreach* 루프를 LINQ 쿼리 또는 LINQ 호출 양식(LINQ 메서드라고도 함)으로 쉽게 변환할 수 있습니다.

**시기:** IEnumerable을 사용하는 foreach 루프가 있고 이 루프를 LINQ 쿼리로 읽으려고 합니다.

**이유:** foreach 루프가 아닌 LINQ 구문을 사용하고 싶습니다. [LINQ](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq)를 사용하면 쿼리가 C#의 고급 언어 구문이 됩니다. LINQ는 파일의 코드양을 줄이고, 코드를 읽기 쉽게 하며, 다른 데이터 소스가 유사한 쿼리 식 패턴을 갖도록 할 수 있습니다.

> [!NOTE]
> LINQ 구문은 일반적으로 foreach 루프보다 효율이 떨어집니다. LINQ를 사용하면 코드의 가독성은 좋아지는 대신 성능이 떨어질 수 있다는 점을 알고 있는 것이 좋습니다.

## <a name="convert-a-foreach-loop-to-linq-refactoring"></a>foreach 루프를 LINQ 리팩터링으로 변환

1. 커서를 `foreach` 키워드에 놓습니다.

    ![IEnumerable을 사용한 Foreach 샘플](media/convert-foreach-to-LINQ.png)

2. 줄의 임의 위치에서 **Ctrl**+ **.** 를 눌러 **빠른 작업 및 리팩터링** 메뉴를 트리거합니다.

   ![LINQ 메뉴로 변환 샘플](media/convert-foreach-to-LINQ-codefix.png)

3. **LINQ로 변환** 또는 **Linq(호출 양식)로 변환**을 선택합니다.

   ![LINQ 쿼리 결과 샘플](media/convert-foreach-to-LINQ-result.png)

   ![LINQ 호출 양식 결과 샘플](media/convert-foreach-to-LINQ-callform-result.png)

### <a name="sample-code"></a>샘플 코드

```csharp
using System.Collections.Generic;

public class Class1
{
    public void MyMethod()
    {
        var greetings = new List<string>()
            { "hi", "yo", "hello", "howdy" };

        IEnumerable<string> enumerable()
        {
            foreach (var greet in greetings)
            {
                if (greet.Length < 3)
                {
                    yield return greet;
                }
            }

            yield break;
        }
    }
}
```

## <a name="see-also"></a>참조

- [리팩터링](../refactoring-in-visual-studio.md)
- [변경 내용 미리 보기 창](../../ide/preview-changes.md)
- [.NET 개발자를 위한 팁](../csharp-developer-productivity.md)
