---
title: 메서드 시그니처 변경
description: 메서드 매개 변수의 순서를 제거하거나 변경합니다. 메서드를 마우스 오른쪽 단추로 클릭하고 빠른 작업 및 리팩터링를 선택한 다음 시그니처 변경을 선택합니다.
ms.date: 01/26/2018
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.remove
- vs.csharp.refactoring.reorder
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 97c03c798732b5d722b2dc49f3ec7ffa490b4f06
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "68711257"
---
# <a name="change-a-method-signature-refactoring"></a>메서드 시그니처 변경 리팩터링

이 리팩터링은 다음에 적용됩니다.

- C#

- Visual Basic

**대상:** 메서드 매개 변수의 순서를 제거하거나 변경할 수 있습니다.

**시기:** 다양한 위치에서 현재 사용 중인 메서드 매개 변수를 이동하거나 제거하려고 합니다.

**이유:** 매개 변수를 수동으로 제거하고 다시 정렬한 후 해당 메서드에 대한 모든 호출을 찾아 하나씩 변경할 수 있지만 오류가 발생할 수 있습니다.  이 리팩터링 도구는 작업을 자동으로 수행합니다.

## <a name="how-to"></a>방법

1. 수정할 메서드 또는 해당 사용 중 하나의 이름을 강조 표시하거나 메서드 이름 내부에 텍스트 커서를 놓습니다.

   - C#:

       ![강조 표시된 코드 C#](media/changesignature-highlight-cs.png)

   - VB:

       ![강조 표시된 코드 Visual Basic](media/changesignature-highlight-vb.png)

2. 다음 작업 중 하나를 수행합니다.

   - **키보드**
      - **Ctrl+R**을 누른 다음 **Ctrl+V**를 누릅니다.  바로 가기 키는 선택한 프로필에 따라 다를 수 있습니다.
      - 줄의 임의 위치에서 **Ctrl**+ **.** 를 눌러 **빠른 작업 및 리팩터링** 메뉴를 트리거하고 [미리 보기] 창 팝업에서 **시그니처 변경**을 선택합니다.
   - **마우스**
      - **편집 > 리팩터링 > 매개 변수 제거**를 선택합니다.
      - **편집 > 리팩터링 > 매개 변수 다시 정렬**을 선택합니다.
      - 코드를 마우스 오른쪽 단추로 클릭하고, **빠른 작업 및 리팩터링** 메뉴를 선택하고, [미리 보기] 창 팝업에서 **시그니처 변경**을 선택합니다.

3. 표시되는 **시그니처 변경** 대화 상자에서 오른쪽 단추를 사용하여 메서드 시그니처를 변경할 수 있습니다.

   ![시그니처 변경 대화 상자](media/changesignature-dialog-cs.png)

   | 단추 | Description
   | ------ | ---
   | **위쪽/아래쪽** | 선택한 매개 변수를 목록에서 위아래로 이동합니다.
   | **제거** | 목록에서 선택한 매개 변수를 제거합니다.
   | **복원** | 선택한 취소선이 그어진 매개 변수를 목록으로 복원합니다.

   > [!TIP]
   > **참조 변경 내용 미리 보기** 확인란을 사용하여 커밋하기 전에 [결과를 확인](../../ide/preview-changes.md)합니다.

4. 완료되면 **확인** 단추를 눌러 변경합니다.

   - C#:

      ![시그니처 변경 결과 - C#](media/changesignature-result-cs.png)

   - Visual Basic:

      ![시그니처 변경 결과 - Visual Basic](media/changesignature-result-vb.png)

## <a name="see-also"></a>참고 항목

- [리팩터링](../refactoring-in-visual-studio.md)
- [변경 내용 미리 보기](../../ide/preview-changes.md)