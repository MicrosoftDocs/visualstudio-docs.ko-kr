---
title: 메서드 재정의 생성
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 3c3a8f4eaf863fd8174ff70339fffc80141fc38d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75569246"
---
# <a name="generate-an-override-in-visual-studio"></a>Visual Studio에서 재정의 생성

이 코드 생성은 다음에 적용됩니다.

- C#

- Visual Basic

**대상:** 기본 클래스에서 재정의할 수 있는 메서드에 대한 코드를 즉시 생성할 수 있습니다.

**시기:** 기본 클래스 메서드를 재정의하고 시그니처를 자동으로 생성하려고 합니다.

**이유:** 메서드 시그니처를 직접 작성할 수 있지만 이 기능은 시그니처를 자동으로 생성합니다.

## <a name="how-to"></a>방법

1. C#에서 `override` 또는 Visual Basic에서 `Overrides` 및 다음에 공백을 입력합니다. 이는 재정의 메서드를 삽입하는 것과 같습니다.

   - C#:

      ![IntelliSense 재정의 C#](media/override-intellisense-cs.png)

   - Visual Basic:

      ![IntelliSense 재정의 VB](media/override-intellisense-vb.png)

2. 기본 클래스에서 재정의할 메서드를 선택합니다.

   > [!TIP]
   > - 속성 아이콘 사용 ![속성 아이콘](media/override-property-cs.png) 목록에서 속성을 표시하거나 숨깁니다.
   > - 메서드 아이콘 사용 ![메서드 아이콘](media/override-method-cs.png) 목록에서 메서드를 표시하거나 숨깁니다.

   선택한 메서드 또는 속성이 구현할 수 있는 재정의로 클래스에 추가됩니다.

   - C#:

       ![재정의 결과 C#](media/override-result-cs.png)

   - Visual Basic:

       ![재정의 결과 VB](media/override-result-vb.png)

## <a name="see-also"></a>참고 항목

- [코드 생성](../code-generation-in-visual-studio.md)
