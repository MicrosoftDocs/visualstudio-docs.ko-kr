---
title: 메서드 추출
description: 코드를 선택하고 Ctrl+R, Ctrl+M을 입력하여 코드 조각을 자체 메서드로 전환합니다.
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jmartens
f1_keywords:
- vs.csharp.refactoring.extractmethod
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: b39112a696611103828d862c7f7adf04784e6222
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860999"
---
# <a name="extract-a-method-refactoring"></a>메서드 추출 리팩터링

이 리팩터링은 다음에 적용됩니다.

- C#

- Visual Basic

**대상:** 코드 조각을 고유한 메서드로 변환할 수 있습니다.

**시기:** 다른 메서드에서 호출해야 하는 일부 메서드에 기존 코드 조각이 있습니다.

**이유:** 해당 코드를 복사하여 붙여넣을 수 있지만 중복이 발생합니다. 더 나은 솔루션은 다른 메서드에서 자유롭게 호출할 수 있는 고유한 메서드로 해당 조각을 리팩터링하는 것입니다.

## <a name="how-to"></a>방법

1. 추출할 코드를 강조 표시합니다.

   - C#:

       !Program 클래스의 C# 코드를 보여 주는 스크린샷 해당 클래스의 Main 함수에서 코드 줄이 강조 표시됩니다.](media/extractmethod-highlight-cs.png)

   - Visual Basic:

       ![Main Sub의 Visual Basic 코드를 보여 주는 스크린샷 해당 Sub에서 코드 줄이 강조 표시됩니다.](media/extractmethod-highlight-vb.png)

2. 다음 작업 중 하나를 수행합니다.

   - **키보드**
      - **Ctrl+R** 을 누른 다음 **Ctrl+M** 을 누릅니다. 바로 가기 키는 선택한 프로필에 따라 다를 수 있습니다.
      - 줄의 임의 위치에서 **Ctrl**+ **.** 를 눌러 **빠른 작업 및 리팩터링** 메뉴를 트리거하고 [미리 보기] 창 팝업에서 **메서드 추출** 을 선택합니다.
   - **마우스**
      - **편집 > 리팩터링 > 메서드 추출** 을 선택합니다.
      - 코드를 마우스 오른쪽 단추로 클릭하고 **리팩터링 > 추출 > 메서드 추출** 을 선택합니다.
      - 코드를 마우스 오른쪽 단추로 클릭하고, **빠른 작업 및 리팩터링** 메뉴를 선택하고, [미리 보기] 창 팝업에서 **메서드 추출** 을 선택합니다.

   메서드가 즉시 만들어집니다. 이제 여기에서 새 이름을 입력하여 간단히 메서드 이름을 바꿀 수 있습니다.

   > [!TIP]
   > 또한 이 새 이름을 사용하도록 주석과 기타 문자열을 업데이트할 뿐 아니라, IDE의 오른쪽 위에 표시되는 **이름 바꾸기** 상자의 확인란을 사용하여 저장하기 전에 [변경 내용을 미리 볼](../../ide/preview-changes.md) 수 있습니다.

   - C#:

      ![Program 클래스의 C# 코드를 보여 주는 스크린샷 메서드 이름이 강조 표시되고 이름 바꾸기 팝업 창이 열립니다.](media/extractmethod-rename-cs.png)

   - Visual Basic:

      ![Main Sub의 Visual Basic 코드를 보여 주는 스크린샷 메서드 이름이 강조 표시되고 이름 바꾸기 팝업 창이 열립니다.](media/extractmethod-rename-vb.png)

3. 변경 내용에 만족할 경우 **적용** 단추를 선택하거나 **Enter** 키를 누르면 변경 내용이 커밋됩니다.

## <a name="see-also"></a>참고 항목

- [리팩터링](../refactoring-in-visual-studio.md)
- [변경 내용 미리 보기](../../ide/preview-changes.md)
