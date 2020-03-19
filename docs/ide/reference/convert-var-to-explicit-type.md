---
title: var을 명시적 형식으로 바꾸도록 코드 리팩터링
ms.date: 05/15/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 4ec388564e1851402f085f6bbaefba08dbea212c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595776"
---
# <a name="refactoring-to-replace-var-with-an-explicit-type"></a>var을 명시적 형식으로 바꾸도록 리팩터링

이 리팩터링을 사용하여 지역 변수 선언의 [var](/dotnet/csharp/language-reference/keywords/var)을 명시적 형식으로 바꿉니다.

이 리팩터링은 다음에 적용됩니다.

- C#

## <a name="why-to-use-an-explicit-type"></a>명시적 형식을 사용하는 이유

다음은 명시적 형식으로 변수를 선언하는 몇 가지 이유입니다.

- 코드의 가독성을 향상합니다.

- 선언에서 변수를 초기화하지 않아도 됩니다.

그러나 변수가 무명 형식으로 초기화되고 개체의 속성이 나중에 액세스될 경우에는 [var](/dotnet/csharp/language-reference/keywords/var)을 사용해야 합니다. 자세한 내용은 [암시적 형식 지역 변수(C#)](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables)를 참조하세요.

## <a name="how-to-use-it"></a>사용 방법

1. `var` 키워드에 캐럿을 배치합니다.

1. 줄의 임의 위치에서 **Ctrl**+ **.** 를 눌러 또는 코드 파일의 여백에 있는 스크루드라이버 ![스크루드라이버 아이콘](../media/screwdriver-icon.png) 아이콘을 클릭합니다.

   ![명시적 형식 빠른 작업 메뉴 사용](media/use-explicit-type.png)

1. **명시적 형식 사용**을 선택합니다. 또는 **변경 사항 미리 보기**를 선택하여 [변경 사항 미리 보기](../../ide/preview-changes.md) 대화 상자를 연 다음, **적용**을 선택합니다.

## <a name="see-also"></a>참고 항목

- [암시적 형식 변수(C#)](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables)
- [리팩터링](../refactoring-in-visual-studio.md)
- [변경 내용 미리 보기](../../ide/preview-changes.md)
