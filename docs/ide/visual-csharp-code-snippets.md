---
title: C# 코드 조각
ms.date: 06/05/2017
ms.topic: reference
helpviewer_keywords:
- snippets [C#]
- code snippets [C#]
- Code Snippet Inserter [C#]
- C#, code snippets
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: d41907a15b7e0b1692dda3f4d678c2b843dfcd03
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75594164"
---
# <a name="c-code-snippets"></a>C# 코드 조각

코드 조각은 신속하게 코드에 삽입할 수 있는 준비된 코드 조각입니다. 예를 들어 `for` 코드 조각에서는 비어 있는 `for` 루프를 만듭니다. 일부 코드 조각은 코드 감싸기 코드 조각으로, 코드 줄을 선택한 다음 선택한 코드 줄을 통합하는 코드 조각을 선택할 수 있습니다. 예를 들어 코드 줄을 선택한 다음 `for` 코드 조각을 활성화하는 경우 루프 블록 안에 해당 코드 줄을 포함하여 `for` 루프를 만듭니다. 코드 조각을 사용하면 빠르고 쉽게, 안정적으로 프로그램 코드를 작성할 수 있습니다.

커서 위치에 코드 조각을 삽입하거나, 현재 선택한 코드 주위에 코드 감싸기 코드 조각을 삽입할 수 있습니다. 코드 조각 삽입기는 **IntelliSense**메뉴의 **코드 조각 삽입** 또는 **코드 감싸기** 명령을 통해 또는 각각 키보드 바로 가기 **Ctrl**+**K**,**X** 또는 **Ctrl**+**K**,**S**를 사용하여 호출됩니다.

**코드 조각 삽입기**에 사용 가능한 모든 코드 조각에 대한 코드 조각 이름이 표시됩니다. 또한 코드 조각 삽입기에는 코드 조각의 이름이나 코드 조각 이름의 일부를 입력할 수 있는 입력 대화 상자가 포함되어 있습니다. 코드 조각 삽입기에서 코드 조각 이름과 가장 일치하는 항목이 강조 표시됩니다. 언제든지 **Tab** 키를 누르면 코드 조각 삽입기가 해제되고 현재 선택한 코드 조각이 삽입됩니다. **Esc** 키를 입력하거나 코드 편집기에서 마우스를 클릭하면 코드 조각을 삽입하지 않고 코드 조각 삽입기가 해제됩니다.

## <a name="default-code-snippets"></a>기본 코드 조각

기본적으로 다음 코드 조각이 C#용 Visual Studio에 포함되어 있습니다.

|이름(또는 바로 가기)|Description|코드 조각을 삽입할 수 있는 유효 위치|
| - |-----------------| - |
|#if|[#if](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-if) 지시문과 [#endif](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-endif) 지시문을 만듭니다.|원하는 위치|
|#region|[#region](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-region) 지시문과 [#endregion](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-endregion) 지시문을 만듭니다.|원하는 위치|
|~|포함하는 클래스에 대한 [finalizer](/dotnet/csharp/programming-guide/classes-and-structs/destructors)(소멸자)를 만듭니다.|클래스 내부|
|attribute|<xref:System.Attribute>에서 파생되는 클래스에 대한 선언을 만듭니다.|네임스페이스(전역 네임스페이스 포함), 클래스 또는 구조체 내부|
|선택|[checked](/dotnet/csharp/language-reference/keywords/checked) 블록을 만듭니다.|메서드, 인덱서, 속성 접근자 또는 이벤트 접근자 내부|
|class|class 선언을 만듭니다.|네임스페이스(전역 네임스페이스 포함), 클래스 또는 구조체 내부|
|ctor|포함하는 클래스에 대한 생성자를 만듭니다.|클래스 내부|
|cw|<xref:System.Console.WriteLine%2A> 호출을 만듭니다.|메서드, 인덱서, 속성 접근자 또는 이벤트 접근자 내부|
|do|[do](/dotnet/csharp/language-reference/keywords/do) `while` 루프를 만듭니다.|메서드, 인덱서, 속성 접근자 또는 이벤트 접근자 내부|
|else|[else](/dotnet/csharp/language-reference/keywords/if-else) 블록을 만듭니다.|메서드, 인덱서, 속성 접근자 또는 이벤트 접근자 내부|
|enum|[enum](/dotnet/csharp/language-reference/keywords/enum) 선언을 만듭니다.|네임스페이스(전역 네임스페이스 포함), 클래스 또는 구조체 내부|
|equals|<xref:System.Object> 클래스에 정의된 <xref:System.Object.Equals%2A> 메서드를 재정의하는 메서드 선언을 만듭니다.|클래스 또는 구조체 내부|
|exception|예외(기본적으로 <xref:System.Exception>)에서 파생되는 클래스에 대한 선언을 만듭니다.|네임스페이스(전역 네임스페이스 포함), 클래스 또는 구조체 내부|
|for|[for](/dotnet/csharp/language-reference/keywords/for) 루프를 만듭니다.|메서드, 인덱서, 속성 접근자 또는 이벤트 접근자 내부|
|foreach|[foreach](/dotnet/csharp/language-reference/keywords/foreach-in) 루프를 만듭니다.|메서드, 인덱서, 속성 접근자 또는 이벤트 접근자 내부|
|forr|각 반복 후에 루프 변수가 감소하는 [for](/dotnet/csharp/language-reference/keywords/for) 루프를 만듭니다.|메서드, 인덱서, 속성 접근자 또는 이벤트 접근자 내부|
|if|[if](/dotnet/csharp/language-reference/keywords/if-else) 블록을 만듭니다.|메서드, 인덱서, 속성 접근자 또는 이벤트 접근자 내부|
|인덱서|indexer 선언을 만듭니다.|클래스 또는 구조체 내부|
|인터페이스|[interface](/dotnet/csharp/language-reference/keywords/interface) 선언을 만듭니다.|네임스페이스(전역 네임스페이스 포함), 클래스 또는 구조체 내부|
|호출|안전하게 이벤트를 호출하는 블록을 만듭니다.|메서드, 인덱서, 속성 접근자 또는 이벤트 접근자 내부|
|iterator|반복기를 만듭니다.|클래스 또는 구조체 내부|
|iterindex|중첩된 클래스를 사용하여 "명명된" 반복기 및 인덱서 쌍을 만듭니다.|클래스 또는 구조체 내부|
|lock|[lock](/dotnet/csharp/language-reference/keywords/lock-statement) 블록을 만듭니다.|메서드, 인덱서, 속성 접근자 또는 이벤트 접근자 내부|
|mbox|<xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=fullName> 호출을 만듭니다. *System.Windows.Forms.dll*에 대한 참조를 추가해야 할 수도 있습니다.|메서드, 인덱서, 속성 접근자 또는 이벤트 접근자 내부|
|네임스페이스|[namespace](/dotnet/csharp/language-reference/keywords/namespace) 선언을 만듭니다.|네임스페이스(전역 네임스페이스 포함) 내부|
|prop|[자동 구현 속성](/dotnet/csharp/programming-guide/classes-and-structs/auto-implemented-properties) 선언을 만듭니다.|클래스 또는 구조체 내부|
|propfull|`get` 및 `set` 접근자를 사용하여 속성 선언을 만듭니다.|클래스 또는 구조체 내부|
|propg|전용 `set` 접근자를 사용하여 읽기 전용 [자동 구현 속성](/dotnet/csharp/programming-guide/classes-and-structs/auto-implemented-properties)을 만듭니다.|클래스 또는 구조체 내부|
|sim|[static](/dotnet/csharp/language-reference/keywords/static) [int](/dotnet/csharp/language-reference/keywords/int) Main 메서드 선언을 만듭니다.|클래스 또는 구조체 내부|
|struct|[struct](/dotnet/csharp/language-reference/keywords/struct) 선언을 만듭니다.|네임스페이스(전역 네임스페이스 포함), 클래스 또는 구조체 내부|
|svm|[static](/dotnet/csharp/language-reference/keywords/static) [void](/dotnet/csharp/language-reference/keywords/void) Main 메서드 선언을 만듭니다.|클래스 또는 구조체 내부|
|스위치|[switch](/dotnet/csharp/language-reference/keywords/switch) 블록을 만듭니다.|메서드, 인덱서, 속성 접근자 또는 이벤트 접근자 내부|
|다음을 시도해 보세요.|[try-catch](/dotnet/csharp/language-reference/keywords/try-catch) 블록을 만듭니다.|메서드, 인덱서, 속성 접근자 또는 이벤트 접근자 내부|
|tryf|[try-finally](/dotnet/csharp/language-reference/keywords/try-finally) 블록을 만듭니다.|메서드, 인덱서, 속성 접근자 또는 이벤트 접근자 내부|
|선택 취소|[unchecked](/dotnet/csharp/language-reference/keywords/unchecked) 블록을 만듭니다.|메서드, 인덱서, 속성 접근자 또는 이벤트 접근자 내부|
|unsafe|[unsafe](/dotnet/csharp/language-reference/keywords/unsafe) 블록을 만듭니다.|메서드, 인덱서, 속성 접근자 또는 이벤트 접근자 내부|
|사용|[using](/dotnet/csharp/language-reference/keywords/using-directive) 지시문을 만듭니다.|네임스페이스(전역 네임스페이스 포함) 내부|
|while|[while](/dotnet/csharp/language-reference/keywords/while) 루프를 만듭니다.|메서드, 인덱서, 속성 접근자 또는 이벤트 접근자 내부|

## <a name="see-also"></a>참고 항목

- [코드 조각 함수](../ide/code-snippet-functions.md)
- [코드 조각](../ide/code-snippets.md)
- [템플릿 매개 변수](../ide/template-parameters.md)
- [방법: 코드 감싸기 코드 조각 사용](../ide/how-to-use-surround-with-code-snippets.md)
