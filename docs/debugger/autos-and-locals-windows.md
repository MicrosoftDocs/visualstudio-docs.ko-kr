---
title: 변수 검사-자동 및 지역 창 | Microsoft Docs
ms.custom: seodec18
ms.date: 10/18/2018
ms.topic: conceptual
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
ms.openlocfilehash: b159f631534135ac568fb03dbffa46ae0360fc47
ms.sourcegitcommit: 0b90e1197173749c4efee15c2a75a3b206c85538
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/07/2019
ms.locfileid: "74904102"
---
# <a name="inspect-variables-in-the-autos-and-locals-windows"></a>자동 및 지역 창에서 변수 검사

디버깅하는 동안 **Autos**와 **Locals** 창에 변수 값이 표시됩니다. Windows는 디버깅 세션 중에서만 사용할 수 있습니다. **Autos** 창에는 현재 중단점 주위에 사용된 변수가 표시됩니다. **Locals** 창에는 일반적으로 현재 함수 또는 메서드인 지역 범위에 정의된 변수가 표시됩니다. 처음으로 코드를 디버그하려는 경우 이 문서를 진행하기 전에 [초보자를 위한 디버깅](../debugger/debugging-absolute-beginners.md)과 [기술 및 도구 디버깅](../debugger/write-better-code-with-visual-studio.md)을 먼저 읽고 오는것이 좋습니다.

**Autos** 창은 C#, Visual Basic, C++ 및 Python 코드에서는 사용할 수 있지만 JavaScript 또는 F#에서는 사용할 수 없습니다.

**자동** 창을 열려면 디버그 하는 동안 **Windows** > **자동**으로 **디버그** > 선택 하거나 **Ctrl**+**alt**+**V** > **을**누릅니다.

디버깅하는 동안 **Locals** 창을 열려면 **디버그** > **Windows** > **Locals**를 선택하거나 **Alt**+**4**를 누릅니다.

> [!NOTE]
> 이 토픽은 Windows의 Visual Studio에 적용됩니다. Mac용 Visual Studio에 대한 내용은 [Mac용 Visual Studio에서 데이터 시각화](/visualstudio/mac/data-visualizations)를 참조하세요.

## <a name="use-the-autos-and-locals-windows"></a>자동 및 지역 창 사용

배열과 객체는 **Autos** 및 **Locals** 창에 트리 컨트롤로 표시됩니다. 변수 이름 왼쪽에 있는 화살표를 선택하면 필드와 속성 표시가 확장되어 보입니다. **Locals** 창에 있는 <xref:System.IO.FileStream?displayProperty=fullName> 객체의 예는 다음과 같습니다.

![지역-FileStream](../debugger/media/locals-filestream.png "Locals-FileStream")

**Locals** 또는 **Autos** 창의 빨간색 값은 마지막 평가 이후 값이 변경되었음을 나타냅니다. 이전 디버깅 세션에서 변경되었거나 창에서 값을 변경했기 때문일 수 있습니다.

디버거 창의 기본 숫자 형식은 10진수입니다. 16진수로 변경하려면 **Locals** 또는 **Autos** 창에서 마우스 오른쪽 단추를 클릭하고 **16진수 표시**를 선택하세요. 이 변경은 모든 디버거 창에 영향을 줍니다.

**Autos** 또는 **Locals** 창에서 대부분의 변수 값을 편집하려면 값을 두 번 클릭하고 새 값을 입력하세요.

값에 대해 식을 입력할 수 있습니다(예: `a + b`). 디버거는 유효한 언어 식을 대부분 받아들입니다.

값에 대해 식을 입력할 수 있습니다(예: `a + b`). 디버거는 유효한 언어 식을 대부분 받아들입니다.
네이티브 C++ 코드에서 변수 이름의 컨텍스트를 한정해야 할 수 있습니다. 자세한 내용은 [컨텍스트 연산자(C++)](../debugger/context-operator-cpp.md)를 참조하세요.

>[!CAUTION]
>값과 표현식을 변경하기 전에 결과를 이해해야 합니다. 가능한 문제는 다음과 같습니다.
>
>- 일부 경우에는 식을 계산하면 변수 값이 바뀌거나 프로그램 상태에 영향이 미칠 수 있습니다. 예를 들어, `var1 = ++var2`를 계산하면 `var1` 와 `var2`값 전부가 변경됩니다. 이러한 경우 해당 식은 [부작용](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\))이 있다고 합니다. 부작용을 정확히 이해하지 않으면 예상치 못한 결과가 도출될 수 있습니다.
>
>- 부동 소수점 값을 편집하면 소수 부분이 10진수에서 이진수로 변환되면서 약간의 오차가 발생할 수 있습니다. 겉보기에 무해한 편집이라도 부동 소수점 변수의 일부 비트가 변경될 수 있습니다.

::: moniker range=">= vs-2019" 
## <a name="search-in-the-autos-or-locals-window"></a>Autos 또는 Locals 창에서 검색

각 창 위의 검색 창을 사용하여 **Autos** 또는 **Locals** 창의 이름, 값 및 유형 열에서 키워드를 검색할 수 있습니다. ENTER를 누르거나 화살표 중 하나를 선택하여 검색을 실행할 수 있습니다. 진행 중인 검색을 취소하려면 검색 표시줄에서 "x" 아이콘을 선택합니다.

찾은 일치 항목을 탐색하려면 왼쪽 및 오른쪽 화살표(각각 Shift + F3 및 F3)를 사용하세요.

![지역 창에서 검색](../debugger/media/ee-search-locals.png "지역 창에서 검색")

검색을 더 또는 덜 철저하게 하려면 **Autos** 또는 **Locals** 창의 맨 위에 있는 더 **심층적인 검색** 드롭 다운을 사용하여 중첩된 개체를 검색할 수준을 선택하세요. 
## <a name="pin-properties-in-the-autos-or-locals-window"></a>자동 또는 지역 창에서 속성 고정

> [!NOTE]
> 이 기능은 .NET Core 3.0 이상에서 지원 됩니다.

**Pinnable 속성** 도구를 사용 하 여 자동 및 지역 창에서 개체의 속성을 기준으로 개체를 신속 하 게 검사할 수 있습니다.  이 도구를 사용 하려면 속성 위로 마우스를 이동 하 고 표시 되는 고정 아이콘을 선택 하거나 마우스 오른쪽 단추를 클릭 하 고 결과 상황에 맞는 메뉴에서 **즐겨찾기로 멤버 고정** 옵션을 선택 합니다.  그러면 해당 속성이 개체의 속성 목록 맨 위에 표시 되 고 속성 이름 및 값이 **값** 열에 표시 됩니다.  속성을 고정 해제 하려면 고정 아이콘을 다시 선택 하거나 상황에 맞는 메뉴에서 **멤버를 즐겨찾기로 고정 해제** 옵션을 선택 합니다.

![지역 창에서 속성 고정](../debugger/media/basic-pin.gif "지역 창에서 속성 고정")

자동 또는 지역 창에서 개체의 속성 목록을 볼 때 속성 이름을 전환 하 고 고정 되지 않은 속성을 필터링 할 수도 있습니다.  자동 또는 지역 창 위의 도구 모음에서 단추를 선택 하 여 각 옵션에 액세스할 수 있습니다.

![속성 이름 설정/해제](../debugger/media/toggle-property-names.gif "속성 이름 설정/해제")
![즐겨찾기 속성](../debugger/media/filter-pinned-properties-locals.png "즐겨찾기 속성 필터링")

## <a name="pin-properties-in-the-autos-or-locals-window"></a>자동 또는 지역 창에서 속성 고정

> [!NOTE]
> 이 기능은 .NET Core 3.0 이상에서 지원 됩니다.

**Pinnable 속성** 도구를 사용 하 여 자동 및 지역 창에서 개체의 속성을 기준으로 개체를 신속 하 게 검사할 수 있습니다.  이 도구를 사용 하려면 속성 위로 마우스를 이동 하 고 표시 되는 고정 아이콘을 선택 하거나 마우스 오른쪽 단추를 클릭 하 고 결과 상황에 맞는 메뉴에서 **즐겨찾기로 멤버 고정** 옵션을 선택 합니다.  그러면 해당 속성이 개체의 속성 목록 맨 위에 표시 되 고 속성 이름 및 값이 **값** 열에 표시 됩니다.  속성을 고정 해제 하려면 고정 아이콘을 다시 선택 하거나 상황에 맞는 메뉴에서 **멤버를 즐겨찾기로 고정 해제** 옵션을 선택 합니다.

![지역 창에서 속성 고정](../debugger/media/basic-pin.gif "지역 창에서 속성 고정")

자동 또는 지역 창에서 개체의 속성 목록을 볼 때 속성 이름을 전환 하 고 고정 되지 않은 속성을 필터링 할 수도 있습니다.  자동 또는 지역 창 위의 도구 모음에서 단추를 선택 하 여 각 옵션에 액세스할 수 있습니다.

![속성 이름 설정/해제](../debugger/media/toggle-property-names.gif "속성 이름 설정/해제")
![즐겨찾기 속성](../debugger/media/filter-pinned-properties-locals.png "즐겨찾기 속성 필터링")

::: moniker-end

## <a name="change-the-context-for-the-autos-or-locals-window"></a>자동 또는 지역 창의 컨텍스트 변경

**디버그 위치** 도구 모음을 사용하여 원하는 함수, 스레드 또는 프로세스를 선택하여 **Autos** 및 **Locals** 창의 컨텍스트를 변경할 수 있습니다.

**디버그 위치** 도구 모음을 사용하려면 도구 모음 영역의 빈 부분을 클릭하고 드롭 다운에서 **디버그 위치**를 선택하거나 **보기 >  도구 모음 >  디버그 위치**를 선택합니다.

중단점을 설정하고 디버깅을 시작합니다. 중단점에 도달하면 실행이 일시 정지되고 **디버그 위치** 도구 모음에 위치가 표시됩니다.

![디버그 위치 도구 모음](../debugger/media/debuglocationtoolbar.png "디버그 위치 도구 모음")

## <a name="bkmk_whatvariables"></a>자동 창의 변수 (C#, C++, Visual Basic, Python)

다른 코드 언어는 **Autos** 창에서 다른 변수를 표시합니다.

- C# 및 Visual Basic에서 **자동** 창에는 현재 또는 이전 줄에 사용된 모든 변수가 표시됩니다. 예를 들어, C# 또는 Visual Basic 코드에서 다음 4개의 변수를 선언하세요.

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

   `c = 3;` 줄에 중단점을 설정하고 디버거를 시작하세요. 실행이 일시 중지되면 **Autos** 창은 다음을 표시합니다.

   ![자동-CSharp](../debugger/media/autos-csharp.png "Autos-CSharp")

   `c = 3` 행이 아직 실행되지 않았으므로 `c` 값은 0입니다.

- C ++에서 **Autos** 창은 실행이 일시 중지된 현재 줄 이전에 적어도 세 줄에 사용된 변수를 표시합니다. 예를 들어, C++ 코드에서 6개의 변수를 선언하세요.

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

    `e = 5;` 줄에 중단점을 설정하고 디버거를 실행합니다. 실행이 중지되는 경우 **Autos** 창에 다음이 표시됩니다.

    ![자동C++](../debugger/media/autos-cplus.png "자동C++")

    `e = 5` 줄이 실행되지 않았으므로 변수 `e`는 초기화되지 않았습니다.

## <a name="bkmk_returnValue"></a> View return values of method calls
 .NET 및 C++ 코드에서는 메서드 호출을 넘어서거나 벗어날 때 **Autos** 창에서 반환 값을 검사할 수 있습니다. 로컬 변수에 저장되지 않은 경우 메서드 호출 반환 값을 보는 것이 유용할 수 있습니다. 메서드는 매개 변수 또는 다른 메서드의 반환 값으로 사용될 수 있습니다.

 예를 들어 다음 C# 코드는 두 함수의 반환 값을 추가 합니다.

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

`sumVars()`의 반환 값을 확인 하 고 자동 창에서 메서드 호출을 `subtractVars()` 합니다.

1. `int x = sumVars(a, b) + subtractVars(c, d);` 줄에 중단점을 설정합니다.

1. 디버깅을 시작하고 실행이 중단점에서 일시 중지하는 경우 **단계씩**을 선택하거나 **F10**을 누릅니다. **Autos** 창에 다음과 같은 반환 값이 표시됩니다.

  ![자동 반환 값C#](../debugger/media/autosreturnvaluecsharp2.png "자동 반환 값C#")

## <a name="see-also"></a>참조

- [디버깅이란?](../debugger/what-is-debugging.md)
- [디버깅 기술 및 도구](../debugger/write-better-code-with-visual-studio.md)
- [먼저 디버깅 살펴보기](../debugger/debugger-feature-tour.md)
- [디버거 창](../debugger/debugger-windows.md)
