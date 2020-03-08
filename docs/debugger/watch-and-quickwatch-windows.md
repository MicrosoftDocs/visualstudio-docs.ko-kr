---
title: 변수에 대 한 조사식 설정 | Microsoft Docs
ms.custom: seodec18
ms.date: 10/11/2018
ms.topic: conceptual
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
ms.openlocfilehash: ea3d2a1e82e92473859fef29754fbb831cf3685b
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78409336"
---
# <a name="watch-variables-with-watch-windows-and-quickwatch"></a>조사식 창 및 간략한 조사식을 사용하여 변수 살펴보기

디버깅 하는 동안 **조사식** 창 및 **간략** 한 조사식을 사용 하 여 변수 및 식을 조사할 수 있습니다. 창은 디버깅 세션 중에만 사용할 수 있습니다.

**조사식** 창은 디버그 하는 동안 한 번에 여러 변수를 표시할 수 있습니다. **간략 한 조사식** 대화 상자에는 한 번에 하나의 변수가 표시 되며 디버깅을 계속 하려면 닫아야 합니다.

처음으로 코드를 디버깅 하는 경우이 문서를 진행 하기 전에 절대 초보자와 [디버깅 기술 및 도구](../debugger/write-better-code-with-visual-studio.md) [에 대 한 디버깅](../debugger/debugging-absolute-beginners.md) 을 읽어야 할 수 있습니다.

## <a name="observe-variables-with-a-watch-window"></a>조사식 창를 사용 하 여 변수 관찰

두 개 이상의 **조사식** 창을 열고 **조사식** 창에서 둘 이상의 변수를 관찰할 수 있습니다.

예를 들어 `a`의 값에 대 한 조사식을 설정 하려면 다음 코드에서를 `b`하 고 `c` 합니다.

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

1. 왼쪽 여백을 클릭 하 고 **디버그** > **중단점 설정/해제**를 선택 하거나 **F9**키를 눌러 `c = a + b;` 줄에 중단점을 설정 합니다.

1. 녹색 **시작** 화살표 또는 **디버그** > **디버깅 시작**을 선택 하거나 **F5**키를 눌러 디버깅을 시작 합니다. 중단점에서 실행이 일시 중지 됩니다.

1. **디버그** > **Windows** > **시청** > 조사식 **1**을 선택 하거나 **Ctrl**+**Alt**+**W** > **1**을 눌러 **조사식** 창을 엽니다.

   Windows **2**, **3**또는 **4**를 선택 하 여 추가 **조사식** 창을 열 수 있습니다.

1. **조사식** 창에서 빈 행을 선택 하 고 변수 `a`를 입력 합니다. `b` 및 `c`에 대해서도 동일 하 게 수행 합니다.

   ![조사식 변수](../debugger/media/watchvariables.png "WatchVariables")

1. **디버그** > 한 **단계씩 코드 실행** 을 선택 하거나 필요에 따라 **F11** 키를 눌러 디버깅을 계속 진행 합니다. **조사식** 창의 변수 값은 `for` 루프를 반복할 때 변경 됩니다.

>[!NOTE]
>C++만 해당
>- 변수 이름 또는 변수 이름을 사용하는 식의 컨텍스트를 규정해야 할 수도 있습니다. 컨텍스트는 변수가 있는 함수, 소스 파일 또는 모듈입니다. 컨텍스트를 한 정해야 하는 경우 **조사식** 창에서 **이름** 에 [contextC++연산자 ()](../debugger/context-operator-cpp.md) 구문을 사용 합니다.
>
>- $사용 하 여 레지스터 이름 및 변수 이름을 추가할 수 있습니다. **\<&nbsp;이름 >** 또는 **@\<이름**&nbsp;를 **조사식** 창의 **이름** 에 등록 합니다. 자세한 내용은 [Pseudovariables](../debugger/pseudovariables.md)를 참조하세요.

## <a name="use-expressions-in-a-watch-window"></a>조사식 창에서 식 사용

디버거에서 인식 하는 모든 유효한 식을 **조사식** 창에서 관찰할 수 있습니다.

예를 들어 이전 섹션의 코드에서 **조사식** 창에 `(a + b + c) / 3`를 입력 하 여 세 값의 평균을 얻을 수 있습니다.

![조사식 식](../debugger/media/watchexpression.png "조사식 식")

**조사식** 창에서 식을 계산 하는 규칙은 일반적으로 코드 언어에서 식을 계산 하는 규칙과 동일 합니다. 식에 구문 오류가 있으면 코드 편집기와 동일한 컴파일러 오류를 예상합니다. 예를 들어 이전 식의 오타가 있으면 **조사식** 창에서이 오류가 생성 됩니다.

![조사식 식 오류](../debugger/media/watchexpressionerror.png "조사식 식 오류")

두 개의 물결선 아이콘이 있는 원이 **조사식** 창에 표시 될 수 있습니다. 이 아이콘은 잠재적인 스레드 간 종속성으로 인해 디버거가 표현식을 평가하지 않음을 의미합니다. 코드를 평가하려면 앱의 다른 스레드가 일시적으로 실행되어야 하지만 중단 모드이므로 일반적으로 앱의 모든 스레드가 중지됩니다. 다른 스레드가 일시적으로 실행되도록 허용하면 앱 상태에 예기치 않은 영향을 줄 수 있으며 디버거는 해당 스레드의 중단점 및 예외와 같은 이벤트를 무시할 수 있습니다.

::: moniker range=">= vs-2019" 
## <a name="search-in-the-watch-window"></a>조사식 창 검색

각 창 위의 검색 표시줄을 사용 하 여 **조사식** 창의 Name, Value 및 Type 열에서 키워드를 검색할 수 있습니다. ENTER를 누르거나 화살표 중 하나를 선택하여 검색을 실행하세요. 진행 중인 검색을 취소하려면 검색 표시줄에서 "x" 아이콘을 선택합니다.

찾은 일치 항목을 탐색하려면 왼쪽 및 오른쪽 화살표(각각 Shift + F3 및 F3)를 사용하세요.

![조사식 창에서 검색](../debugger/media/ee-search-watch.png "조사식 창에서 검색")

검색을 보다 정밀 하 게 또는 더 낮게 만들려면 **조사식** 창 맨 위에 있는 **자세히 검색** 드롭다운 목록을 사용 하 여 중첩 된 개체를 검색할 수준 깊이를 선택 합니다. 

## <a name="pin-properties-in-the-watch-window"></a>조사식 창에서 속성 고정

>[!NOTE]
> 이 기능은 .NET Core 3.0 이상에서 지원 됩니다.

**Pinnable 속성** 도구를 사용 하 여 조사식 창의 속성을 기준으로 개체를 신속 하 게 검사할 수 있습니다.  이 도구를 사용 하려면 속성 위로 마우스를 이동 하 고 표시 되는 고정 아이콘을 선택 하거나 마우스 오른쪽 단추를 클릭 하 고 결과 상황에 맞는 메뉴에서 **즐겨찾기로 멤버 고정** 옵션을 선택 합니다.  그러면 해당 속성이 개체의 속성 목록 맨 위에 표시 되 고 속성 이름 및 값이 **값** 열에 표시 됩니다.  속성을 고정 해제 하려면 고정 아이콘을 다시 선택 하거나 상황에 맞는 메뉴에서 **멤버를 즐겨찾기로 고정 해제** 옵션을 선택 합니다.

![조사식 창에서 속성 고정](../debugger/media/basic-pin-watch.gif "조사식 창에서 속성 고정")

조사식 창에서 개체의 속성 목록을 볼 때 속성 이름을 전환 하 고 고정 되지 않은 속성을 필터링 할 수도 있습니다.  조사식 창 위의 도구 모음에서 단추를 선택 하 여 두 옵션 모두에 액세스할 수 있습니다.

::: moniker-end

### <a name="bkmk_refreshWatch"></a>조사식 값 새로 고침

식을 평가할 때 새로 고침 아이콘 (원형 화살표)이 **조사식** 창에 나타날 수 있습니다. 새로 고침 아이콘은 오류 또는 오래된 값을 나타냅니다.

값을 새로 고치려면 새로 고침 아이콘을 선택하거나 스페이스바를 누릅니다. 디버거가 식을 다시 계산합니다. 그러나 값이 계산되지 않은 이유에 따라 식을 다시 계산하지 못하거나 계산하지 않고자 할 수도 있습니다.

새로 고침 아이콘을 마우스로 가리키거나 식이 계산 되지 않은 이유에 대 한 **값** 열을 확인 합니다. 그 이유는 다음과 같습니다.

- 이전 예에서와 같이 식을 계산할 때 오류가 발생했습니다. 시간 초과가 발생하거나 변수가 범위를 벗어났을 수 있습니다.

- 식에 앱에서 부작용을 유발할 수 있는 함수 호출이 있습니다. [식 파생 효과](#bkmk_sideEffects)를 참조 하세요.

- 속성의 자동 계산과 암시적 함수 호출은 비활성화되어 있습니다.

속성 자동 확인 및 암시적 함수 호출을 사용할 수 없으므로 새로 고침 아이콘이 표시 되는 경우 **도구** > **옵션** 에서 **속성 확인 및 기타 암시적 함수 호출 사용** 을 선택 하 여 > **디버깅** > **일반**을 선택 하 여 새로 고침 아이콘을 사용 하도록 설정할 수 있습니다.

새로 고침 아이콘을 사용하여 시연하려면:

1. **도구** > **옵션** > **디버깅** > **일반**에서 **속성 확인 및 기타 암시적 함수 호출 사용** 확인란의 선택을 취소 합니다.

1. 다음 코드를 입력 하 고 **조사식** 창에서 `list.Count` 속성에 대 한 조사식을 설정 합니다.

   ```csharp
   static void Main(string[] args)
   {
       List<string> list = new List<string>();
       list.Add("hello");
       list.Add("goodbye");
   }
   ```

1. 디버깅을 시작합니다. **조사식** 창에는 다음 메시지와 유사한 내용이 표시 됩니다.

   ![조사식 새로 고침](../debugger/media/refreshwatch.png "조사식 새로 고침")

1. 값을 새로 고치려면 새로 고침 아이콘을 선택하거나 스페이스바를 누릅니다. 디버거가 식을 다시 평가 합니다.

### <a name="bkmk_sideEffects"></a>식 부작용

일부 식을 계산 하면 변수 값이 변경 되거나 응용 프로그램의 상태에 영향을 줄 수 있습니다. 예를 들어 다음 식을 계산하면 `var1`의 값이 변경됩니다.

```csharp
var1 = var2
```

이 코드를 통해 [부작용](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\))이 발생할 수 있습니다. 부작용은 앱 작동 방식을 변경하여 디버깅을 더 어렵게 만들 수 있습니다.

부작용이 있는 식은 처음 입력할 때 한 번만 계산됩니다. 그런 다음 **조사식** 창에 식이 회색으로 표시 되 고 추가 평가가 사용 하지 않도록 설정 됩니다. 도구 설명 또는 **값** 열은 식에 부작용이 발생 하는 것을 설명 합니다. 값 옆에 나타나는 새로 고침 아이콘을 선택하여 강제로 재계산할 수 있습니다.

부작용을 발생시키지 않는 하나의 방법은 자동 함수 계산을 끄는 것입니다. **도구** > **옵션** > **디버깅** > **일반**에서 속성 확인 **및 기타 암시적 함수 호출 사용**을 선택 취소 합니다.

의 C# 경우에만 속성이 나 암시적 함수 호출이 해제 된 경우에는 **조사식** 창에서 변수 **이름** 에 **ac** 형식 한정자를 추가 하 여 계산을 강제로 실행할 수 있습니다. [C#의 형식 지정자](../debugger/format-specifiers-in-csharp.md)를 참조하세요.

## <a name="bkmk_objectIds"></a>조사식 창에서 개체 Id 사용 (C# 및 Visual Basic)

때로는 특정 개체의 동작을 관찰하려는 경우가 있습니다. 예를 들어, 해당 변수가 범위를 벗어난 후 로컬 변수가 참조하는 개체를 추적하고자 할 수 있습니다. C# 및 Visual Basic에서 참조 형식의 특정 인스턴스에 대한 개체 ID를 만들고 **조사식** 창 및 중단점 조건에서 사용할 수 있습니다. 개체 ID는 CLR(공용 언어 런타임) 디버깅 서비스에 의해 생성되고 개체와 연결됩니다.

> [!NOTE]
> 개체 ID는 개체가 가비지 수집되는 것을 방해하지 않는 약한 참조를 생성합니다. 현재 디버깅 세션에 대해서만 유효합니다.

다음 코드에서 `MakePerson()` 메서드는 지역 변수를 사용 하 여 `Person`를 만듭니다.

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

`DoSomething()` 메서드에서 `Person` 이름을 확인 하려면 **조사식** 창에서 `Person` 개체 ID에 대 한 참조를 추가할 수 있습니다.

1. `Person` 개체를 만든 후 코드에서 중단점을 설정 합니다.

1. 디버깅을 시작합니다.

1. 중단점에서 실행이 일시 중지 되 면 **디버그** > **Windows** > **로컬**을 선택 하 여 **지역** 창을 엽니다.

1. **지역** 창에서 `Person` 변수를 마우스 오른쪽 단추로 클릭 하 고 **개체 ID 만들기**를 선택 합니다.

   **지역** 창에는 달러 기호 ( **$** )와 숫자 (개체 ID)가 표시 됩니다.

1. 개체 ID를 마우스 오른쪽 단추로 클릭 하 고 **조사식 추가**를 선택 하 여 개체 Id를 **조사식** 창에 추가 합니다.

1. `DoSomething()` 메서드에서 다른 중단점을 설정 합니다.

1. 디버깅을 계속합니다. `DoSomething()` 메서드에서 실행이 일시 중지 되 면 **조사식** 창에 `Person` 개체가 표시 됩니다.

   > [!NOTE]
   > 개체의 속성 (예: `Person.Name`)을 확인 하려면 **속성 확인 및 기타 암시적 함수 호출을 사용 하도록 설정** **하 > **  >  ** > ** **도구** > **옵션** 을 선택 하 여 속성 평가를 사용 하도록 설정 해야 합니다.

## <a name="dynamic-view-and-the-watch-window"></a>동적 뷰 및 조사식 창

일부 스크립팅 언어 (예: JavaScript 또는 Python)는 동적 또는 [오리](https://en.wikipedia.org/wiki/Duck_typing) 형식화를 사용 하 고 .net 버전 4.0 이상에서는 일반적인 디버깅 창에서 관찰 하기 어려운 개체를 지원 합니다.

**조사식** 창에는 <xref:System.Dynamic.IDynamicMetaObjectProvider> 인터페이스를 구현 하는 형식에서 만들어진 동적 개체로 이러한 개체가 표시 됩니다. 동적 객체 노드는 동적 객체의 동적 멤버를 표시하지만 멤버 값을 편집 할 수는 없습니다.

**동적 뷰** 값을 새로 고치려면 동적 개체 노드 옆의 [새로 고침 아이콘](#bkmk_refreshWatch) 을 선택 합니다.

개체에 대 한 **동적 보기만** 표시 하려면 **조사식** 창에서 동적 개체 이름 뒤에 **동적** 형식 지정자를 추가 합니다.

- C#의 경우: `ObjectName, dynamic`
- Visual Basic의 경우: `$dynamic, ObjectName`

>[!NOTE]
>- 디버거 C# 는 다음 코드 줄을 단계별로 실행 하는 경우 **동적 뷰에서** 값을 자동으로 다시 평가 하지 않습니다.
>- Visual Basic 디버거는 **동적 뷰**를 통해 추가 된 식을 자동으로 새로 고칩니다.
>- **동적 뷰**의 멤버를 평가하면 [부작용](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\))이 발생할 수 있습니다.

**개체를 동적 개체로 캐스팅 하는 새 조사식 변수를 삽입 하려면**

1. **동적 뷰의**자식을 마우스 오른쪽 단추로 클릭 합니다.
1. **조사식 추가**를 선택 합니다. `object.name` `((dynamic) object).name` 되 고 새 **조사식** 창에 표시 됩니다.

또한 디버거는 **자동** 창에 개체의 **동적 뷰** 자식 노드를 추가 합니다. **자동** 창을 열려면 디버깅 하는 동안 **디버그** > **Windows** > **자동**을 선택 합니다.

또한 **동적 뷰** 는 COM 개체에 대 한 디버깅을 향상 시킵니다. 디버거가 **__ComObject**에 래핑된 COM 개체를 가져오는 경우 해당 개체에 대 한 **동적 뷰** 노드를 추가 합니다.

## <a name="observe-a-single-variable-or-expression-with-quickwatch"></a>QuickWatch로 단일 변수 또는 표현식 관찰

**간략 한 조사식** 을 사용 하 여 단일 변수를 관찰할 수 있습니다.

예를 들어, 다음 코드의 경우:

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

`a` 변수를 관찰 하려면

1. `a = a + b;` 줄에 중단점을 설정합니다.

1. 디버깅을 시작합니다. 중단점에서 실행이 일시 중지 됩니다.

1. 코드에서 `a` 변수를 선택 합니다.

1. **디버그** > **간략 한 조사식**을 선택 하거나 **Shift**+**F9**키를 누르거나 마우스 오른쪽 단추를 클릭 하 고 **간략 한 조사식**을 선택 합니다.

   **간략 한 조사식** 대화 상자가 나타납니다. `a` 변수는 **값** 이 **1**인 **식** 상자에 있습니다.

   ![간략 한 조사식 변수](../debugger/media/quickwatchvariable.png "간략 한 조사식 변수")

1. 변수를 사용 하 **여 식을 계산 하려면 식 상자에** `a + b`와 같은 식을 입력 하 고 다시 **계산**을 선택 합니다.

   ![간략 한 조사식 식](../debugger/media/quickwatchexpression.png "간략 한 조사식 식")

1. **간략** **한 조사식에서 조사식 창에** 변수 또는 식을 추가 하려면 **조사식 추가**를 선택 합니다.

1. **닫기** 를 선택 하 여 **간략 한 조사식** 창을 닫습니다. **간략 한 조사식** 은 모달 대화 상자 이므로 열려 있는 동안에는 디버깅을 계속할 수 없습니다.

1. 디버깅을 계속합니다. **조사식** 창에서 변수를 확인할 수 있습니다.

## <a name="see-also"></a>참고 항목
- [디버깅이란?](../debugger/what-is-debugging.md)
- [디버깅 기술 및 도구](../debugger/write-better-code-with-visual-studio.md)
- [먼저 디버깅 살펴보기](../debugger/debugger-feature-tour.md)
- [디버거 창](../debugger/debugger-windows.md)
