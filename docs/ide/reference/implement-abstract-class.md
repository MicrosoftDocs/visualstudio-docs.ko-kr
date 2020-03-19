---
title: 추상 클래스 구현
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 6fcfdc06a055df28159f9d1ddc440aaf113f3264
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75568908"
---
# <a name="implement-an-abstract-class-in-visual-studio"></a>Visual Studio에서 추상 클래스 구현

이 코드 생성은 다음에 적용됩니다.

- C#

- Visual Basic

**대상:** 추상 클래스를 구현하는 데 필요한 코드를 즉시 생성할 수 있습니다.

**시기:** 추상 클래스에서 상속하려고 합니다.

**이유:** 모든 추상 멤버를 하나씩 수동으로 구현할 수 있지만 이 기능은 모든 메서드 시그니처를 자동으로 생성합니다.

## <a name="how-to"></a>방법

1. 추상 클래스에서 상속되었지만 일부 필요한 멤버를 구현하지 않았음을 나타내는 빨간색 구부러진 곡선이 있는 줄에 커서를 놓습니다.

   - C#:

       ![강조 표시된 코드 C#](media/abstract-highlight-cs.png)

   - Visual Basic:

       ![강조 표시된 코드 VB](media/abstract-highlight-vb.png)

2. 다음 작업 중 하나를 수행합니다.

   - **키보드**
      - 줄의 임의 위치에서 **Ctrl**+ **.** 를 눌러 **빠른 작업 및 리팩터링** 메뉴를 트리거합니다.
   - **마우스**
      - 마우스 오른쪽 단추로 클릭하고 **빠른 작업 및 리팩터링** 메뉴를 선택합니다.
      - 빨간색 구부러진 곡선 위로 마우스를 이동하고 표시되는 ![오류 전구](media/error-bulb.png) 아이콘을 클릭합니다.
      - 텍스트 커서가 이미 구부러진 빨간 곡선이 있는 줄 위에 있으면 왼쪽 여백에 나타나는 ![오류 전구](media/error-bulb.png) 아이콘을 클릭합니다.

   ![클래스 구현 미리 보기](media/abstract-preview-cs.png)

3. 드롭다운 메뉴에서 **추상 클래스 구현**을 선택합니다.

   > [!TIP]
   > - 미리 보기 창 맨 아래에 있는 **변경 내용 미리 보기** 링크를 사용하여 선택하기 전에 적용될 [모든 변경 내용을 확인](../../ide/preview-changes.md)합니다.
   > - 미리 보기 창의 맨 아래에 있는 **문서**, **프로젝트** 및 **솔루션** 링크를 사용하여 추상 클래스에서 상속되는 여러 클래스에서 적절한 메서드 시그니처를 만듭니다.

   추상 메서드 시그니처가 만들어지고 구현할 준비가 됩니다.

   - C#:

       ![클래스 구현 결과 C#](media/abstract-result-cs.png)

   - Visual Basic:

       ![클래스 구현 결과 VB](media/abstract-result-vb.png)

## <a name="see-also"></a>참고 항목

- [코드 생성](../code-generation-in-visual-studio.md)
- [변경 내용 미리 보기](../../ide/preview-changes.md)
