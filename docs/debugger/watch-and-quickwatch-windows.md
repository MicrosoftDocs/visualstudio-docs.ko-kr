---
title: 변수에 조사식 설정 | Microsoft Docs
ms.custom: seodec18
ms.date: 10/11/2018
ms.topic: how-to
f1_keywords:
- vs.debug.watch
helpviewer_keywords:
- debugging [Visual Studio], Watch window
- expressions [debugger], evaluating
- variables [debugger], evaluating
- expression evaluation
- registers, evaluating
- debugging [Visual Studio], expression evaluation
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6ab66089de25b7648b13e1ba05f88ab55b7868df
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2020
ms.locfileid: "85348030"
---
# <a name="watch-variables-with-watch-windows-and-quickwatch"></a>조사식 창 및 간략한 조사식을 사용하여 변수 보기

디버깅하는 동안 **조사식** 창과 **간략한 조사식**을 사용하여 변수와 식을 볼 수 있습니다. 창은 디버깅 세션 중에만 사용할 수 있습니다.

**조사식** 창은 디버깅하는 동안 한 번에 여러 변수를 표시할 수 있습니다. **간략한 조사식** 대화 상자에는 한 번에 하나의 변수가 표시되며 디버깅을 계속하려면 닫아야 합니다.

코드를 처음으로 디버그하는 경우 이 문서를 진행하기 전에 먼저 [완전 초보자를 위한 디버깅](../debugger/debugging-absolute-beginners.md) 및 [디버깅 기술과 도구](../debugger/write-better-code-with-visual-studio.md)를 읽어보는 것이 좋습니다.

## <a name="observe-variables-with-a-watch-window"></a>조사식 창을 사용하여 변수 관찰

두 개 이상의 **조사식** 창을 열고 **조사식** 창에서 둘 이상의 변수를 관찰할 수 있습니다.

예를 들어 다음 코드에서 `a`, `b`, `c`의 값에 조사식을 설정하려면:

```C++
int main()
{
    int a, b, c;
    a = 1;
    b = 2;
    c = 0;

    for (int i = 0; i < 10; i++)
    {
        a++;
        b *= 2;
        c = a + b;
    }

    return 0;
}

```

1. 왼쪽 여백을 클릭하여 `c = a + b;` 줄에 중단점을 설정하고 **디버그** > **중단점 설정/해제**를 선택하거나 **F9**를 누릅니다.

1. 녹색 **시작** 화살표 또는 **디버그** > **디버깅 시작**을 선택하거나 **F5**를 눌러 디버깅을 시작합니다. 중단점에서 실행이 일시 중지됩니다.

1. **디버그** > **창** > **조사식** > **조사식 1**을 선택하거나 **Ctrl**+**Alt**+**W** > **1**을 눌러서 **조사식** 창을 엽니다.

   조사식 **2**, **3** 또는 **4**를 선택하여 추가 **조사식** 창을 열 수 있습니다.

1. **조사식** 창에서 빈 행을 선택하고 변수 `a`를 입력합니다. `b` 및 `c`에 대해서도 동일하게 수행합니다.

   ![변수 보기](../debugger/media/watchvariables.png "WatchVariables")

1. **디버그** > **단계 정보**를 선택하거나 진행에 필요한 경우 **F11**을 눌러서 디버깅을 계속합니다. `for` 루프를 반복하면 **조사식** 창의 변수 값이 변경됩니다.

>[!NOTE]
>C++의 경우에만
>- 변수 이름의 컨텍스트 또는 변수 이름을 사용하는 식을 한정해야 할 수도 있습니다. 컨텍스트는 변수가 있는 함수, 원본 파일 또는 모듈입니다. 컨텍스트를 한정해야 하는 경우 **조사식** 창의 **이름**에서 [컨텍스트 연산자(C++)](../debugger/context-operator-cpp.md) 구문을 사용합니다.
>
>- **$\<register&nbsp;name> 또는** **@\<register&nbsp;name>** 을 사용하여 **조사식** 창의 **이름**에 등록 이름 및 변수 이름을 추가할 수 있습니다. 자세한 내용은 [Pseudovariables](../debugger/pseudovariables.md)를 참조하세요.

## <a name="use-expressions-in-a-watch-window"></a>조사식 창에서 식 사용

**조사식** 창에서 디버거가 인식한 올바른 모든 식을 관찰할 수 있습니다.

예를 들어 이전 섹션에 있는 코드의 경우 **조사식** 창에 `(a + b + c) / 3`을 입력하여 다음과 같이 세 가지 값의 평균을 구할 수 있습니다.

![조사식 식](../debugger/media/watchexpression.png "조사식 식")

**조사식** 창에서 식을 계산하는 규칙은 일반적으로 코드 언어에서 식을 계산하는 규칙과 동일합니다. 식에 구문 오류가 있으면 코드 편집기와 동일한 컴파일러 오류를 예상합니다. 예를 들어 이전 식에 오타가 있으면 **조사식** 창에서 이 오류가 생성됩니다.

![조사식 식 오류](../debugger/media/watchexpressionerror.png "조사식 식 오류")

**조사식** 창에 두 개의 물결선 아이콘이 있는 원이 나타날 수 있습니다. 이 아이콘은 잠재적 크로스 스레드 종속성으로 인해 디버거가 식을 계산하지 않음을 의미합니다. 코드를 계산하려면 앱의 다른 스레드를 임시로 실행해야 하지만 중단 모드에 있기 때문에 앱의 모든 스레드가 일반적으로 중지됩니다. 다른 스레드를 임시로 실행하도록 허용하면 앱 상태에 예기치 않은 영향을 줄 수 있으며, 디버거는 해당 스레드의 중단점 및 예외와 같은 이벤트를 무시할 수 있습니다.

::: moniker range=">= vs-2019" 
## <a name="search-in-the-watch-window"></a>조사식 창에서 검색

각 창 위의 검색 표시줄을 사용하여 **조사식** 창의 이름, 값 및 형식 열에서 키워드를 검색할 수 있습니다. ENTER를 누르거나 화살표 중 하나를 선택하여 검색을 실행합니다. 진행 중인 검색을 취소하려면 검색 창에서 "x" 아이콘을 선택합니다.

왼쪽 및 오른쪽 화살표(각각 Shift+F3, F3)를 사용하여 찾은 일치 항목 사이를 탐색합니다.

![조사식 창에서 검색](../debugger/media/ee-search-watch.png "조사식 창에서 검색")

검색을 보다 정밀하게 하려면 **조사식** 창의 맨 위에 있는 **심층 검색** 드롭다운을 사용하여 중첩된 개체를 검색하려는 수준 깊이를 선택합니다. 

## <a name="pin-properties-in-the-watch-window"></a>조사식 창에서 속성 고정

>[!NOTE]
> 이 기능은 .NET Core 3.0 이상에서 지원됩니다.

**고정 가능한 속성** 도구를 사용하여 조사식 창에서 해당 속성을 기준으로 개체를 신속하게 검사할 수 있습니다.  이 도구를 사용하려면 속성을 마우스로 가리켜서 표시되는 고정 아이콘을 선택하거나 마우스 오른쪽 단추를 클릭하고 바로 가기 메뉴에서 **즐겨찾기로 멤버 고정** 옵션을 선택합니다.  그러면 해당 속성이 개체의 속성 목록 맨 위로 버블링되고 속성 이름과 값이 **값** 열에 표시됩니다.  속성을 고정 해제하려면 고정 아이콘을 다시 선택하거나 바로 가기 메뉴에서 **즐겨찾기로 멤버 고정 해제** 옵션을 선택합니다.

![조사식 창에서 속성 고정](../debugger/media/basic-pin-watch.gif "조사식 창에서 속성 고정")

조사식 창에서 개체의 속성 목록을 볼 때 속성 이름을 전환하고 고정되지 않은 속성을 필터링할 수도 있습니다.  조사식 창 위의 도구 모음에서 단추를 선택하여 두 가지 옵션에 액세스할 수 있습니다.

::: moniker-end

### <a name="refresh-watch-values"></a><a name="bkmk_refreshWatch"></a> 조사식 값 새로 고침

식이 계산될 때 **조사식** 창에 새로 고침 아이콘(원형 화살표)이 나타날 수 있습니다. 새로 고침 아이콘은 오류 또는 오래된 값을 나타냅니다.

값을 새로 고치려면 새로 고침 아이콘을 선택하거나 스페이스바를 누릅니다. 디버거가 식을 다시 계산합니다. 그러나 값이 계산되지 않은 이유에 따라 식을 다시 계산할 수 없을 수 있습니다.

새로 고침 아이콘을 마우스로 가리키거나 식이 계산되지 않은 이유에 대한 **값** 열을 봅니다. 이유는 다음과 같습니다.

- 이전 예제와 같이 식이 계산되는 중에 오류가 발생했습니다. 시간 제한이 발생하거나 변수가 범위를 벗어났을 수 있습니다.

- 식에 앱에서 부작용을 트리거할 수 있는 함수 호출이 있습니다. [식 부작용](#bkmk_sideEffects)을 참조하세요.

- 속성 자동 계산 및 암시적 함수 호출을 사용할 수 없습니다.

속성 자동 계산 및 암시적 함수 호출이 사용하지 않도록 설정되어 있어서 새로 고침 아이콘이 나타나는 경우, **도구** > **옵션** > **디버깅** > **일반**에서 **속성 계산 및 기타 암시적 함수 호출 사용**을 선택하여 사용하도록 설정할 수 있습니다.

새로 고침 아이콘을 사용하여 시연하려면:

1. **도구** > **옵션** > **디버깅** > **일반**에서 **속성 계산 및 기타 암시적 함수 호출 사용** 확인란의 선택을 해제합니다.

1. 다음 코드를 입력하고 **조사식** 창에서 `list.Count` 속성에 대한 조사식을 설정합니다.

   ```csharp
   static void Main(string[] args)
   {
       List<string> list = new List<string>();
       list.Add("hello");
       list.Add("goodbye");
   }
   ```

1. 디버깅을 시작합니다. **조사식** 창에 다음과 같은 메시지가 표시됩니다.

   ![조사식 새로 고침](../debugger/media/refreshwatch.png "조사식 새로 고침")

1. 값을 새로 고치려면 새로 고침 아이콘을 선택하거나 스페이스바를 누릅니다. 디버거가 식을 다시 계산합니다.

### <a name="expression-side-effects"></a><a name="bkmk_sideEffects"></a> 식 부작용

일부 경우에는 식을 계산하면 변수 값이 바뀌거나 앱 상태에 영향이 미칠 수 있습니다. 예를 들어 다음 식을 계산하면 `var1`의 값이 변경됩니다.

```csharp
var1 = var2
```

이 코드는 [부작용](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\))을 일으킬 수 있습니다. 부작용은 앱의 작동 방식을 변경하여 디버깅을 더 어렵게 만들 수 있습니다.

부작용이 있는 식은 처음 입력할 때 한 번만 계산됩니다. 그 후에는 **조사식** 창에서 식이 회색으로 나타나고 추가 계산을 사용하지 않도록 설정됩니다. 도구 설명 또는 **값** 열에서 식이 부작용을 일으킨다고 설명합니다. 값 옆에 나타나는 새로 고침 아이콘을 선택하여 강제로 다시 계산할 수 있습니다.

부작용 지정을 방지하는 한 가지 방법은 자동 함수 계산을 해제하는 것입니다. **도구** > **옵션** > **디버깅** > **일반**에서 **속성 계산 및 기타 암시적 함수 호출 사용**의 선택을 취소합니다.

C#의 경우에만 속성 계산이나 암시적 함수 호출을 해제할 때 **조사식** 창의 변수 **이름**에 **ac** 형식 한정자를 추가하여 강제로 계산할 수 있습니다. [C#의 형식 지정자](../debugger/format-specifiers-in-csharp.md)를 참조하세요.

## <a name="use-object-ids-in-the-watch-window-c-and-visual-basic"></a><a name="bkmk_objectIds"></a> 조사식 창에서 개체 ID 사용(C# 및 Visual Basic)

특정 개체의 동작을 관찰하려는 경우가 있습니다. 예를 들어 변수가 범위를 벗어난 후 지역 변수에 의해 참조된 개체를 추적할 수 있습니다. C# 및 Visual Basic에서 참조 형식의 특정 인스턴스에 대한 개체 ID를 만들고 **조사식** 창 및 중단점 조건에서 사용할 수 있습니다. 개체 ID는 CLR(공용 언어 런타임) 디버깅 서비스에 의해 생성되고 개체와 연결됩니다.

> [!NOTE]
> 개체 ID는 개체가 가비지를 수집하지 않도록 차단하지 않는 약한 참조를 만듭니다. 현재 디버깅 세션에 대해서만 유효합니다.

다음 코드에서 `MakePerson()` 메서드는 지역 변수를 사용하여 `Person`을 만듭니다.

```csharp
class Person
{
    public Person(string name)
    {
        Name = name;
    }
    public string Name { get; set; }
}

public class Program
{
    static List<Person> _people = new List<Person>();
    public static void Main(string[] args)
    {
        MakePerson();
        DoSomething();
    }

    private static void MakePerson()
    {
        var p = new Person("Bob");
        _people.Add(p);
    }

    private static void DoSomething()
    {
        // more processing
         Console.WriteLine("done");
    }
}
```

`DoSomething()` 메서드에서 `Person` 이름을 찾으려면 **조사식** 창에서 `Person` 개체 ID에 대한 참조를 추가할 수 있습니다.

1. `Person` 개체를 만든 후에 코드에서 중단점을 설정합니다.

1. 디버깅을 시작합니다.

1. 중단점에서 실행이 일시 중지되면 **디버그** > **Windows** > **지역**을 선택하여 **지역** 창을 엽니다.

1. **지역** 창에서 `Person` 변수를 마우스 오른쪽 단추로 클릭하고 **개체 ID만들기**를 선택합니다.

   개체 ID인 **지역** 창에 달러 기호( **$** )와 숫자가 표시되어야 합니다.

1. 개체 ID를 마우스 오른쪽 단추로 클릭하고 **조사식 추가**를 선택하여 **조사식** 창에 개체 ID를 추가합니다.

1. `DoSomething()` 메서드에서 다른 중단점을 설정합니다.

1. 디버깅을 계속합니다. `DoSomething()` 메서드에서 실행이 일시 중지되면 **조사식** 창에 `Person` 개체가 표시됩니다.

   > [!NOTE]
   > `Person.Name`과 같은 개체의 속성을 보려면 **도구** > **옵션** > **디버깅** > **일반** > **속성 계산 및 기타 암시적 함수 호출 사용**을 선택하여 속성 계산을 사용하도록 설정해야 합니다.

## <a name="dynamic-view-and-the-watch-window"></a>동적 뷰 및 조사식 창

일부 스크립팅 언어(예: JavaScript 또는 Python)는 동적 또는 [duck](https://en.wikipedia.org/wiki/Duck_typing) 입력을 사용하며, .NET 버전 4.0 이상에서는 일반 디버깅 창에서 관찰하기 어려운 개체를 지원합니다.

**조사식** 창에는 <xref:System.Dynamic.IDynamicMetaObjectProvider> 인터페이스를 구현하는 형식에서 만들어진 동적 개체로 이러한 개체가 표시됩니다. 동적 개체 노드에서는 동적 개체의 동적 멤버가 표시되지만 멤버의 값을 편집할 수 없습니다.

**동적 뷰** 값을 새로 고치려면 동적 개체 노드 옆의 [새로 고침 아이콘](#bkmk_refreshWatch)을 선택합니다.

개체의 **동적 뷰**만 표시하려면 **조사식** 창에서 동적 개체 이름 뒤에 **동적** 형식 지정자를 추가합니다.

- C#의 경우: `ObjectName, dynamic`
- Visual Basic의 경우: `$dynamic, ObjectName`

>[!NOTE]
>- C# 디버거는 다음 코드 줄을 단계별로 실행할 때 디버거에서 **동적 뷰**에 값을 자동으로 다시 계산하지 않습니다.
>- Visual Basic 디버거는 **동적 뷰**를 통해 추가된 식을 자동으로 새로 고칩니다.
>- **동적 뷰**의 멤버를 평가하면 [부작용](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\))이 발생할 수 있습니다.

**개체를 동적 개체로 캐스트하는 새 조사식 변수를 삽입하려면:**

1. **동적 뷰**의 자식을 마우스 오른쪽 단추로 클릭합니다.
1. **조사식 추가**를 선택합니다. `object.name`은 `((dynamic) object).name`이 되고 새 **조사식** 창에 표시됩니다.

또한 디버거는 **자동** 창에 **동적 뷰** 개체의 자식 노드를 추가합니다. **자동** 창을 열려면 디버깅하는 동안 **디버그** > **창** > **자동**을 선택합니다.

**동적 뷰**는 COM 개체에 대한 디버깅도 향상시킵니다. 디버거가 **System.__ComObject**에 래핑된 COM 개체에 도달하면 개체에 대한 **동적 뷰** 노드를 추가합니다.

## <a name="observe-a-single-variable-or-expression-with-quickwatch"></a>간략한 조사식을 사용하여 단일 변수 또는 식 관찰

**간략한 조사식**을 사용하여 단일 변수를 관찰할 수 있습니다.

예를 들어, 아래 코드의 경우 다음을 수행합니다.

```csharp
static void Main(string[] args)
{
    int a, b;
    a = 1;
    b = 2;
    for (int i = 0; i < 10; i++)
    {
        a = a + b;
    }
}
```

`a` 변수를 관찰하려면

1. `a = a + b;` 줄에 중단점을 설정합니다.

1. 디버깅을 시작합니다. 중단점에서 실행이 일시 중지됩니다.

1. 코드에서 `a` 변수를 선택합니다.

1. **디버그** > **간략한 조사식**을 선택하고 **Shift**+**F9**를 누르거나 마우스 오른쪽 단추를 클릭하고 **간략한 조사식**을 선택합니다.

   **간략한 조사식** 대화 상자가 나타납니다. `a` 변수는 **값**이 **1**인 **식** 상자에 있습니다.

   ![간략한 조사식 변수](../debugger/media/quickwatchvariable.png "간략한 조사식 변수")

1. 변수를 사용하여 식을 계산하려면 **식** 상자에 `a + b`와 같은 식을 입력하고 **다시 계산**을 선택합니다.

   ![간략한 조사식 식](../debugger/media/quickwatchexpression.png "간략한 조사식 식")

1. **간략한 조사식**의 변수 또는 식을 **조사식** 창에 추가하려면 **조사식 추가**를 선택합니다.

1. **닫기**를 선택하여 **간략한 조사식** 창을 닫습니다 (**간략한 조사식** 창은 모달 대화 상자이므로 열려 있는 한 디버깅을 계속할 수 없음).

1. 디버깅을 계속합니다. **조사식** 창에서 변수를 관찰할 수 있습니다.

## <a name="see-also"></a>참조
- [디버깅이란?](../debugger/what-is-debugging.md)
- [디버깅 기술 및 도구](../debugger/write-better-code-with-visual-studio.md)
- [먼저 디버깅 살펴보기](../debugger/debugger-feature-tour.md)
- [디버거 창](../debugger/debugger-windows.md)
