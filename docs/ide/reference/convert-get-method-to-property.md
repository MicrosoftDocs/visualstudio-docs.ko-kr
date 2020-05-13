---
title: Get 메서드를 속성으로 변환, 속성을 Get 메서드로 변환
ms.date: 03/10/2020
ms.topic: reference
ms.devlang: csharp
author: mikadumont
ms.author: midumont
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.convertmethodtoproperty
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: af507a8b437a20e3d4f4807d582abab6f9a12e27
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094206"
---
# <a name="convert-get-method-to-property--convert-property-to-get-method-refactorings"></a>Get 메서드를 속성으로 변환 / 속성을 Get 메서드로 변환 / 리팩터링

이러한 리팩터링은 다음에 적용됩니다.

- C#

- Visual Basic

## <a name="convert-get-method-to-property"></a>Get 메서드를 속성으로 변환

**대상:** Get 메서드를 속성(및 선택적으로 Set 메서드)으로 변환할 수 있습니다.

**시기:** 논리를 포함하지 않는 Get 메서드가 있습니다.

### <a name="how-to"></a>방법

1. Get 메서드 이름에 커서를 놓습니다.

1. 다음 작업 중 하나를 수행합니다.

   - **키보드**
      - 줄의 임의 위치에서 **Ctrl**+ **.** 를 눌러 **빠른 작업 및 리팩터링** 메뉴를 트리거하고 [미리 보기] 창 팝업에서 **메서드를 속성으로 대체**를 선택합니다.
   - **마우스**
      - 코드를 마우스 오른쪽 단추로 클릭하고, **빠른 작업 및 리팩터링** 메뉴를 선택하고, [미리 보기] 창 팝업에서 **메서드를 속성으로 대체**를 선택합니다.

1. (선택 사항) Set 메서드가 있는 경우 **Get 메서드 및 Set 메서드를 속성으로 대체**를 선택하여 이때 Set 메서드를 변환할 수도 있습니다.

1. 코드 미리 보기의 변경 내용에 만족할 경우 **Enter** 키를 누르거나 메뉴에서 수정을 클릭하면 변경 내용이 커밋됩니다.

예제:

```csharp
private int MyValue;

// Before
public int GetMyValue()
{
    return MyValue;
}

// Replace 'GetMyValue' with property

// After
public int MyValue
{
    get { return MyValue; }
}
```

## <a name="convert-property-to-get-method"></a>속성을 Get 메서드로 변환

**대상:** 속성을 Get 메서드로 변환할 수 있습니다.

**시기:** 값을 즉시 설정하고 가져오는 것 이외에 관련된 속성이 있습니다.

### <a name="how-to"></a>방법

1. Get 메서드 이름에 커서를 놓습니다.

1. 다음 작업 중 하나를 수행합니다.

   - **키보드**
      - 줄의 임의 위치에서 **Ctrl**+ **.** 를 눌러 **빠른 작업 및 리팩터링** 메뉴를 트리거하고 [미리 보기] 창 팝업에서 **속성을 메서드로 대체**를 선택합니다.
   - **마우스**
      - 코드를 마우스 오른쪽 단추로 클릭하고, **빠른 작업 및 리팩터링** 메뉴를 선택하고, [미리 보기] 창 팝업에서 **속성을 메서드로 대체**를 선택합니다.

1. 코드 미리 보기의 변경 내용에 만족할 경우 **Enter** 키를 누르거나 메뉴에서 수정을 클릭하면 변경 내용이 커밋됩니다.

## <a name="see-also"></a>참고 항목

- [리팩터링](../refactoring-in-visual-studio.md)
- [변경 내용 미리 보기](../../ide/preview-changes.md)
