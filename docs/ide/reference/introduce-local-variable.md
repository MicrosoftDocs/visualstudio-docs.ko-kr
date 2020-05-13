---
title: 지역 변수 소개
description: 기존 식을 대체할 지역 변수를 생성합니다. 식을 선택하고 마우스 오른쪽 단추를 클릭한 다음 빠른 작업 및 리팩터링 메뉴를 선택하고 ‘expression’의 모든 항목에 대한 로컬 지정을 선택합니다.
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 0fbd5ed752b28cc3f8c0dd734ed2b3ce09e80b78
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75568817"
---
# <a name="introduce-a-local-variable-in-visual-studio"></a>Visual Studio에서 지역 변수 소개

이 코드 생성은 다음에 적용됩니다.

- C#

- Visual Basic

**대상:** 기존 식을 대체할 지역 변수를 즉시 생성할 수 있습니다.

**시기:** 지역 변수에 있는 경우 나중에 쉽게 다시 사용할 수 있는 코드가 있습니다.

**이유:** 코드를 여러 번 복사하여 붙여넣으면 다양한 위치에서 사용할 수 있지만, 작업을 한 번 수행하고 지역 변수에 결과를 저장한 다음, 전체적으로 지역 변수를 사용하는 것이 좋습니다.

## <a name="how-to"></a>방법

1. 새 지역 변수에 할당할 식을 강조 표시합니다.

   - C#:

       ![강조 표시된 코드 C#](media/local-highlight-cs.png)

   - Visual Basic:

       ![강조 표시된 코드 VB](media/local-highlight-vb.png)

2. 다음 작업 중 하나를 수행합니다.

   - **키보드**
      - 줄의 임의 위치에서 **Ctrl**+ **.** 를 눌러 **빠른 작업 및 리팩터링** 메뉴를 트리거합니다.
   - **마우스**
      - 마우스 오른쪽 단추로 클릭하고 **빠른 작업 및 리팩터링** 메뉴를 선택합니다.
      - 텍스트 커서가 이미 구부러진 빨간 곡선이 있는 줄 위에 있으면 왼쪽 여백에 나타나는 ![스크루드라이버](media/screwdriver.png) 아이콘을 클릭합니다.

   ![로컬 미리 보기 소개](media/local-preview-cs.png)

3. 드롭다운 메뉴에서 **'expression'(모든 항목)에 대해 지역 변수 소개'** 를 선택합니다.

   > [!TIP]
   > 미리 보기 창 맨 아래에 있는 **변경 내용 미리 보기** 링크를 사용하여 선택하기 전에 적용될 [모든 변경 내용을 확인](../../ide/preview-changes.md)합니다.

   사용에서 추론된 형식을 사용하여 지역 변수가 만들어집니다. 새 지역 변수에 새 이름을 지정합니다.

   - C#:

       ![인터페이스 구현 결과 C#](media/local-result-cs.png)

   - Visual Basic:

       ![인터페이스 구현 결과 VB](media/local-result-vb.png)

   > [!NOTE]
   > **...모든 항목...** 메뉴 옵션을 사용하면 특별히 강조 표시한 항목만이 아니라 선택한 식의 모든 인스턴스를 대체할 수 있습니다.

## <a name="see-also"></a>참고 항목

- [코드 생성](../code-generation-in-visual-studio.md)
- [변경 내용 미리 보기](../../ide/preview-changes.md)
