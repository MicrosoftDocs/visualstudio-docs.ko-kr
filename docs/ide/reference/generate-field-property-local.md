---
title: 필드, 속성, 로컬 변수 생성
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: b554aa5586150942c0fc7d7aeada9356a67029ca
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595607"
---
# <a name="generate-a-field-property-or-local-variable-in-visual-studio"></a>Visual Studio에서 필드, 속성 또는 로컬 변수 생성

이 코드 생성은 다음에 적용됩니다.

- C#

- Visual Basic

**대상:** 이전에 선언되지 않은 필드, 속성 또는 로컬에 대한 코드를 즉시 생성할 수 있습니다.

**시기:** 새 필드, 속성 또는 로컬을 소개하고 자동으로 해당 항목을 제대로 선언하려고 합니다.

**이유:** 필드, 속성 또는 로컬을 사용하기 전에 사용자가 해당 항목을 선언할 수 있지만, 이 기능은 선언 및 형식을 자동으로 생성합니다.

## <a name="how-to"></a>방법

1. 빨간색 구부러진 곡선이 있는 줄에 커서를 놓습니다. 빨간색 구부러진 곡선은 아직 존재하지 않는 필드, 로컬 또는 속성을 나타냅니다.

   - C#:

       ![강조 표시된 코드 C#](media/field-highlight-cs.png)

   - Visual Basic:

       ![강조 표시된 코드 VB](media/field-highlight-vb.png)

2. 다음 작업 중 하나를 수행합니다.

   - **키보드**
      - 줄의 임의 위치에서 **Ctrl**+ **.** 를 눌러 **빠른 작업 및 리팩터링** 메뉴를 트리거합니다.
   - **마우스**
      - 마우스 오른쪽 단추로 클릭하고 **빠른 작업 및 리팩터링** 메뉴를 선택합니다.
      - 빨간색 구부러진 곡선 위로 마우스를 이동하고 표시되는 ![오류 전구](media/error-bulb.png) 아이콘을 클릭합니다.
      - 텍스트 커서가 이미 구부러진 빨간 곡선이 있는 줄 위에 있으면 왼쪽 여백에 나타나는 ![오류 전구](media/error-bulb.png) 아이콘을 클릭합니다.

      ![필드/속성/로컬 생성 미리 보기](media/field-preview-cs.png)

3. 드롭다운 목록에서 생성 옵션 중 하나를 선택합니다.

   > [!TIP]
   > 미리 보기 창 맨 아래에 있는 **변경 내용 미리 보기** 링크를 사용하여 선택하기 전에 적용될 [모든 변경 내용을 확인](../../ide/preview-changes.md)합니다.

   필드, 속성 또는 로컬은 해당 사용에서 추론된 형식을 사용하여 만들어집니다.

   - C#:

       ![메서드 생성 결과 C#](media/field-result-cs.png)

   - Visual Basic:

       ![메서드 생성 결과 VB](media/field-result-vb.png)

## <a name="see-also"></a>참고 항목

- [코드 생성](../code-generation-in-visual-studio.md)
- [변경 내용 미리 보기](../../ide/preview-changes.md)
