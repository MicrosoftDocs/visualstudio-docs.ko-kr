---
title: 인터페이스 구현
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 7d420bd0d42e89476696966f7eda94a19893fc23
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595555"
---
# <a name="implement-an-interface-in-visual-studio"></a>Visual Studio에서 인터페이스 구현

이 코드 생성은 다음에 적용됩니다.

- C#

- Visual Basic

**대상:** 인터페이스를 구현하는 데 필요한 코드를 즉시 생성할 수 있습니다.

**시기:** 인터페이스에서 상속하려고 합니다.

**이유:** 모든 인터페이스를 하나씩 수동으로 구현할 수 있지만 이 기능은 모든 메서드 시그니처를 자동으로 생성합니다.

## <a name="how-to"></a>방법

1. 인터페이스를 참조했지만 일부 필요한 멤버를 구현하지 않았음을 나타내는 빨간색 구부러진 곡선이 있는 줄에 커서를 놓습니다.

   - C#:

       ![강조 표시된 코드 C#](media/interface-highlight-cs.png)

   - Visual Basic:

       ![강조 표시된 코드 VB](media/interface-highlight-vb.png)

2. 다음 작업 중 하나를 수행합니다.

   - **키보드**
      - 줄의 임의 위치에서 **Ctrl**+ **.** 를 눌러 **빠른 작업 및 리팩터링** 메뉴를 트리거합니다.
   - **마우스**
      - 마우스 오른쪽 단추로 클릭하고 **빠른 작업 및 리팩터링** 메뉴를 선택합니다.
      - 빨간색 구부러진 곡선 위로 마우스를 이동하고 표시되는 ![오류 전구](media/error-bulb.png) 아이콘을 클릭합니다.
      - 텍스트 커서가 이미 구부러진 빨간 곡선이 있는 줄 위에 있으면 왼쪽 여백에 나타나는 ![오류 전구](media/error-bulb.png) 아이콘을 클릭합니다.

3. 드롭다운 메뉴에서 **인터페이스 구현**을 선택합니다.

   ![인터페이스 구현 미리 보기](media/interface-preview-cs.png)

   > [!TIP]
   > - 미리 보기 창 맨 아래에 있는 **변경 내용 미리 보기** 링크를 사용하여 선택하기 전에 적용될 [모든 변경 내용을 확인](../../ide/preview-changes.md)합니다.
   > - 미리 보기 창의 맨 아래에 있는 **문서**, **프로젝트** 및 **솔루션** 링크를 사용하여 인터페이스를 구현하는 여러 클래스에서 적절한 메서드 시그니처를 만듭니다.

   인터페이스의 메서드 시그니처가 만들어지고 구현할 준비가 됩니다.

   - C#:

       ![인터페이스 구현 결과 C#](media/interface-result-cs.png)

   - Visual Basic:

       ![인터페이스 구현 결과 VB](media/interface-result-vb.png)

   > [!TIP]
   > (C#만 해당) 이름 충돌을 방지하려면 **명시적으로 인터페이스 구현** 옵션을 사용하여 생성된 각 메서드 앞에 인터페이스 이름을 추가합니다.
   >
   > ![명시적으로 인터페이스 구현 결과](media/interface-explicitresult-cs.png);

## <a name="see-also"></a>참고 항목

- [코드 생성](../code-generation-in-visual-studio.md)
- [변경 내용 미리 보기](../../ide/preview-changes.md)
