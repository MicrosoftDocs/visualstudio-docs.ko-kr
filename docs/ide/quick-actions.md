---
title: 빠른 작업, 전구 및 스크루드라이버
ms.date: 03/28/2018
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: bfafcca1cddcaa216b8a9e12dd7d961949afa2bb
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90036524"
---
# <a name="quick-actions"></a>빠른 작업

빠른 작업을 사용하면 단일 작업으로 쉽게 코드를 리팩터링하거나, 생성하거나, 수정할 수 있습니다. 빠른 작업은 C#, [C++](/cpp/ide/writing-and-refactoring-code-cpp) 및 Visual Basic 코드 파일에 사용할 수 있습니다. 일부 작업은 특정 언어에 국한되며, 나머지 작업은 모든 언어에 적용됩니다.

빠른 작업은 다음에 사용할 수 있습니다.

- [코드 분석기](../code-quality/roslyn-analyzers-overview.md) 규칙 위반에 대한 코드 수정 적용

::: moniker range=">=vs-2019"

- 코드 분석기 규칙 위반 [표시 안 함](../code-quality/use-roslyn-analyzers.md#suppress-violations) 또는 해당 심각도 [구성](../code-quality/use-roslyn-analyzers.md#set-rule-severity-from-the-light-bulb-menu)

::: moniker-end

::: moniker range="vs-2017"

- 코드 분석기 규칙 위반 [표시 안 함](../code-quality/use-roslyn-analyzers.md#suppress-violations)

::: moniker-end

- 리팩터링 적용(예: [임시 변수 인라인](../ide/reference/inline-temporary-variable.md))

- 코드 생성(예: [지역 변수 도입](../ide/reference/introduce-local-variable.md))

> [!NOTE]
> 이 토픽은 Windows의 Visual Studio에 적용됩니다. Mac용 Visual Studio는 [리팩터링(Mac용 Visual Studio)](/visualstudio/mac/refactoring)을 참조하세요.

전구![전구 아이콘](media/light-bulb-icon.png) 또는 스크루드라이버![스크루드라이버 아이콘](media/screwdriver-icon.png) 아이콘을 사용하거나 **Ctrl**+**을 눌러 빠른 작업을 적용 할 수 있습니다.** 동작을 사용할 수 있는 코드 줄에 커서가 있는 경우입니다. 오류를 나타내는 빨간 물결무늬가 있는 경우 오류 전구![오류 전구 아이콘](media/error-light-bulb-icon.png)가 표시되고, Visual Studio에는 해당 오류에 사용할 수 있는 수정 사항이 있습니다.

어떤 언어든지 타사에서 SDK에 포함하는 방식 등을 통해 사용자 지정 진단 및 제안을 제공할 수 있으며 Visual Studio 전구는 이러한 규칙을 기반으로 표시됩니다.

## <a name="icons"></a>아이콘

빠른 작업을 사용할 수 있을 때 나타나는 아이콘은 사용 가능한 해결 방법 또는 리팩터링 형식을 나타냅니다. *스크루드라이버* ![스크루드라이버 아이콘](media/screwdriver-icon.png) 아이콘은 코드를 변경하는 데 사용할 수 있는 작업이 있음을 나타내지만 반드시 사용해야 하는 것은 아닙니다. *노란색 전구* ![전구 아이콘](media/light-bulb-icon.png) 아이콘은 코드 개선을 위해 *해야 하는* 작업이 있음을 나타냅니다. *오류 전구* ![오류 전구 아이콘](media/error-light-bulb-icon.png) 아이콘은 코드에서 오류를 수정하는 데 사용할 수 있는 작업이 있음을 나타냅니다.

## <a name="to-see-a-light-bulb-or-screwdriver"></a>전구 또는 스크루드라이버를 표시하려면

사용 가능한 수정 사항이 있다면 다음과 같은 경우에 전구가 표시됩니다.

- 오류 위치를 마우스로 가리키는 경우

   ![마우스로 가리킨 전구](../ide/media/vs2015_lightbulb_hover.png)

- 캐럿(커서)을 해당 코드 줄로 이동하는 경우(편집기의 왼쪽 여백에 표시됨)

코드 줄에서 **Ctrl**+ **.** 를 눌러 사용 가능한 빠른 작업 및 리팩토링 목록을 볼 수 있습니다.

잠재적 수정 사항을 보려면 전구 또는 **잠재적 수정 사항 표시** 링크 옆의 아래쪽 화살표를 선택합니다. 사용 가능한 빠른 작업 목록이 표시됩니다.

![확장된 전구](../ide/media/vs2015_lightbulb_hover_expanded.png)

## <a name="see-also"></a>참고 항목

- [Visual Studio에서 코드 생성](../ide/code-generation-in-visual-studio.md)
- [일반적인 빠른 작업](../ide/common-quick-actions.md)
- [코드 스타일 및 빠른 작업](../ide/code-styles-and-code-cleanup.md)
- [코드(C++) 쓰기 및 리팩터링](/cpp/ide/writing-and-refactoring-code-cpp)
- [리팩터링(Mac용 Visual Studio)](/visualstudio/mac/refactoring)
