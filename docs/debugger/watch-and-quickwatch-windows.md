﻿---
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
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301016"
---

# <a name="watch-variables-with-watch-windows-and-quickwatch"></a>조사식 창 및 간략한 조사식을 사용하여 변수 살펴보기

디버깅하는 동안 **Watch** 창 및 **QuickWatch를** 사용하여 변수 및 식을 볼 수 있습니다. 창은 디버깅 세션 중에만 사용할 수 있습니다.

**조사식** 창은 디버깅하는 동안 한 번에 여러 변수를 표시할 수 있습니다.**간략한 조사식** 대화 상자는 한 번에 하나의 변수를 표시하며 디버깅을 계속하려면 닫아야 합니다.

이 문서를 진행하기 전에 코드를 디버깅하려고 처음 시도한 경우 [절대 초보자를 위한 디버깅](../debugger/debugging-absolute-beginners.md) 및 [디버깅 기술 및 도구를](../debugger/write-better-code-with-visual-studio.md) 읽을 수 있습니다.

## <a name="observe-variables-with-a-watch-window"></a>감시 창을 통해 변수 관찰

둘 이상의 **감시** 창을 열고 **감시** 창에서 둘 이상의 변수를 관찰할 수 있습니다.

예를 들어 `a`의 값에 대 한 조사식을 설정 하려면 다음 코드에서를 `b`하 고 `c` 합니다.
예를 들어 다음 코드에서 a, b 및 c 값에 조사식을 설정하려면:

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

1. 먼저 `c = a + b;`;`에 중단점을 설정합니다. 왼쪽 여백을 클릭하거나, **디버그**  >  **중단점 토글** 을 설정하거나, **F9**키를 누르면 됩니다.

1. 녹색 **시작** 화살표 또는 **디버그** > **시작 디버깅을**선택하여 디버깅을 시작하거나 **F5를**누릅니다. 중단점에서 실행이 일시 중지됩니다.

1. **디버그** >  **Windows** >  **조사식** >  **조사식1**을 선택하거나, **Ctrl** + **Alt** + **W** >  **1**을 눌러 조사식 창을 엽니다.
2.녹색 **시작** 화살표 또는 **디버그> 디버깅 시작**을 선택하여 디버깅을 시작하거나 **F5**를 누르십시오. 중단 점에서 실행이 일시 중지됩니다.

3.**디버그**> **Windows**> **조사식**> **조사식1**을 선택하거나, **Ctrl** + **Alt** + **W**> **1**을 눌러 조사식 창을 엽니다.

   창 **2**,**3** 또는 **4**를 선택하여 추가 **조사식**창을 열 수 있습니다.
   
4.**조사식** 창에서 빈 행을 선택하고 변수 `a`를 입력합니다. `b`와 `c`에 대해서도 동일하게 수행하세요.
5. 계속 진행하려면 **디버그**> **단계씩**을 선택하거나 **F11**을 눌러 디버깅을 계속하세요. `for` 루프를 반복할 때 **조사식** 창에서 변수 값이 변경됩니다.

>[!NOTE]
>C++만 해당
>- 변수 이름 또는 변수 이름을 사용하는 식의 컨텍스트를 규정해야 할 수도 있습니다. 컨텍스트는 변수가 있는 함수, 소스 파일 또는 모듈입니다. 컨텍스트를 규정해야 하는 경우 **조사식** 창의 **이름**에서 [컨텍스트 연산자(C++)](../debugger/context-operator-cpp.md) 문서를 참조하세요.

>- $사용 하 여 레지스터 이름 및 변수 이름을 추가할 수 있습니다. **\<&nbsp;이름 >** 또는 **@\<이름**&nbsp;를 **조사식** 창의 **이름** 에 등록 합니다. 자세한 내용은 [Pseudovariables](../debugger/pseudovariables.md)를 참조하세요.

## <a name="use-expressions-in-a-watch-window"></a>감시 창에서 표현식 사용

**감시** 창에서 디버거가 인식하는 유효한 식을 관찰할 수 있습니다.


예를 들어, 이전 섹션의 코드에 대해 **조사식** 창에 `(a + b + c) / 3`을 입력하여 세 가지 값의 평균을 얻을 수 있습니다:

![시청 식](../debugger/media/watchexpression.png "시청 식")


**조사식** 창에서 식을 평가하는 규칙은 일반적으로 코드 언어의 식을 평가하기 위한 규칙과 동일합니다. 식에 구문 오류가 있으면 코드 편집기와 동일한 컴파일러 오류를 예상합니다. 예를 들어 앞의 식에서 오타가 발생하면 **조사식** 창에서도 오류가 발생합니다:

![시청식 오류](../debugger/media/watchexpressionerror.png "시청식 오류")

두 개의 물결 모양의 선 아이콘이 있는 원이 **Watch** 창에 나타날 수 있습니다. 이 아이콘은 잠재적인 스레드 간 종속성으로 인해 디버거가 식을 평가하지 않는다는 것을 의미합니다. 코드를 평가하려면 앱의 다른 스레드가 일시적으로 실행되려면 앱의 다른 스레드가 필요하지만 중단 모드에 있으므로 앱의 모든 스레드는 일반적으로 중지됩니다. 다른 스레드를 일시적으로 실행하도록 허용하면 앱 상태에 예기치 않은 영향을 미칠 수 있으며 디버거는 해당 스레드의 중단점 및 예외와 같은 이벤트를 무시할 수 있습니다.


::: moniker range=">= vs-2019" 
## <a name="search-in-the-watch-window"></a>보기 창에서 검색


각 창 위의 검색 표시줄을 사용하여 **조사식** 창의 이름, 값 및 유형 열에서 키워드를 검색할 수 있습니다. ENTER를 누르거나 화살표 중 하나를 선택하여 검색을 실행할 수 있습니다. 진행 중인 검색을 취소하려면 검색 표시줄에서 "x" 아이콘을 선택합니다.

왼쪽 및 오른쪽 화살표(각각 Shift+F3 및 F3)를 사용하여 찾은 일치 항목 사이를 탐색합니다.

![시계 창에서 검색](../debugger/media/ee-search-watch.png "시계 창에서 검색")

검색을 다소 철저하게 하려면 **조사식** 창의 상단에 있는 **심층 검색** 드롭다운을 사용하여 중첩된 개체에 대해 검색할 수준을 선택하세요.

## <a name="pin-properties-in-the-watch-window"></a>보기 창의 속성 고정

>[!NOTE]
> 이 기능은 .NET Core 3.0 이상에서 지원됩니다.

고정 가능한 속성 도구를 사용하여 조사창의 속성별로 객체를 빠르게 **검사할** 수 있습니다.  이 도구를 사용하려면 속성 위로 마우스를 가져가고 나타나는 핀 아이콘을 선택하거나 마우스 오른쪽 단추로 클릭하고 결과 컨텍스트 메뉴에서 **핀 멤버를 즐겨찾기** 옵션으로 선택합니다.  이렇게 하면 해당 속성이 개체의 속성 목록 맨 위에 포동포동하게 되고 속성 이름과 값이 **Value** 열에 표시됩니다.  속성의 고정을 해제하려면 핀 아이콘을 다시 선택하거나 컨텍스트 메뉴에서 멤버 고정 해제 옵션을 **즐겨찾기로** 선택합니다.

![보기 창의 속성 고정](../debugger/media/basic-pin-watch.gif "보기 창의 속성 고정")

Watch 창에서 개체의 속성 목록을 볼 때 속성 이름을 전환하고 고정되지 않은 속성을 필터링할 수도 있습니다.  감시 창 위의 도구 모음에서 단추를 선택하여 두 옵션에 모두 액세스할 수 있습니다.

::: moniker-end

### <a name="refresh-watch-values"></a><a name="bkmk_refreshWatch"></a>시계 값 새로 고침


식을 계산하는 경우에 새로 고침 아이콘(원형 화살표)이 **조사식** 창에 나타날 수 있습니다. 새로 고침 아이콘은 오류 또는 오래된 값을 나타냅니다.

값을 새로 고치려면 새로 고침 아이콘을 선택하거나 스페이스바를 누릅니다. 디버거가 식을 다시 계산합니다. 그러나 값이 평가되지 않은 이유에 따라 식을 다시 평가하거나 다시 평가하지 않을 수 있습니다.

새로 고침 아이콘 위로 마우스를 가져가거나 식이 평가되지 않은 이유로 **값** 열을 볼 수 있습니다. 그 이유는 다음과 같습니다.

- 이전 예제와 같이 식이 평가될 때 오류가 발생했습니다. 시간 시간이 발생하거나 변수가 범위를 벗어날 수 있습니다.

- 식에는 앱에서 부작용을 유발할 수 있는 함수 호출이 있습니다. [식 부작용](#bkmk_sideEffects)을 참조하십시오.

- 속성 및 암시적 함수 호출의 자동 평가는 사용할 수 없습니다.

속성 및 암시적 함수 호출의 자동 평가가 비활성화되어 새로 고침 아이콘이 나타나면 **도구**> **옵션**> **디버깅**> **일반**에서 **속성 확인 및 기타 암시적 함수 호출** 사용을 선택하여 이를 사용할 수 있습니다.

새로 고침 아이콘을 사용하여 시연하려면 다음을 수행하십시오.

1. **도구** > **옵션** > **디버깅** > **일반에서**Enable 속성 평가 및 기타 **암시적 함수 호출** 확인란을 선택 취소합니다.

2. 다음 코드를 입력합니다. 그리고 **조사식** 창에서 `list.Count`속성에 조사식을 설정합니다.


   ```csharp
   static void Main(string[] args)
   {
       List<string> list = new List<string>();
       list.Add("hello");
       list.Add("goodbye");
   }
   ```


   ![리프레시 워치](../debugger/media/refreshwatch.png "리프레시 워치")

1. 값을 새로 고치려면 새로 고침 아이콘을 선택하거나 스페이스바를 누릅니다. 디버거는 식을 다시 평가합니다.

### <a name="expression-side-effects"></a><a name="bkmk_sideEffects"></a>표현 효과

일부 식을 계산 하면 변수 값이 변경 되거나 응용 프로그램의 상태에 영향을 줄 수 있습니다. 예를 들어 다음 식을 계산하면 `var1`의 값이 변경됩니다.
### <a name="bkmk_sideEffects"></a>식 부작용

일부 식을 계산 하면 변수 값이 변경 되거나 응용 프로그램의 상태에 영향을 줄 수 있습니다. 예를 들어 다음 식을 계산하면 `var1`의 값이 변경됩니다.

```csharp
var1 = var2
```


이 코드는 [부작용(side effect)](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\))을 유발할 수 있습니다. 부작용은 앱 작동 방식을 변경하여 디버깅을 더 어렵게 만들 수 있습니다.

부작용이 있는 식은 처음 입력할 때 한 번만 평가됩니다. 그런 다음 식이 **Watch** 창에서 회색으로 표시되고 추가 평가가 비활성화됩니다. 도구 설명 또는 **값** 열은 표현식이 부작용을 일으킨다고 설명합니다. 값 옆에 나타나는 새로 고침 아이콘을 선택하여 강제로 재평가할 수 있습니다.

부작용 지정을 방지하는 한 가지 방법은 자동 기능 평가를 끄는 것입니다. **도구** > **옵션** > **디버깅** > **일반에서**속성 **평가 및 기타 암시적 함수 호출을 선택**해제합니다.

의 C# 경우에만 속성이 나 암시적 함수 호출이 해제 된 경우에는 **조사식** 창에서 변수 **이름** 에 **ac** 형식 한정자를 추가 하 여 계산을 강제로 실행할 수 있습니다. [C#의 형식 지정자](../debugger/format-specifiers-in-csharp.md)를 참조하세요.
C#의 경우에만 속성 평가 또는 암시적 함수 호출이 해제된 경우 **조사식** 창의 변수 **이름**에 **ac** 형식 수정자를 추가하여 강제로 평가할 수 있습니다. [C#의 형식 지정자](../debugger/format-specifiers-in-csharp.md)를 참조하세요.


## <a name="use-object-ids-in-the-watch-window-c-and-visual-basic"></a><a name="bkmk_objectIds"></a>감시 창에서 개체 아이디 사용(C# 및 시각적 기본)

특정 개체의 동작을 관찰하려는 경우가 있습니다. 예를 들어 해당 변수가 범위를 벗어난 후 로컬 변수에서 참조하는 개체를 추적할 수 있습니다. C# 및 Visual Basic에서 참조 형식의 특정 인스턴스에 대한 개체 ID를 만들고 **조사식** 창 및 중단점 조건에서 사용할 수 있습니다. 개체 ID는 CLR(공용 언어 런타임) 디버깅 서비스에 의해 생성되고 개체와 연결됩니다.

> [!NOTE]
> 개체 아이디는 개체가 가비지 수집되는 것을 방지하지 않는 약한 참조를 만듭니다. 현재 디버깅 세션에 대해서만 유효합니다.

다음 코드에서 메서드는 `MakePerson()` 로컬 `Person` 변수를 사용하여 만듭니다.

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


`DoSomething()` 메서드에서 `Person`의 이름을 찾으려면 **조사식** 창에서 `Person` 개체 ID에 대한 참조를 추가할 수 있습니다.

1. 개체를 만든 후 코드에서 `Person` 중단점을 설정합니다.

2. 디버깅을 시작합니다.

3. 중단점에서 실행이 일시 정지되면 **디버그**> **창**> **로컬**을 선택하여 **로컬** 창을 엽니다.

4. **로컬** 창에서 `Person` 변수를 마우스 오른쪽 단추로 클릭하고 **개체 ID 만들기**를 선택하세요.

   **로컬** 창에 달러 기호(**$**)와 숫자가 표시되어야 합니다. 이는 개체 ID입니다.

5. 개체 ID를 마우스 오른쪽 단추로 클릭하고 **조사식 추가**를 선택하여 **조사식** 창에 개체 ID를 추가합니다.

6. `DoSomething()` 메서드에 또 다른 중단점을 설정합니다.

7. 디버깅을 계속합니다. `DoSomething()` 메서드에서 실행이 일시 중지되면 **조사식** 창에 `Person` 개체가 표시됩니다.

   > [!NOTE]
   > 개체의 속성을 표시하려는 경우 `Person.Name`를 선택하여 속성 평가를 사용해야 합니다. **도구** > **옵션** > **디버깅** > **일반** > **속성 확인 및 기타 암시적 함수 호출**을 선택합니다.

## <a name="dynamic-view-and-the-watch-window"></a>동적 보기 및 보기 창

일부 스크립팅 언어(예: JavaScript 또는 Python)는 동적 또는 [오리](https://en.wikipedia.org/wiki/Duck_typing) 입력을 사용하며 .NET 버전 4.0 이상은 일반 디버깅 창에서 관찰하기 어려운 개체를 지원합니다.

**조사식** 창에는 이러한 객체가 동적 객체로 표시되며, 이 객체는 <xref:System.Dynamic.IDynamicMetaObjectProvider> 인터페이스를 구현하는 유형에서 생성됩니다. 동적 객체 노드는 동적 객체의 동적 멤버를 표시하지만 멤버 값을 편집 할 수는 없습니다.

동적 보기 값을 새로 고치려면 동적 개체 노드 옆에 있는 [새로 고침 아이콘을](#bkmk_refreshWatch) **선택합니다.**

개체에 대한 **동적 보기만** 표시하려면 **Watch** 창에서 동적 개체 이름 옆에 **동적** 형식 지정기를 추가합니다.


- C#의 경우: `ObjectName, dynamic`
- Visual Basic의 경우: `$dynamic, ObjectName`

>[!NOTE]
>- C# 디버거는 다음 코드 줄로 단계별로 이동하면 **동적 보기의** 값을 자동으로 다시 평가하지 않습니다.
>- Visual Basic 디버거는 **동적 보기를**통해 추가된 식을 자동으로 새로 고칩니다.
>- **동적 뷰**의 멤버를 평가하면 [부작용](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\))이 발생할 수 있습니다.

**동적 오브젝트에 객체를 캐스팅하는 새 watch 변수를 삽입하려면 다음을 수행합니다.**

1. **동적 뷰**의 하위를 마우스 오른쪽 단추로 클릭합니다.
2. **조사식 추가**를 선택합니다. `object.name`은 `((dynamic)object).name`이 되고 새로운 **조사식** 창에 나타납니다.

또한 디버거는 자동 창에 개체의 **동적 보기** 자식 **노드를 추가합니다.** **자동** 창을 열려면 디버깅 중에**Windows** > 자동 **디버그를** > 선택합니다.**Autos**

**동적 보기는** COM 개체에 대한 디버깅도 향상시킵니다. 디버거가 **System.__ComObject**래핑된 COM 개체에 도달하면 개체에 대한 **동적 보기** 노드가 추가됩니다.

## <a name="observe-a-single-variable-or-expression-with-quickwatch"></a> QuickWatch로 단일 변수 또는 표현식 관찰

**QuickWatch를** 사용하여 단일 변수를 관찰할 수 있습니다.

예를 들어 다음 코드의 경우:


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


변수 `a`를 관찰해 봅시다:


1. `a = a + b;` 줄에 중단점을 설정합니다.

1. 디버깅을 시작합니다. 중단점에서 실행이 일시 중지됩니다.

1. 코드에서 `a` 변수를 선택합니다.

1. **디버그** > **간략 한 조사식**을 선택 하거나 **Shift**+**F9**키를 누르거나 마우스 오른쪽 단추를 클릭 하 고 **간략 한 조사식**을 선택 합니다.
**QuickWatch** 대화 상자가 나타납니다. 변수`a`는 **식** 상자에 있으며 **값**이 **1**입니다.

   **퀵워치** 대화 상자가 나타납니다. 변수는 `a` **값** **1이**있는 **식** 상자에 있습니다.

5. 변수를 사용하여 표현식을 평가하려면 표현식 상자에 `a + b`와 같은 **식**을 입력하고 **재평가**를 선택하십시오.
   ![간략 한 조사식 변수](../debugger/media/quickwatchvariable.png "간략 한 조사식 변수")

   ![퀵워치 표현식](../debugger/media/quickwatchexpression.png "퀵워치 표현식")

7.**QuickWatch** 창을 닫으려면 **닫기**를 선택하세요. (**QuickWatch**는 모달 대화 상자이므로 열려 있는 한 계속 디버깅할 수 없습니다.)
8. 디버깅을 계속합니다. **조사식** 창에서 변수를 확인할 수 있습니다.

## <a name="see-also"></a>참고 항목
- [디버깅이란?](../debugger/what-is-debugging.md)
- [디버깅 기술 및 도구](../debugger/write-better-code-with-visual-studio.md)
- [디버깅을 먼저 살펴보십시오.](../debugger/debugger-feature-tour.md)
- [디버거 창](../debugger/debugger-windows.md)
