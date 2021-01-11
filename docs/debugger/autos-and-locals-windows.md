---
title: 변수 검사 - 자동 및 지역 창 | Microsoft Docs
description: Visual Studio에서 디버그하는 동안 자동 및 지역 창에서 변수를 검사합니다. 디버깅하는 동안 자동 및 지역 창에 변수 값이 표시됩니다.
ms.custom: SEO-VS-2020, seodec18
ms.date: 10/18/2018
ms.topic: how-to
f1_keywords:
- vs.debug.autos
- vs.debug.locals
helpviewer_keywords:
- debugger, variable windows
- debugging [Visual Studio], variable windows
ms.assetid: bb6291e1-596d-4af0-9f22-5fd713d6b84b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b57c27d038193a5c73bee48814a2aa457a94b6a6
ms.sourcegitcommit: 3c571f44bfd6402efea5187af43df287bac5b6ac
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/24/2020
ms.locfileid: "97760915"
---
# <a name="inspect-variables-in-the-autos-and-locals-windows"></a>자동 및 지역 창에서 변수 검사

디버깅하는 동안 **자동** 및 **지역** 창에 변수 값이 표시됩니다. 창은 디버깅 세션 중에만 사용할 수 있습니다. **자동** 창에는 현재 중단점 주위에서 사용된 변수가 표시됩니다. **지역** 창에는 일반적으로 현재 함수 또는 메서드인 로컬 범위에 정의된 변수가 표시됩니다.

> [!NOTE]
> 코드를 처음으로 디버그하는 경우 이 문서를 진행하기 전에 먼저 [완전 초보자를 위한 디버깅](../debugger/debugging-absolute-beginners.md) 및 [디버깅 기술과 도구](../debugger/write-better-code-with-visual-studio.md)를 읽어보는 것이 좋습니다.

 **자동** 창은 C#, Visual Basic, C++ 및 Python 코드에 사용할 수 있지만 JavaScript 또는 F#에는 사용할 수 없습니다.

디버깅 중에 **자동** 창을 열려면 **디버그** > **Windows** > **자동** 을 선택하거나 **Ctrl**+**Alt**+**V** > **A** 를 누릅니다.

디버깅 중에 **지역** 창을 열려면 **디버그** > **Windows** > **지역** 을 선택하거나 **Alt**+**4** 를 누릅니다.

> [!NOTE]
> 이 토픽은 Windows용 Visual Studio에만 적용됩니다. Mac용 Visual Studio는 [Mac용 Visual Studio의 데이터 시각화](/visualstudio/mac/data-visualizations)를 참조하세요.

## <a name="use-the-autos-and-locals-windows"></a>자동 및 지역 창 사용

배열 및 개체는 트리 컨트롤로 **자동** 및 **지역** 창에 표시됩니다. 필드 및 속성을 표시하도록 보기를 확장하려면 변수 이름 왼쪽에 있는 화살표를 선택합니다. 다음은 **지역** 창에 있는 <xref:System.IO.FileStream?displayProperty=fullName> 개체의 예입니다.

![파일이 System.IO.FileStream 값으로 설정된 지역 창의 스크린샷](../debugger/media/locals-filestream.png)

**지역** 또는 **자동** 창의 빨간색 값은 마지막 평가 이후 값이 변경되었음을 의미합니다. 이전 디버깅 세션에서 변경되었거나 창에서 값을 변경했기 때문일 수 있습니다.

디버거 창의 기본 숫자 형식은 10진수입니다. 16진수로 변경하려면 **지역** 또는 **자동** 창을 마우스 오른쪽 단추로 클릭하고 **16진수 표시** 를 선택합니다. 이 변경 내용은 모든 디버거 창에 영향을 줍니다.

## <a name="edit-variable-values-in-the-autos-or-locals-window"></a>자동 또는 지역 창에서 변수 값 편집

**자동** 또는 **지역** 창에서 대부분의 변수 값을 편집하려면 값을 두 번 클릭하고 새 값을 입력합니다.

값에 대해 식을 입력할 수 있습니다(예: `a + b`). 디버거는 유효한 언어 식을 대부분 받아들입니다.

네이티브 C++ 코드에서 변수 이름의 컨텍스트를 한정해야 할 수 있습니다. 자세한 내용은 [컨텍스트 연산자(C++)](../debugger/context-operator-cpp.md)를 참조하세요.

>[!CAUTION]
>값과 식을 변경하기 전에 결과를 이해해야 합니다. 가능한 문제는 다음과 같습니다.
>
>- 일부 경우에는 식을 계산하면 변수 값이 바뀌거나 프로그램 상태에 영향이 미칠 수 있습니다. 예를 들어 `var1 = ++var2`를 평가하면 `var1` 및 `var2`의 값이 모두 변경됩니다. 이러한 식은 [파생 작업](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\))이 있다고 합니다. 파생 작업은 인식하지 못하는 경우 의도하지 않은 결과가 발생할 수 있습니다.
>
>- 부동 소수점 값을 편집하면 소수 부분이 10진수에서 이진수로 변환되면서 약간의 오차가 발생할 수 있습니다. 겉보기에 해가 없는 편집 작업을 수행하는 경우에도 부동 소수점 변수의 일부 비트가 변경될 수 있습니다.

::: moniker range=">= vs-2019" 
## <a name="search-in-the-autos-or-locals-window"></a>자동 또는 지역 창에서 검색

각 창 위의 검색 창을 사용하여 **자동** 또는 **지역** 창의 이름, 값 및 형식 열에서 키워드를 검색할 수 있습니다. ENTER를 누르거나 화살표 중 하나를 선택하여 검색을 실행합니다. 진행 중인 검색을 취소하려면 검색 창에서 "x" 아이콘을 선택합니다.

왼쪽 및 오른쪽 화살표(각각 Shift+F3, F3)를 사용하여 찾은 일치 항목 사이를 탐색합니다.

![지역 창에서 검색](../debugger/media/ee-search-locals.png "지역 창에서 검색")

검색을 보다 정밀하게 하려면 **자동** 또는 **지역** 창의 맨 위에 있는 **심층 검색** 드롭다운을 사용하여 중첩된 개체를 검색하려는 수준 깊이를 선택합니다. 

## <a name="pin-properties-in-the-autos-or-locals-window"></a>자동 또는 지역 창에서 속성 고정

> [!NOTE]
> 이 기능은 .NET Core 3.0 이상에서 지원됩니다.

**고정 가능한 속성** 도구를 사용하여 자동 및 지역 창에서 해당 속성을 기준으로 개체를 신속하게 검사할 수 있습니다.  이 도구를 사용하려면 속성을 마우스로 가리킨 후 표시되는 고정 아이콘을 선택하거나 마우스 오른쪽 단추를 클릭하고 바로 가기 메뉴에서 **즐겨찾기로 멤버 고정** 옵션을 선택합니다.  그러면 해당 속성이 개체의 속성 목록 맨 위로 버블링되고 속성 이름과 값이 **값** 열에 표시됩니다.  속성을 고정 해제하려면 고정 아이콘을 다시 선택하거나 바로 가기 메뉴에서 **즐겨찾기로 멤버 고정 해제** 옵션을 선택합니다.

![지역 창에서 속성 고정](../debugger/media/basic-pin.gif "지역 창에서 속성 고정")

자동 또는 지역 창에서 개체의 속성 목록을 볼 때 속성 이름을 전환하고 고정되지 않은 속성을 필터링할 수도 있습니다.  자동 또는 지역 창 위의 도구 모음에서 단추를 선택하여 각 옵션에 액세스할 수 있습니다.

![즐겨찾기 속성 필터링](../debugger/media/filter-pinned-properties-locals.png "즐겨찾기 속성 필터링")
![속성 이름 설정/해제](../debugger/media/toggle-property-names.gif "속성 이름 설정/해제")

::: moniker-end

## <a name="change-the-context-for-the-autos-or-locals-window"></a>자동 또는 지역 창의 컨텍스트 변경

**디버그 위치** 도구 모음을 사용하여 원하는 함수, 스레드 또는 프로세스를 선택할 수 있습니다. 이 함수는 **자동** 및 **지역** 창의 컨텍스트를 변경합니다.

**디버그 위치** 도구 모음을 사용하도록 설정하려면 도구 모음 영역의 빈 부분을 클릭하고 드롭다운에서 **디버그 위치** 를 선택하거나 **보기** > **도구 모음** > **디버그 위치** 를 선택합니다.

중단점을 설정하고 디버깅을 시작합니다. 중단점에 도달하면 실행이 일시 중지되고 **디버그 위치** 도구 모음에서 위치를 볼 수 있습니다.

![디버그 위치 도구 모음](../debugger/media/debuglocationtoolbar.png "디버그 위치 도구 모음")

## <a name="variables-in-the-autos-window-c-c-visual-basic-python"></a><a name="bkmk_whatvariables"></a> 자동 창의 변수(C#, C++, Visual Basic, Python)

다른 코드 언어는 **자동** 창에 다른 변수를 표시합니다.

- C# 및 Visual Basic에서 **자동** 창에는 현재 또는 이전 줄에 사용된 모든 변수가 표시됩니다. 예를 들어 C# 또는 Visual Basic 코드에서 다음 네 가지 변수를 선언합니다.

   ```csharp
       public static void Main()
       {
          int a, b, c, d;
          a = 1;
          b = 2;
          c = 3;
          d = 4;
       }
   ```

   `c = 3;` 줄에 중단점을 설정하고 디버거를 시작합니다. 실행이 일시 중지되면 **자동** 창이 표시됩니다.

   ![c 값이 0으로 설정된 자동 창의 스크린샷](../debugger/media/autos-csharp.png)

   `c = 3` 줄이 아직 실행되지 않았으므로 `c`의 값은 0입니다.

- C++의 **자동** 창에는 실행이 중지된 현재 줄 앞에 세 개 이상의 줄에서 사용된 변수가 표시됩니다. 예를 들어 C++ 코드에서 6개의 변수를 선언합니다.

   ```C++
       void main() {
           int a, b, c, d, e, f;
           a = 1;
           b = 2;
           c = 3;
           d = 4;
           e = 5;
           f = 6;
       }
   ```

    `e = 5;` 줄에 중단점을 설정하고 디버거를 실행합니다. 실행이 중지되면 **자동** 창이 표시됩니다.

    ![값이 3인 int c를 보여 주는 줄이 강조 표시된 자동 창의 스크린샷](../debugger/media/autos-cplus.png)

    `e = 5` 줄이 아직 실행되지 않았기 때문에 `e` 변수가 초기화되지 않았습니다.

## <a name="view-return-values-of-method-calls"></a><a name="bkmk_returnValue"></a> View return values of method calls
 .NET 및 C++ 코드에서는 메서드 호출을 프로시저 단위로 실행하거나 프로시저에서 나가는 경우 **자동** 창의 반환 값을 검사할 수 있습니다. 메서드 호출 반환 값 보기는 지역 변수에 저장되지 않는 경우에 유용할 수 있습니다. 메서드는 매개 변수 또는 다른 메서드의 반환 값으로 사용할 수 있습니다.

 예를 들어 다음 C# 코드는 두 함수의 반환 값을 추가합니다.

```csharp
static void Main(string[] args)
{
    int a, b, c, d;
    a = 1;
    b = 2;
    c = 3;
    d = 4;
    int x = sumVars(a, b) + subtractVars(c, d);
}

private static int sumVars(int i, int j)
{
    return i + j;
}

private static int subtractVars(int i, int j)
{
    return j - i;
}
```

자동 창에서 `sumVars()` 및 `subtractVars()` 메서드 호출의 반환 값을 보려면 다음을 수행합니다.

1. `int x = sumVars(a, b) + subtractVars(c, d);` 줄에 중단점을 설정합니다.

1. 디버깅을 시작하고 중단점에서 실행이 일시 중지되면 **프로시저 단위 실행** 을 선택하거나 **F10** 을 누릅니다. **자동** 창에서 다음 반환 값을 확인해야 합니다.

  ![자동 반환 값 C#](../debugger/media/autosreturnvaluecsharp2.png "자동 반환 값 C#")

## <a name="see-also"></a>참조

- [디버깅이란?](../debugger/what-is-debugging.md)
- [디버깅 기술 및 도구](../debugger/write-better-code-with-visual-studio.md)
- [먼저 디버깅 살펴보기](../debugger/debugger-feature-tour.md)
- [디버거 창](../debugger/debugger-windows.md)
