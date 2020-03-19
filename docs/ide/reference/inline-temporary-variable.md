---
title: 임시 변수를 해당 값으로 바꾸기
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 8f0199436f5f9b1013a4c49cfb5909e760c73dcc
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75568869"
---
# <a name="inline-a-temporary-variable-refactoring"></a>임시 변수 인라인 리팩터링

이 리팩터링은 다음에 적용됩니다.

- C#

- Visual Basic

**대상:** 임시 변수를 제거하고 해당 값으로 바꿀 수 있습니다.

**시기:** 임시 변수를 사용하면 코드를 이해하기가 더 어렵습니다.

**이유:** 임시 변수를 제거하면 코드를 더 쉽게 읽을 수 있습니다.

## <a name="how-to"></a>방법

1. 인라인할 임시 변수를 강조 표시하거나 임시 변수 내부에 텍스트 커서를 놓습니다.

   - C#:

       ![강조 표시된 코드 - C#](media/inline-highlight-cs.png)

   - Visual Basic:

       ![강조 표시된 코드 - Visual Basic](media/inline-highlight-vb.png)

2. 다음 작업 중 하나를 수행합니다.

   - **키보드**
      - 줄의 임의 위치에서 **Ctrl**+ **.** 를 눌러 **빠른 작업 및 리팩터링** 메뉴를 트리거합니다.
   - **마우스**
      - 코드를 마우스 오른쪽 단추로 클릭하고 **빠른 작업 및 리팩터링** 메뉴를 선택합니다.

3. [미리 보기] 창 팝업에서 **인라인 임시 변수**를 선택합니다.

   변수가 제거되고 해당 사용이 변수 값으로 대체됩니다.

   - C#:

      ![인라인 결과 - C#](media/inline-result-cs.png)

   - Visual Basic:

      ![인라인 결과 - Visual Basic](media/inline-result-vb.png)

## <a name="see-also"></a>참고 항목

- [리팩터링](../refactoring-in-visual-studio.md)
