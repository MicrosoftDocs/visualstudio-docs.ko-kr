---
title: EditorConfig에 대한 .NET 언어 규칙
ms.date: 03/31/2020
ms.topic: reference
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- language code style rules [EditorConfig]
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: cbe2b18b9edd6f2d4634ede41d676519f1b80ad3
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90035722"
---
# <a name="language-conventions"></a>언어 규칙

Visual Studio 내의 EditorConfig 언어 규칙은 2개 범주, 즉 Visual Basic과 C#에 적용되는 규칙과 C#에만 적용되는 규칙으로 나뉩니다. 언어 규칙은 한정자와 괄호 등 프로그래밍 언어의 다양한 측면이 사용되는 방식에 영향을 줍니다.

> [!TIP]
> - 원하는 프로그래밍 언어의 코드 예제를 보려면 브라우저 창의 오른쪽 위에 있는 언어 선택을 사용하여 선택합니다.
>
>   ![코드 언어 선택 컨트롤](media/code-language-picker.png)
>
> - **이 문서의 내용** 링크를 사용하여 페이지의 다른 섹션으로 이동할 수 있습니다.

## <a name="rule-format"></a>규칙 형식

언어 규칙의 일반적인 형식은 다음과 같습니다.

`option_name = value:severity`

각 언어 규칙에 대해 이 스타일을 선호하는지 여부 또는 시기를 정의하는 값을 지정합니다. 대부분의 규칙은 `true`(이 스타일 선호) 또는 `false`(이 스타일 선호 안 함) 값을 허용합니다. 다른 규칙은 `when_on_single_line`, `never` 등의 값을 허용합니다. 규칙의 두 번째 부분은 [심각도](#severity-levels)를 지정합니다.

::: moniker range=">=vs-2019"

> [!NOTE]
> 언어 규칙은 분석기에서 적용되므로, 분석기의 기본 구성 구문을 사용하여 심각도를 설정할 수도 있습니다. 구문은 `dotnet_diagnostic.<rule ID>.severity = <severity>` 형식을 사용합니다(예: `dotnet_diagnostic.IDE0040.severity = silent`). 자세한 내용은 [EditorConfig 파일에서 규칙 심각도 설정](../code-quality/use-roslyn-analyzers.md#set-rule-severity-in-an-editorconfig-file)을 참조하세요.

::: moniker-end

## <a name="severity-levels"></a>심각도 수준

언어 규칙 심각도는 해당 스타일을 적용할 수준을 지정합니다. 다음 표에서는 가능한 심각도 값 및 해당 효과를 나열합니다.

심각도 | 효과
:------- | ------
`error` | 이 스타일 규칙을 위반하는 경우 컴파일러 오류가 표시됩니다.
`warning` | 이 스타일 규칙을 위반하는 경우 컴파일러 경고가 표시됩니다.
`suggestion` | 이 스타일 규칙을 위반하는 경우 이를 사용자에게 제안으로 표시합니다. 제안은 처음 두 개의 문자 아래에 세 개의 회색 점으로 표시됩니다.
`silent` | 이 규칙을 위반하는 경우 사용자에게 아무 것도 표시되지 않습니다. 그러나 코드 생성 기능은 이 스타일의 코드를 생성합니다. `silent` 심각도의 규칙은 정리에 참여하고 **빠른 작업 및 리팩터링** 메뉴에 표시됩니다.
`none` | 이 규칙을 위반하는 경우 사용자에게 아무 것도 표시되지 않습니다. 그러나 코드 생성 기능은 이 스타일의 코드를 생성합니다. `none` 심각도의 규칙은 **빠른 작업 및 리팩터링** 메뉴에 나타나지 않습니다. 대부분의 경우 “사용하지 않도록 설정” 또는 “무시”되는 것으로 간주됩니다.

::: moniker range=">=vs-2019"

## <a name="automatically-configure-code-styles"></a>자동으로 코드 스타일 구성

Visual Studio 2019 버전 16.3부터, 스타일 위반이 발생한 후에 [빠른 작업](quick-actions.md) 전구 메뉴에서 코드 스타일 규칙을 구성할 수 있습니다.

코드 스타일 규칙을 변경하려면 다음을 수행합니다.

1. 편집기에서 물결선을 마우스로 가리킨 다음, 표시되는 전구 메뉴를 엽니다. **문제 구성 또는 표시 안 함** >  **\<rule ID> 코드 스타일 구성**을 선택합니다.

   ![Visual Studio의 전구 메뉴에서 코드 스타일 구성](media/vs-2019/configure-code-style.png)

2. 여기서 코드 스타일 옵션 중 하나를 선택합니다.

   ![코드 스타일 설정 구성](media/vs-2019/configure-code-style-setting.png)

   Visual Studio에서 미리 보기 상자에 표시된 것처럼 EditorConfig 파일의 구성 설정을 수정하거나 새로 추가합니다.

코드 스타일 위반의 심각도를 변경하려면 동일한 단계를 수행하되, **\<rule ID> 코드 스타일 구성** 대신 **\<rule ID> 심각도 구성**을 선택합니다. 자세한 내용은 [자동으로 규칙 심각도 구성](../code-quality/use-roslyn-analyzers.md#set-rule-severity-from-the-light-bulb-menu)을 참조하세요.

::: moniker-end

## <a name="net-code-style-settings"></a>.NET 코드 스타일 설정

이 섹션의 스타일 규칙은 C# 및 Visual Basic 모두에 적용됩니다.

- ["This." 및 "Me." 한정자](#this-and-me)
  - dotnet\_style\_qualification\_for_field
  - dotnet\_style\_qualification\_for_property
  - dotnet\_style\_qualification\_for_method
  - dotnet\_style\_qualification\_for_event
- [형식 참조를 위한 프레임워크 형식 이름 대신 언어 키워드](#language-keywords)
  - dotnet\_style\_predefined\_type\_for\_locals\_parameters_members
  - dotnet\_style\_predefined\_type\_for\_member_access
- [한정자 기본 설정](#normalize-modifiers)
  - dotnet\_style\_require\_accessibility_modifiers
  - visual\_basic\_preferred\_modifier_order
  - dotnet\_style\_readonly\_field
- [괄호 기본 설정](#parentheses-preferences)
  - dotnet\_style\_parentheses\_in\_arithmetic\_binary\_operators
  - dotnet\_style\_parentheses\_in\_other\_binary\_operators
  - dotnet\_style\_parentheses\_in\_other\_operators
  - dotnet\_style\_parentheses\_in\_relational\_binary\_operators
- [식 수준 기본 설정](#expression-level-preferences)
  - dotnet\_style\_object_initializer
  - dotnet\_style\_collection_initializer
  - dotnet\_style\_explicit\_tuple_names
  - dotnet\_style\_prefer\_inferred\_tuple_names
  - dotnet\_style\_prefer\_inferred\_anonymous\_type\_member_names
  - dotnet\_style\_prefer\_auto\_properties
  - dotnet\_style\_prefer\_conditional\_expression\_over\_assignment
  - dotnet\_style\_prefer\_conditional\_expression\_over\_return
  - dotnet\_style\_prefer\_compound\_assignment
- ["Null" 검사 기본 설정](#null-checking-preferences)
  - dotnet\_style\_coalesce_expression
  - dotnet\_style\_null_propagation
  - dotnet\_style\_prefer\_is\_null\_check\_over\_reference\_equality\_method

### <a name="this-and-me-qualifiers"></a><a name="this-and-me"></a>"This." 그리고 "Me." 한정자

이 스타일 규칙은 필드, 속성, 메서드 또는 이벤트에 적용할 수 있습니다. 값이 **true**이면 C#에서 `this.` 또는 Visual Basic에서 `Me.`를 코드 기호 앞에 추가하는 것이 좋습니다. 값이 **false**이면 `this.` 또는 `Me.`을 코드 요소 앞에 추가하지 _않는_ 것이 좋습니다.

이러한 규칙은 *.editorconfig* 파일에서 다음과 같이 표시될 수 있습니다.

```ini
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_qualification_for_field = false:suggestion
dotnet_style_qualification_for_property = false:suggestion
dotnet_style_qualification_for_method = false:suggestion
dotnet_style_qualification_for_event = false:suggestion
```

#### <a name="dotnet_style_qualification_for_field"></a>dotnet\_style\_qualification\_for_field

|속성|값|
|-|-|
| **규칙 이름** | dotnet_style_qualification_for_field |
| **규칙 ID** | IDE0003 및 IDE0009 |
| **해당 언어** | C# 및 Visual Basic |
| **값** | `true` - 필드 앞에 `this.`(C#) 또는 `Me.`(Visual Basic) 추가<br /><br />`false` - 필드 앞에 `this.` 또는 `Me.`를 추가하지 ‘않음’ |
| **Visual Studio 기본값** | `false:silent` |

코드 예제:

```csharp
// dotnet_style_qualification_for_field = true
this.capacity = 0;

// dotnet_style_qualification_for_field = false
capacity = 0;
```

```vb
' dotnet_style_qualification_for_field = true
Me.capacity = 0

' dotnet_style_qualification_for_field = false
capacity = 0
```

#### <a name="dotnet_style_qualification_for_property"></a>dotnet\_style\_qualification\_for_property

|속성|값|
|-|-|
| **규칙 이름** | dotnet_style_qualification_for_property |
| **규칙 ID** | IDE0003 및 IDE0009 |
| **해당 언어** | C# 및 Visual Basic |
| **값** | `true` - 속성 앞에 `this.`(C#) 또는 `Me.`(Visual Basic) 추가<br /><br />`false` - 속성 앞에 `this.` 또는 `Me.`를 추가하지 ‘않음’ |
| **Visual Studio 기본값** | `false:silent` |

코드 예제:

```csharp
// dotnet_style_qualification_for_property = true
this.ID = 0;

// dotnet_style_qualification_for_property = false
ID = 0;
```

```vb
' dotnet_style_qualification_for_property = true
Me.ID = 0

' dotnet_style_qualification_for_property = false
ID = 0
```

#### <a name="dotnet_style_qualification_for_method"></a>dotnet\_style\_qualification\_for_method

|속성|값|
|-|-|
| **규칙 이름** | dotnet_style_qualification_for_method |
| **규칙 ID** | IDE0003 및 IDE0009 |
| **해당 언어** | C# 및 Visual Basic |
| **값** | `true` - 메서드 앞에 `this.`(C#) 또는 `Me.`(Visual Basic) 추가<br /><br />`false` - 메서드 앞에 `this.` 또는 `Me.`를 추가하지 ‘않음’ |
| **Visual Studio 기본값** | `false:silent` |

코드 예제:

```csharp
// dotnet_style_qualification_for_method = true
this.Display();

// dotnet_style_qualification_for_method = false
Display();
```

```vb
' dotnet_style_qualification_for_method = true
Me.Display()

' dotnet_style_qualification_for_method = false
Display()
```

#### <a name="dotnet_style_qualification_for_event"></a>dotnet\_style\_qualification\_for_event

|속성|값|
|-|-|
| **규칙 이름** | dotnet_style_qualification_for_event |
| **규칙 ID** | IDE0003 및 IDE0009 |
| **해당 언어** | C# 및 Visual Basic |
| **값** | `true` - 이벤트 앞에 `this.`(C#) 또는 `Me.`(Visual Basic) 추가<br /><br />`false` - 이벤트 앞에 `this.` 또는 `Me.`를 추가하지 ‘않음’ |
| **Visual Studio 기본값** | `false:silent` |

코드 예제:

```csharp
// dotnet_style_qualification_for_event = true
this.Elapsed += Handler;

// dotnet_style_qualification_for_event = false
Elapsed += Handler;
```

```vb
' dotnet_style_qualification_for_event = true
AddHandler Me.Elapsed, AddressOf Handler

' dotnet_style_qualification_for_event = false
AddHandler Elapsed, AddressOf Handler
```

### <a name="language-keywords-instead-of-framework-type-names-for-type-references"></a><a name="language-keywords"></a>형식 참조를 위한 프레임워크 형식 이름 대신 언어 키워드

지역 변수, 메서드 매개 변수 및 클래스 멤버 또는 멤버 액세스 식을 입력할 별도 규칙으로 이 스타일 규칙을 적용할 수 있습니다. 값이 **true**인 경우 자신을 나타내는 키워드를 가진 형식에 형식 이름(예: `Int32`) 대신 언어 키워드(예: `int` 또는 `Integer`)를 사용하는 것이 좋습니다. 값이 **false**인 경우 언어 키워드 대신 형식 이름을 사용하는 것이 좋습니다.

이러한 규칙은 *.editorconfig* 파일에서 다음과 같이 표시될 수 있습니다.

```ini
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_predefined_type_for_locals_parameters_members = true:suggestion
dotnet_style_predefined_type_for_member_access = true:suggestion
```

#### <a name="dotnet_style_predefined_type_for_locals_parameters_members"></a>dotnet\_style\_predefined\_type\_for\_locals\_parameters_members

|속성|값|
|-|-|
| **규칙 이름** | dotnet_style_predefined_type_for_locals_parameters_members |
| **규칙 ID** | IDE0012 및 IDE0014 |
| **해당 언어** | C# 및 Visual Basic |
| **값** | `true` - 자신을 나타내는 키워드가 포함된 형식의 경우, 로컬 변수, 메서드 매개 변수 및 클래스 멤버에 형식 이름 대신 언어 키워드 사용<br /><br />`false` - 로컬 변수, 메서드 매개 변수 및 클래스 멤버에 언어 키워드 대신 형식 이름 사용 |
| **Visual Studio 기본값** | `true:silent` |

코드 예제:

```csharp
// dotnet_style_predefined_type_for_locals_parameters_members = true
private int _member;

// dotnet_style_predefined_type_for_locals_parameters_members = false
private Int32 _member;
```

```vb
' dotnet_style_predefined_type_for_locals_parameters_members = true
Private _member As Integer

' dotnet_style_predefined_type_for_locals_parameters_members = false
Private _member As Int32
```

#### <a name="dotnet_style_predefined_type_for_member_access"></a>dotnet\_style\_predefined\_type\_for\_member_access

|속성|값|
|-|-|
| **규칙 이름** | dotnet_style_predefined_type_for_member_access |
| **규칙 ID** | IDE0013 및 IDE0015 |
| **해당 언어** | C# 및 Visual Basic |
| **값** | `true` - 자신을 나타내는 키워드가 포함된 형식의 경우, 멤버 액세스 식에 형식 이름 대신 언어 키워드 사용<br /><br />`false` - 멤버 액세스 식에 언어 키워드 대신 형식 이름 사용 |
| **Visual Studio 기본값** | `true:silent` |

코드 예제:

```csharp
// dotnet_style_predefined_type_for_member_access = true
var local = int.MaxValue;

// dotnet_style_predefined_type_for_member_access = false
var local = Int32.MaxValue;
```

```vb
' dotnet_style_predefined_type_for_member_access = true
Dim local = Integer.MaxValue

' dotnet_style_predefined_type_for_member_access = false
Dim local = Int32.MaxValue
```

### <a name="modifier-preferences"></a><a name="normalize-modifiers"></a>한정자 기본 설정

이 섹션의 스타일 규칙은 액세스 가능성 한정자 요구, 원하는 한정자 정렬 순서 지정 및 읽기 전용 한정자 요구를 포함한 한정자 기본 설정과 관련이 있습니다.

이러한 규칙은 *.editorconfig* 파일에서 다음과 같이 표시될 수 있습니다.

```ini
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_require_accessibility_modifiers = always:suggestion
dotnet_style_readonly_field = true:warning

# CSharp code style settings:
[*.cs]
csharp_preferred_modifier_order = public,private,protected,internal,static,extern,new,virtual,abstract,sealed,override,readonly,unsafe,volatile,async:suggestion

# Visual Basic code style settings:
[*.vb]
visual_basic_preferred_modifier_order = Partial,Default,Private,Protected,Public,Friend,NotOverridable,Overridable,MustOverride,Overloads,Overrides,MustInherit,NotInheritable,Static,Shared,Shadows,ReadOnly,WriteOnly,Dim,Const,WithEvents,Widening,Narrowing,Custom,Async:suggestion
```

#### <a name="dotnet_style_require_accessibility_modifiers"></a>dotnet\_style\_require\_accessibility_modifiers

|속성|값|
|-|-|
| **규칙 이름** | dotnet_style_require_accessibility_modifiers |
| **규칙 ID** | IDE0040 |
| **해당 언어** | C# 및 Visual Basic |
| **값** | `always` - 접근성 한정자 지정<br /><br />`for_non_interface_members` - 공용 인터페이스 멤버를 제외하고 접근성 한정자 선언 (이는 **always**와 같으며 C#에서 기본 인터페이스의 메서드를 추가할 경우 향후 교정을 위해 추가되었습니다.)<br /><br />`never` - 접근성 한정자 지정 안 함<br /><br />`omit_if_default` - 기본 한정자인 경우를 제외하고 접근성 한정자 지정 |
| **Visual Studio 기본값** | `for_non_interface_members:silent` |
| **도입된 버전** | Visual Studio 2017 15.5 버전 |

코드 예제:

```csharp
// dotnet_style_require_accessibility_modifiers = always
// dotnet_style_require_accessibility_modifiers = for_non_interface_members
class MyClass
{
    private const string thisFieldIsConst = "constant";
}

// dotnet_style_require_accessibility_modifiers = never
class MyClass
{
    const string thisFieldIsConst = "constant";
}
```

#### <a name="csharp_preferred_modifier_order"></a>csharp_preferred_modifier_order

|속성|값|
|-|-|
| **규칙 이름** | csharp_preferred_modifier_order |
| **규칙 ID** | IDE0036 |
| **해당 언어** | C# |
| **값** | `public`, `private`, `protected`와 같은 하나 이상의 C# 한정자입니다. |
| **Visual Studio 기본값** | `public, private, protected, internal, static, extern, new, virtual, abstract, sealed, override, readonly, unsafe, volatile, async:silent` |
| **도입된 버전** | Visual Studio 2017 15.5 버전 |

- 이 규칙이 한정자 목록으로 설정되면 지정된 순서를 선호합니다.
- 이 규칙이 파일에서 생략되면 한정자 순서를 선호하지 않습니다.

코드 예제:

```csharp
// csharp_preferred_modifier_order = public,private,protected,internal,static,extern,new,virtual,abstract,sealed,override,readonly,unsafe,volatile,async
class MyClass
{
    private static readonly int _daysInYear = 365;
}
```

#### <a name="visual_basic_preferred_modifier_order"></a>visual_basic_preferred_modifier_order

|속성|값|
|-|-|
| **규칙 이름** | visual_basic_preferred_modifier_order |
| **규칙 ID** | IDE0036 |
| **해당 언어** | Visual Basic |
| **값** | `Partial`, `Private`, `Public`와 같은 하나 이상의 Visual Basic 한정자입니다. |
| **Visual Studio 기본값** | `Partial, Default, Private, Protected, Public, Friend, NotOverridable, Overridable, MustOverride, Overloads, Overrides, MustInherit, NotInheritable, Static, Shared, Shadows, ReadOnly, WriteOnly, Dim, Const,WithEvents, Widening, Narrowing, Custom, Async:silent` |
| **도입된 버전** | Visual Studio 2017 15.5 버전 |

- 이 규칙이 한정자 목록으로 설정되면 지정된 순서를 선호합니다.
- 이 규칙이 파일에서 생략되면 한정자 순서를 선호하지 않습니다.

코드 예제:

```vb
' visual_basic_preferred_modifier_order = Partial,Default,Private,Protected,Public,Friend,NotOverridable,Overridable,MustOverride,Overloads,Overrides,MustInherit,NotInheritable,Static,Shared,Shadows,ReadOnly,WriteOnly,Dim,Const,WithEvents,Widening,Narrowing,Custom,Async
Public Class MyClass
    Private Shared ReadOnly daysInYear As Int = 365
End Class
```

#### <a name="visual_basic_style_unused_value_expression_statement_preference"></a>visual_basic_style_unused_value_expression_statement_preference

|속성|값|
|-|-|
| **규칙 이름** | visual_basic_style_unused_value_expression_statement_preference |
| **규칙 ID** | IDE0058 |
| **해당 언어** | Visual Basic |
| **값** | `unused_local_variable:silent` |
| **Visual Studio 기본값** | `unused_local_variable:silent` |

코드 예제:

```vb
' visual_basic_style_unused_value_expression_statement_preference = unused_local_variable:silent

Dim unused = Computation()
```

#### <a name="visual_basic_style_unused_value_assignment_preference"></a>visual_basic_style_unused_value_assignment_preference

|속성|값|
|-|-|
| **규칙 이름** | visual_basic_style_unused_value_assignment_preference |
| **규칙 ID** | IDE0059 |
| **해당 언어** | Visual Basic |
| **값** | `unused_local_variable:silent` |
| **Visual Studio 기본값** | `unused_local_variable:silent` |

코드 예제:

```vb
' visual_basic_style_unused_value_assignment_preference = unused_local_variable:suggestion

Dim unused = Computation()
Dim x = 1;
```

#### <a name="dotnet_style_readonly_field"></a>dotnet_style_readonly_field

|속성|값|
|-|-|
| **규칙 이름** | dotnet_style_readonly_field |
| **규칙 ID** | IDE0044 |
| **해당 언어** | C# 및 Visual Basic |
| **값** | `true` - 인라인 또는 생성자 내부에서만 할당되는 경우, `readonly`(C#) 또는 `ReadOnly`(Visual Basic)로 필드를 표시해야 합니다.<br /><br />`false` - `readonly`(C#) 또는 `ReadOnly`(Visual Basic)로 필드를 표시할지 여부에 대한 기본 설정을 지정하지 않습니다. |
| **Visual Studio 기본값** | `true:suggestion` |
| **도입된 버전** | Visual Studio 2017 버전 15.7 |

코드 예제:

```csharp
// dotnet_style_readonly_field = true
class MyClass
{
    private readonly int _daysInYear = 365;
}
```

```vb
' dotnet_style_readonly_field = true
Public Class MyClass
    Private ReadOnly daysInYear As Int = 365
End Class
```

### <a name="parentheses-preferences"></a>괄호 기본 설정

이 섹션의 스타일 규칙은 산술, 관계형 및 기타 이진 연산자의 괄호 사용을 비롯한 괄호 기본 설정과 관련이 있습니다.

이러한 규칙은 *.editorconfig* 파일에서 다음과 같이 표시될 수 있습니다.

```ini
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_parentheses_in_arithmetic_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_relational_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_other_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_other_operators = never_if_unnecessary:silent
```

#### <a name="dotnet_style_parentheses_in_arithmetic_binary_operators"></a>dotnet\_style\_parentheses\_in\_arithmetic\_binary_operators

|속성|값|
|-|-|
| **규칙 이름** | dotnet_style_parentheses_in_arithmetic_binary_operators |
| **규칙 ID** | IDE0047 |
| **해당 언어** | C# 및 Visual Basic |
| **값** | `always_for_clarity` - 산술 연산자(`*`, `/`, `%`, `+`, `-`, `<<`, `>>`, `&`, `^`, `|`) 우선 순위를 명확하게 나타내기 위해 괄호를 사용합니다.<br /><br />`never_if_unnecessary` - 산술 연산자(`*`, `/`, `%`, `+`, `-`, `<<`, `>>`, `&`, `^`, `|`) 우선 순위가 명확하면 괄호를 사용하지 않습니다. |
| **Visual Studio 기본값** | `always_for_clarity:silent` |
| **도입된 버전** | Visual Studio 2017 버전 15.8 |

코드 예제:

```csharp
// dotnet_style_parentheses_in_arithmetic_binary_operators = always_for_clarity
var v = a + (b * c);

// dotnet_style_parentheses_in_arithmetic_binary_operators = never_if_unnecessary
var v = a + b * c;
```

```vb
' dotnet_style_parentheses_in_arithmetic_binary_operators = always_for_clarity
Dim v = a + (b * c)

' dotnet_style_parentheses_in_arithmetic_binary_operators = never_if_unnecessary
Dim v = a + b * c
```

#### <a name="dotnet_style_parentheses_in_relational_binary_operators"></a>dotnet\_style\_parentheses\_in\_relational\_binary_operators

|속성|값|
|-|-|
| **규칙 이름** | dotnet_style_parentheses_in_relational_binary_operators |
| **규칙 ID** | IDE0047 |
| **해당 언어** | C# 및 Visual Basic |
| **값** | `always_for_clarity` - 관계 연산자(`>`, `<`, `<=`, `>=`, `is`, `as`, `==`, `!=`) 우선 순위를 명확하게 나타내기 위해 괄호를 사용합니다.<br /><br />`never_if_unnecessary` - 관계 연산자(`>`, `<`, `<=`, `>=`, `is`, `as`, `==`, `!=`) 우선 순위가 명확하면 괄호를 사용하지 않습니다. |
| **Visual Studio 기본값** | `always_for_clarity:silent` |
| **도입된 버전** | Visual Studio 2017 버전 15.8 |

코드 예제:

```csharp
// dotnet_style_parentheses_in_relational_binary_operators = always_for_clarity
var v = (a < b) == (c > d);

// dotnet_style_parentheses_in_relational_binary_operators = never_if_unnecessary
var v = a < b == c > d;
```

```vb
' dotnet_style_parentheses_in_relational_binary_operators = always_for_clarity
Dim v = (a < b) = (c > d)

' dotnet_style_parentheses_in_relational_binary_operators = never_if_unnecessary
Dim v = a < b = c > d
```

#### <a name="dotnet_style_parentheses_in_other_binary_operators"></a>dotnet\_style\_parentheses\_in\_other\_binary_operators

|속성|값|
|-|-|
| **규칙 이름** | dotnet_style_parentheses_in_other_binary_operators |
| **규칙 ID** | IDE0047 |
| **해당 언어** | C# 및 Visual Basic |
| **값** | `always_for_clarity` - 기타 이항 연산자(`&&`, `||`, `??`) 우선 순위를 명확하게 나타내기 위해 괄호를 사용합니다.<br /><br />`never_if_unnecessary` - 기타 이항 연산자(`&&`, `||`, `??`) 우선 순위가 명확하면 괄호를 사용하지 않습니다. |
| **Visual Studio 기본값** | `always_for_clarity:silent` |
| **도입된 버전** | Visual Studio 2017 버전 15.8 |

코드 예제:

```csharp
// dotnet_style_parentheses_in_other_binary_operators = always_for_clarity
var v = a || (b && c);

// dotnet_style_parentheses_in_other_binary_operators = never_if_unnecessary
var v = a || b && c;
```

```vb
' dotnet_style_parentheses_in_other_binary_operators = always_for_clarity
Dim v = a OrElse (b AndAlso c)

' dotnet_style_parentheses_in_other_binary_operators = never_if_unnecessary
Dim v = a OrElse b AndAlso c
```

#### <a name="dotnet_style_parentheses_in_other_operators"></a>dotnet\_style\_parentheses\_in\_other_operators

|속성|값|
|-|-|
| **규칙 이름** | dotnet_style_parentheses_in_other_operators |
| **규칙 ID** | IDE0047 |
| **해당 언어** | C# 및 Visual Basic |
| **값** | `always_for_clarity` - 연산자 우선 순위를 명확하게 나타내기 위해 괄호를 사용합니다.<br /><br />`never_if_unnecessary` - 연산자 우선 순위가 명확하면 괄호를 사용하지 않습니다. |
| **Visual Studio 기본값** | `never_if_unnecessary:silent` |
| **도입된 버전** | Visual Studio 2017 버전 15.8 |

코드 예제:

```csharp
// dotnet_style_parentheses_in_other_operators = always_for_clarity
var v = (a.b).Length;

// dotnet_style_parentheses_in_other_operators = never_if_unnecessary
var v = a.b.Length;
```

```vb
' dotnet_style_parentheses_in_other_operators = always_for_clarity
Dim v = (a.b).Length

' dotnet_style_parentheses_in_other_operators = never_if_unnecessary
Dim v = a.b.Length
```

### <a name="expression-level-preferences"></a>식 수준 기본 설정

이 섹션의 스타일 규칙은 개체 이니셜라이저, 컬렉션 이니셜라이저, 명시적 또는 유추된 튜플 이름 및 유추된 익명의 형식을 사용하는 식 수준 기본 설정에 대해 다룹니다.

이러한 규칙은 *.editorconfig* 파일에서 다음과 같이 표시될 수 있습니다.

```ini
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_object_initializer = true:suggestion
dotnet_style_collection_initializer = true:suggestion
dotnet_style_explicit_tuple_names = true:suggestion
dotnet_style_prefer_inferred_tuple_names = true:suggestion
dotnet_style_prefer_inferred_anonymous_type_member_names = true:suggestion
dotnet_style_prefer_auto_properties = true:silent
dotnet_style_prefer_conditional_expression_over_assignment = true:suggestion
dotnet_style_prefer_conditional_expression_over_return = true:suggestion
dotnet_style_prefer_compound_assignment = true:suggestion
```

#### <a name="dotnet_style_object_initializer"></a>dotnet\_style\_object_initializer

|속성|값|
|-|-|
| **규칙 이름** | dotnet_style_object_initializer |
| **규칙 ID** | IDE0017 |
| **해당 언어** | C# 및 Visual Basic |
| **값** | `true` - 가능한 경우 개체 이니셜라이저를 사용하여 개체를 초기화합니다.<br /><br />`false` - 개체 이니셜라이저를 사용하여 개체를 초기화하지 ‘않습니다’. |
| **Visual Studio 기본값** | `true:suggestion` |

코드 예제:

```csharp
// dotnet_style_object_initializer = true
var c = new Customer() { Age = 21 };

// dotnet_style_object_initializer = false
var c = new Customer();
c.Age = 21;
```

```vb
' dotnet_style_object_initializer = true
Dim c = New Customer() With {.Age = 21}

' dotnet_style_object_initializer = false
Dim c = New Customer()
c.Age = 21
```

#### <a name="dotnet_style_collection_initializer"></a>dotnet\_style\_collection_initializer

|속성|값|
|-|-|
| **규칙 이름** | dotnet_style_collection_initializer |
| **규칙 ID** | IDE0028 |
| **해당 언어** | C# 및 Visual Basic |
| **값** | `true` - 가능한 경우 컬렉션 이니셜라이저를 사용하여 컬렉션을 초기화합니다.<br /><br />`false` - 컬렉션 이니셜라이저를 사용하여 컬렉션을 초기화하지 ‘않습니다’. |
| **Visual Studio 기본값** | `true:suggestion` |

코드 예제:

```csharp
// dotnet_style_collection_initializer = true
var list = new List<int> { 1, 2, 3 };

// dotnet_style_collection_initializer = false
var list = new List<int>();
list.Add(1);
list.Add(2);
list.Add(3);
```

```vb
' dotnet_style_collection_initializer = true
Dim list = New List(Of Integer) From {1, 2, 3}

' dotnet_style_collection_initializer = false
Dim list = New List(Of Integer)
list.Add(1)
list.Add(2)
list.Add(3)
```

#### <a name="dotnet_style_explicit_tuple_names"></a>dotnet\_style\_explicit\_tuple_names

|속성|값|
|-|-|
| **규칙 이름** | dotnet_style_explicit_tuple_names |
| **규칙 ID** | IDE0033 |
| **해당 언어** | C# 7.0+ 및 Visual Basic 15+ |
| **값** | `true` - ItemX 속성보다 튜플 이름을 선호합니다.<br /><br />`false` - 튜플 이름보다 ItemX 속성을 선호합니다. |
| **Visual Studio 기본값** | `true:suggestion` |

코드 예제:

```csharp
// dotnet_style_explicit_tuple_names = true
(string name, int age) customer = GetCustomer();
var name = customer.name;

// dotnet_style_explicit_tuple_names = false
(string name, int age) customer = GetCustomer();
var name = customer.Item1;
```

```vb
 ' dotnet_style_explicit_tuple_names = true
Dim customer As (name As String, age As Integer) = GetCustomer()
Dim name = customer.name

' dotnet_style_explicit_tuple_names = false
Dim customer As (name As String, age As Integer) = GetCustomer()
Dim name = customer.Item1
```

#### <a name="dotnet_style_prefer_inferred_tuple_names"></a>dotnet\_style\_prefer\_inferred\_tuple_names

|속성|값|
|-|-|
| **규칙 이름** | dotnet_style_prefer_inferred_tuple_names |
| **규칙 ID** | IDE0037 |
| **해당 언어** | C# 7.1+ 및 Visual Basic 15+ |
| **값** | `true` - 유추된 튜플 요소 이름을 선호합니다.<br /><br />`false` - 명시적 튜플 요소 이름을 선호합니다. |
| **Visual Studio 기본값** | `true:suggestion` |
| **도입된 버전** | Visual Studio 2017 버전 15.6 |

코드 예제:

```csharp
// dotnet_style_prefer_inferred_tuple_names = true
var tuple = (age, name);

// dotnet_style_prefer_inferred_tuple_names = false
var tuple = (age: age, name: name);
```

```vb
' dotnet_style_prefer_inferred_tuple_names = true
Dim tuple = (name, age)

' dotnet_style_prefer_inferred_tuple_names = false
Dim tuple = (name:=name, age:=age)
```

#### <a name="dotnet_style_prefer_inferred_anonymous_type_member_names"></a>dotnet\_style\_prefer\_inferred\_anonymous\_type\_member_names

|속성|값|
|-|-|
| **규칙 이름** | dotnet_style_prefer_inferred_anonymous_type_member_names |
| **규칙 ID** | IDE0037 |
| **해당 언어** | C# 및 Visual Basic |
| **값** | `true` - 유추된 무명 형식 멤버 이름을 선호합니다.<br /><br />`false` - 명시적 무명 형식 멤버 이름을 선호합니다. |
| **Visual Studio 기본값** | `true:suggestion` |
| **도입된 버전** | Visual Studio 2017 버전 15.6 |

코드 예제:

```csharp
// dotnet_style_prefer_inferred_anonymous_type_member_names = true
var anon = new { age, name };

// dotnet_style_prefer_inferred_anonymous_type_member_names = false
var anon = new { age = age, name = name };
```

```vb
' dotnet_style_prefer_inferred_anonymous_type_member_names = true
Dim anon = New With {name, age}

' dotnet_style_prefer_inferred_anonymous_type_member_names = false
Dim anon = New With {.name = name, .age = age}
```

#### <a name="dotnet_style_prefer_auto_properties"></a>dotnet\_style\_prefer\_auto\_properties

|속성|값|
|-|-|
| **규칙 이름** | dotnet_style_prefer_auto_properties |
| **규칙 ID** | IDE0032 |
| **해당 언어** | C# 및 Visual Basic |
| **값** | `true` - 프라이빗 지원 필드가 있는 속성보다 자동 속성을 선호합니다.<br /><br />`false` - 자동 속성보다 프라이빗 지원 필드가 있는 속성을 선호합니다. |
| **Visual Studio 기본값** | `true:suggestion` |
| **도입된 버전** | Visual Studio 2017 버전 15.7 |

코드 예제:

```csharp
// dotnet_style_prefer_auto_properties = true
private int Age { get; }

// dotnet_style_prefer_auto_properties = false
private int age;

public int Age
{
    get
    {
        return age;
    }
}
```

```vb
' dotnet_style_prefer_auto_properties = true
Public ReadOnly Property Age As Integer

' dotnet_style_prefer_auto_properties = false
Private _age As Integer

Public ReadOnly Property Age As Integer
    Get
        return _age
    End Get
End Property
```

#### <a name="dotnet_style_prefer_is_null_check_over_reference_equality_method"></a>dotnet\_style\_prefer\_is\_null\_check\_over\_reference\_equality\_method

|속성|값|
|-|-|
| **규칙 이름** | dotnet_style_prefer_is_null_check_over_reference_equality_method |
| **규칙 ID** | IDE0041 |
| **해당 언어** | C# 및 Visual Basic |
| **값** | `true` - `object.ReferenceEquals`보다 패턴 일치를 사용한 null 검사를 선호합니다.<br /><br />`false` - 패턴 일치를 사용한 null 검사보다 `object.ReferenceEquals`를 선호합니다. |
| **Visual Studio 기본값** | `true:suggestion` |
| **도입된 버전** | Visual Studio 2017 버전 15.7 |

코드 예제:

```csharp
// dotnet_style_prefer_is_null_check_over_reference_equality_method = true
if (value is null)
    return;

// dotnet_style_prefer_is_null_check_over_reference_equality_method = false
if (object.ReferenceEquals(value, null))
    return;
```

```vb
' dotnet_style_prefer_is_null_check_over_reference_equality_method = true
If value Is Nothing
    Return
End If

' dotnet_style_prefer_is_null_check_over_reference_equality_method = false
If Object.ReferenceEquals(value, Nothing)
    Return
End If
```

#### <a name="dotnet_style_prefer_conditional_expression_over_assignment"></a>dotnet\_style\_prefer\_conditional\_expression\_over_assignment

|속성|값|
|-|-|
| **규칙 이름** | dotnet_style_prefer_conditional_expression_over_assignment |
| **규칙 ID** | IDE0045 |
| **해당 언어** | C# 및 Visual Basic |
| **값** | `true` - if-else 문보다 3개로 구성된 조건을 사용한 할당을 선호합니다.<br /><br />`false` - 3개로 구성된 조건보다 if-else 문을 사용한 할당을 선호합니다. |
| **Visual Studio 기본값** | `true:suggestion` |
| **도입된 버전** | Visual Studio 2017 버전 15.8 |

코드 예제:

```csharp
// dotnet_style_prefer_conditional_expression_over_assignment = true
string s = expr ? "hello" : "world";

// dotnet_style_prefer_conditional_expression_over_assignment = false
string s;
if (expr)
{
    s = "hello";
}
else
{
    s = "world";
}
```

```vb
' dotnet_style_prefer_conditional_expression_over_assignment = true
Dim s As String = If(expr, "hello", "world")

' dotnet_style_prefer_conditional_expression_over_assignment = false
Dim s As String
If expr Then
    s = "hello"
Else
    s = "world"
End If
```

#### <a name="dotnet_style_prefer_conditional_expression_over_return"></a>dotnet\_style\_prefer\_conditional\_expression\_over_return

|속성|값|
|-|-|
| **규칙 이름** | dotnet_style_prefer_conditional_expression_over_return |
| **규칙 ID** | IDE0046 |
| **해당 언어** | C# 및 Visual Basic |
| **값** | `true` - 반환 문에 if-else 문보다 3개로 구성된 조건을 사용합니다.<br /><br />`false` - 반환 문에 3개로 구성된 조건보다 if-else 문을 사용합니다. |
| **Visual Studio 기본값** | `true:suggestion` |
| **도입된 버전** | Visual Studio 2017 버전 15.8 |

코드 예제:

```csharp
// dotnet_style_prefer_conditional_expression_over_return = true
return expr ? "hello" : "world"

// dotnet_style_prefer_conditional_expression_over_return = false
if (expr)
{
    return "hello";
}
else
{
    return "world";
}
```

```vb
' dotnet_style_prefer_conditional_expression_over_return = true
Return If(expr, "hello", "world")

' dotnet_style_prefer_conditional_expression_over_return = false
If expr Then
    Return "hello"
Else
    Return "world"
End If
```

#### <a name="dotnet_style_prefer_compound_assignment"></a>dotnet\_style\_prefer\_compound\_assignment

|속성|값|
|-|-|
| **규칙 이름** | dotnet_style_prefer_compound_assignment |
| **규칙 ID** | IDE0054 |
| **해당 언어** | C# 및 Visual Basic |
| **값** | `true` - [복합 할당](/dotnet/csharp/language-reference/operators/assignment-operator#compound-assignment) 식을 선호합니다.<br /><br />`false` - 복합 할당 식을 선호하지 않습니다. |
| **Visual Studio 기본값** | `true:suggestion` |

코드 예제:

```csharp
// dotnet_style_prefer_compound_assignment = true
x += 1;

// dotnet_style_prefer_compound_assignment = false
x = x + 1;
```

```vb
' dotnet_style_prefer_compound_assignment = true
x += 1

' dotnet_style_prefer_compound_assignment = false
x = x + 1
```

### <a name="null-checking-preferences"></a>Null 검사 기본 설정

이 섹션에서 스타일 규칙은 Null 검사 기본 설정과 관련이 있습니다.

이러한 규칙은 *.editorconfig* 파일에서 다음과 같이 표시될 수 있습니다.

```ini
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_coalesce_expression = true:suggestion
dotnet_style_null_propagation = true:suggestion
dotnet_style_prefer_is_null_check_over_reference_equality_method = true:silent
```

#### <a name="dotnet_style_coalesce_expression"></a>dotnet\_style\_coalesce_expression

|속성|값|
|-|-|
| **규칙 이름** | dotnet_style_coalesce_expression |
| **규칙 ID** | IDE0029 |
| **해당 언어** | C# 및 Visual Basic |
| **값** | `true` - 3개로 구성된 연산자 검사보다 null 병합 식을 선호합니다.<br /><br />`false` - null 병합 식보다 3개로 구성된 연산자 검사를 선호합니다. |
| **Visual Studio 기본값** | `true:suggestion` |

코드 예제:

```csharp
// dotnet_style_coalesce_expression = true
var v = x ?? y;

// dotnet_style_coalesce_expression = false
var v = x != null ? x : y; // or
var v = x == null ? y : x;
```

```vb
' dotnet_style_coalesce_expression = true
Dim v = If(x, y)

' dotnet_style_coalesce_expression = false
Dim v = If(x Is Nothing, y, x) ' or
Dim v = If(x IsNot Nothing, x, y)
```

#### <a name="dotnet_style_null_propagation"></a>dotnet\_style\_null_propagation

|속성|값|
|-|-|
| **규칙 이름** | dotnet_style_null_propagation |
| **규칙 ID** | IDE0031 |
| **해당 언어** | C# 6.0 이상 및 Visual Basic 14 이상 |
| **값** | `true` - 가능한 경우 null 조건 연산자를 사용합니다.<br /><br />`false` - 가능한 경우 3개로 구성된 null 검사를 사용합니다. |
| **Visual Studio 기본값** | `true:suggestion` |

코드 예제:

```csharp
// dotnet_style_null_propagation = true
var v = o?.ToString();

// dotnet_style_null_propagation = false
var v = o == null ? null : o.ToString(); // or
var v = o != null ? o.String() : null;
```

```vb
' dotnet_style_null_propagation = true
Dim v = o?.ToString()

' dotnet_style_null_propagation = false
Dim v = If(o Is Nothing, Nothing, o.ToString()) ' or
Dim v = If(o IsNot Nothing, o.ToString(), Nothing)
```

### <a name="dotnet_style_prefer_is_null_check_over_reference_equality_method"></a>dotnet\_style\_prefer\_is\_null\_check\_over\_reference\_equality\_method

|속성|값|
|-|-|
| **규칙 이름** | dotnet_style_prefer_is_null_check_over_reference_equality_method |
| **규칙 ID** | IDE0041 |
| **해당 언어** | C# 6.0 이상 및 Visual Basic 14 이상 |
| **값** | `true` - 참조 같음 메서드보다 is null 검사를 선호함<br /><br />`false` - is null 검사보다 참조 같음 메서드를 선호함 |
| **Visual Studio 기본값** | `true:silent` |

코드 예제:

```csharp
// dotnet_style_prefer_is_null_check_over_reference_equality_method = true
if (value is null)
    return;

// dotnet_style_prefer_is_null_check_over_reference_equality_method = false
if (object.ReferenceEquals(value, null))
    return;
```

```vb
' dotnet_style_prefer_is_null_check_over_reference_equality_method = true
If value Is Nothing
    Return
End If

' dotnet_style_prefer_is_null_check_over_reference_equality_method = false
If Object.ReferenceEquals(value, Nothing)
    Return
End If
```

## <a name="net-code-quality-settings"></a>.NET 코드 품질 설정

이 섹션의 품질 규칙은 C# 및 Visual Basic 코드 모두에 적용됩니다. 해당 규칙은 Visual Studio IDE(통합 개발 환경)에 기본 제공되는 코드 분석기를 구성하는 데 사용됩니다. EditorConfig 파일을 사용한 FxCop 분석 프로그램 구성에 대해서는, [FxCop 분석기 구성](../code-quality/configure-fxcop-analyzers.md)을 참조하세요.

- [매개 변수 기본 설정](#parameter-preferences)
  - dotnet\_code\_quality\_unused\_parameters

### <a name="parameter-preferences"></a>매개 변수 기본 설정

이 섹션의 품질 규칙에서는 메서드 매개 변수를 고려합니다.

이러한 규칙은 *.editorconfig* 파일에서 다음과 같이 표시될 수 있습니다.

```ini
# CSharp and Visual Basic code quality settings:
[*.{cs,vb}]
dotnet_code_quality_unused_parameters = all:suggestion
```

#### <a name="dotnet_code_quality_unused_parameters"></a>dotnet\_code\_quality\_unused\_parameters

|속성|값|
|-|-|
| **규칙 이름** | dotnet_code_quality_unused_parameters |
| **규칙 ID** | IDE0060 |
| **해당 언어** | C# 및 Visual Basic |
| **값** | `all` - 사용되지 않는 매개 변수가 포함된 모든 액세스 가능성의 메서드를 플래그 지정합니다.<br /><br />`non_public` - 사용되지 않는 매개 변수가 포함된 비공용 메서드만 플래그 지정합니다. |
| **Visual Studio 기본값** | `all:suggestion` |

코드 예제:

```csharp
// dotnet_code_quality_unused_parameters = all:suggestion
public int GetNum() { return 1; }

// dotnet_code_quality_unused_parameters = non_public:suggestion
public int GetNum(int arg1) { return 1; }
```

```vb
' dotnet_code_quality_unused_parameters = all:suggestion
Public Function GetNum()
    Return 1
End Function

' dotnet_code_quality_unused_parameters = non_public:suggestion
Public Function GetNum(arg1 As Integer)
    Return 1
End Function
```

## <a name="c-code-style-settings"></a>C# 코드 스타일 설정

이 섹션의 스타일 규칙은 C#에만 적용됩니다.

- [암시적 및 명시적 형식](#implicit-and-explicit-types)
  - csharp\_style\_var\_for\_built\_in_types
  - csharp\_style\_var\_when\_type\_is_apparent
  - csharp\_style\_var_elsewhere
- [식 본문 멤버](#expression-bodied-members)
  - csharp\_style\_expression\_bodied_methods
  - csharp\_style\_expression\_bodied_constructors
  - csharp\_style\_expression\_bodied_operators
  - csharp\_style\_expression\_bodied_properties
  - csharp\_style\_expression\_bodied_indexers
  - csharp\_style\_expression\_bodied_accessors
  - csharp\_style\_expression\_bodied_lambdas
  - csharp\_style\_expression\_bodied\_local_functions
- [패턴 일치](#pattern-matching)
  - csharp\_style\_pattern\_matching\_over\_is\_with\_cast_check
  - csharp\_style\_pattern\_matching\_over\_as\_with\_null_check
- [인라인 변수 선언](#inlined-variable-declarations)
  - csharp\_style\_inlined\_variable_declaration
- [식 수준 기본 설정](#c-expression-level-preferences)
  - csharp\_prefer\_simple\_default_expression
- ["Null" 검사 기본 설정](#c-null-checking-preferences)
  - csharp\_style\_throw_expression
  - csharp\_style\_conditional\_delegate_call
- [한정자 기본 설정](#normalize-modifiers)
  - csharp\_preferred\_modifier_order
- [코드 블록 기본 설정](#code-block-preferences)
  - csharp\_prefer_braces
- [사용되지 않는 값 기본 설정](#unused-value-preferences)
  - csharp\_style\_unused\_value\_expression\_statement_preference
  - csharp\_style\_unused\_value\_assignment_preference
- [인덱스 및 범위 기본 설정](#index-and-range-preferences)
  - csharp\_style\_prefer\_index_operator
  - csharp\_style\_prefer\_range_operator
- [기타 기본 설정](#miscellaneous-preferences)
  - csharp\_style\_deconstructed\_variable_declaration
  - csharp\_style\_pattern\_local\_over\_anonymous_function
  - csharp\_using\_directive\_placement
  - csharp\_prefer\_static\_local_function
  - csharp\_prefer\_simple\_using_statement
  - csharp\_style\_prefer\_switch_expression

### <a name="implicit-and-explicit-types"></a>암시적 및 명시적 형식

이 섹션의 스타일 규칙은 [var](/dotnet/csharp/language-reference/keywords/var) 키워드 및 변수 선언에서 명시적 형식을 사용하는 방법을 다룹니다. 이 규칙은 형식이 명확할 때 기본 제공 형식 및 다른 위치에 개별적으로 적용할 수 있습니다.

예제 *.editorconfig* 파일:

```ini
# CSharp code style settings:
[*.cs]
csharp_style_var_for_built_in_types = true:suggestion
csharp_style_var_when_type_is_apparent = true:suggestion
csharp_style_var_elsewhere = true:suggestion
```

#### <a name="csharp_style_var_for_built_in_types"></a>csharp\_style\_var\_for\_built\_in_types

|속성|값|
|-|-|
| **규칙 이름** | csharp_style_var_for_built_in_types |
| **규칙 ID** | IDE0007 및 IDE0008 |
| **해당 언어** | C#  |
| **값** | `true` - `int` 등의 기본 제공 시스템 형식을 사용한 변수 선언에 `var`을 사용합니다.<br /><br />`false` - `int` 등의 기본 제공 시스템 형식을 사용한 변수 선언에 `var`보다 명시적 형식을 선호합니다. |
| **Visual Studio 기본값** | `true:silent` |

코드 예제:

```csharp
// csharp_style_var_for_built_in_types = true
var x = 5;

// csharp_style_var_for_built_in_types = false
int x = 5;
```

#### <a name="csharp_style_var_when_type_is_apparent"></a>csharp\_style\_var\_when\_type\_is_apparent

|속성|값|
|-|-|
| **규칙 이름** | csharp_style_var_when_type_is_apparent |
| **규칙 ID** | IDE0007 및 IDE0008 |
| **해당 언어** | C#  |
| **값** | `true` - 선언 식의 오른쪽에서 형식이 이미 언급된 경우 `var`을 선호합니다.<br /><br />`false` - 선언 식의 오른쪽에서 형식이 이미 언급된 경우 `var`보다 명시적 형식을 선호합니다. |
| **Visual Studio 기본값** | `true:silent` |

코드 예제:

```csharp
// csharp_style_var_when_type_is_apparent = true
var obj = new Customer();

// csharp_style_var_when_type_is_apparent = false
Customer obj = new Customer();
```

#### <a name="csharp_style_var_elsewhere"></a>csharp\_style\_var_elsewhere

|속성|값|
|-|-|
| **규칙 이름** | csharp_style_var_elsewhere |
| **규칙 ID** | IDE0007 및 IDE0008 |
| **해당 언어** | C#  |
| **값** | `true` - 다른 코드 스타일 규칙으로 재정의되지 않은 경우 항상 명시적 형식보다 `var`을 선호합니다.<br /><br />`false` - 다른 코드 스타일 규칙으로 재정의되지 않은 경우 항상 `var`보다 명시적 형식을 선호합니다. |
| **Visual Studio 기본값** | `true:silent` |

코드 예제:

```csharp
// csharp_style_var_elsewhere = true
var f = this.Init();

// csharp_style_var_elsewhere = false
bool f = this.Init();
```

### <a name="expression-bodied-members"></a>식 본문 멤버

이 섹션의 스타일 규칙은 논리가 단일 식으로 구성되는 경우 [식 본문 멤버](/dotnet/csharp/programming-guide/statements-expressions-operators/expression-bodied-members)를 사용하는 방법을 다룹니다. 이 규칙은 메서드, 생성자, 연산자, 속성, 인덱서 및 접근자에 적용할 수 있습니다.

예제 *.editorconfig* 파일:

```ini
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_methods = false:silent
csharp_style_expression_bodied_constructors = false:silent
csharp_style_expression_bodied_operators = false:silent
csharp_style_expression_bodied_properties = true:suggestion
csharp_style_expression_bodied_indexers = true:suggestion
csharp_style_expression_bodied_accessors = true:suggestion
csharp_style_expression_bodied_lambdas = true:silent
csharp_style_expression_bodied_local_functions = false:silent
```

#### <a name="csharp_style_expression_bodied_methods"></a>csharp\_style\_expression\_bodied_methods

|속성|값|
|-|-|
| **규칙 이름** | csharp_style_expression_bodied_methods |
| **규칙 ID** | IDE0022 |
| **해당 언어** | C# 6.0+  |
| **값** | `true` - 메서드에 식 본문을 사용합니다.<br /><br />`when_on_single_line` - 한 줄이 되는 경우 메서드에 식 본문을 사용합니다.<br /><br />`false` - 메서드에 블록 본문을 사용합니다. |
| **Visual Studio 기본값** | `false:silent` |

코드 예제:

```csharp
// csharp_style_expression_bodied_methods = true
public int GetAge() => this.Age;

// csharp_style_expression_bodied_methods = false
public int GetAge() { return this.Age; }
```

#### <a name="csharp_style_expression_bodied_constructors"></a>csharp\_style\_expression\_bodied_constructors

|속성|값|
|-|-|
| **규칙 이름** | csharp_style_expression_bodied_constructors |
| **규칙 ID** | IDE0021 |
| **해당 언어** | C# 7.0+ |
| **값** | `true` - 생성자에 식 본문을 사용합니다.<br /><br />`when_on_single_line` - 한 줄이 되는 경우 생성자에 식 본문을 사용합니다.<br /><br />`false` - 생성자에 블록 본문을 사용합니다. |
| **Visual Studio 기본값** | `false:silent` |

코드 예제:

```csharp
// csharp_style_expression_bodied_constructors = true
public Customer(int age) => Age = age;

// csharp_style_expression_bodied_constructors = false
public Customer(int age) { Age = age; }
```

#### <a name="csharp_style_expression_bodied_operators"></a>csharp\_style\_expression\_bodied_operators

|속성|값|
|-|-|
| **규칙 이름** | csharp_style_expression_bodied_operators |
| **규칙 ID** | IDE0023 및 IDE0024 |
| **해당 언어** | C# 7.0+ |
| **값** | `true` - 연산자에 식 본문을 사용합니다.<br /><br />`when_on_single_line` - 한 줄이 되는 경우 연산자에 식 본문을 사용합니다.<br /><br />`false` - 연산자에 블록 본문을 사용합니다. |
| **Visual Studio 기본값** | `false:silent` |

코드 예제:

```csharp
// csharp_style_expression_bodied_operators = true
public static ComplexNumber operator + (ComplexNumber c1, ComplexNumber c2)
    => new ComplexNumber(c1.Real + c2.Real, c1.Imaginary + c2.Imaginary);

// csharp_style_expression_bodied_operators = false
public static ComplexNumber operator + (ComplexNumber c1, ComplexNumber c2)
{ return new ComplexNumber(c1.Real + c2.Real, c1.Imaginary + c2.Imaginary); }
```

#### <a name="csharp_style_expression_bodied_properties"></a>csharp\_style\_expression\_bodied_properties

|속성|값|
|-|-|
| **규칙 이름** | csharp_style_expression_bodied_properties |
| **규칙 ID** | IDE0025 |
| **해당 언어** | C# 7.0+ |
| **값** | `true` - 속성에 식 본문을 사용합니다.<br /><br />`when_on_single_line` - 한 줄이 되는 경우 속성에 식 본문을 사용합니다.<br /><br />`false` - 속성에 블록 본문을 사용합니다. |
| **Visual Studio 기본값** | `true:silent` |

코드 예제:

```csharp
// csharp_style_expression_bodied_properties = true
public int Age => _age;

// csharp_style_expression_bodied_properties = false
public int Age { get { return _age; }}
```

#### <a name="csharp_style_expression_bodied_indexers"></a>csharp\_style\_expression\_bodied_indexers

|속성|값|
|-|-|
| **규칙 이름** | csharp_style_expression_bodied_indexers |
| **규칙 ID** | IDE0026 |
| **해당 언어** | C# 7.0+ |
| **값** | `true` - 인덱서에 식 본문을 사용합니다.<br /><br />`when_on_single_line` - 한 줄이 되는 경우 인덱서에 식 본문을 사용합니다.<br /><br />`false` - 인덱서에 블록 본문을 사용합니다. |
| **Visual Studio 기본값** | `true:silent` |

코드 예제:

```csharp
// csharp_style_expression_bodied_indexers = true
public T this[int i] => _values[i];

// csharp_style_expression_bodied_indexers = false
public T this[int i] { get { return _values[i]; } }
```

#### <a name="csharp_style_expression_bodied_accessors"></a>csharp\_style\_expression\_bodied_accessors

|속성|값|
|-|-|
| **규칙 이름** | csharp_style_expression_bodied_accessors |
| **규칙 ID** | IDE0027 |
| **해당 언어** | C# 7.0+ |
| **값** | `true` - 접근자에 식 본문을 사용합니다.<br /><br />`when_on_single_line` - 한 줄이 되는 경우 접근자에 식 본문을 사용합니다.<br /><br />`false` - 접근자에 블록 본문을 사용합니다. |
| **Visual Studio 기본값** | `true:silent` |

코드 예제:

```csharp
// csharp_style_expression_bodied_accessors = true
public int Age { get => _age; set => _age = value; }

// csharp_style_expression_bodied_accessors = false
public int Age { get { return _age; } set { _age = value; } }
```

#### <a name="csharp_style_expression_bodied_lambdas"></a>csharp\_style\_expression\_bodied_lambdas

|속성|값|
|-|-|
| **규칙 이름** | csharp_style_expression_bodied_lambdas |
| **규칙 ID** | IDE0053 |
| **값** | `true` - 람다에 식 본문을 사용합니다.<br /><br />`when_on_single_line` - 한 줄이 되는 경우 람다에 식 본문을 사용합니다.<br /><br />`false` - 람다에 블록 본문을 사용합니다. |
| **Visual Studio 기본값** | `true:silent` |

코드 예제:

```csharp
// csharp_style_expression_bodied_lambdas = true
Func<int, int> square = x => x * x;

// csharp_style_expression_bodied_lambdas = false
Func<int, int> square = x => { return x * x; };
```

#### <a name="csharp_style_expression_bodied_local_functions"></a>csharp\_style\_expression\_bodied\_local_functions

C# 7.0부터 C#에서는 [로컬 함수](/dotnet/csharp/programming-guide/classes-and-structs/local-functions)를 지원합니다. 로컬 함수는 다른 멤버에 중첩된 형식의 private 메서드입니다.

|속성|값|
|-|-|
| **규칙 이름** | csharp_style_expression_bodied_local_functions |
| **규칙 ID** | IDE0061 |
| **해당 언어** | C# 7.0+ |
| **값** | `true` - 로컬 함수에 식 본문을 사용합니다.<br /><br />`when_on_single_line` - 한 줄이 되는 경우 로컬 함수에 식 본문을 사용합니다.<br /><br />`false` - 로컬 함수에 블록 본문을 사용합니다. |
| **Visual Studio 기본값** | `false:silent` |

코드 예제:

```csharp
// csharp_style_expression_bodied_local_functions = true
void M()
{
    Hello();
    void Hello() => Console.WriteLine("Hello");
}

// csharp_style_expression_bodied_local_functions = false
void M()
{
    Hello();
    void Hello()
    {
        Console.WriteLine("Hello");
    }
}
```

### <a name="pattern-matching"></a>패턴 일치

이 섹션의 스타일 규칙은 C#에서 [패턴 일치](/dotnet/csharp/pattern-matching)를 사용하는 방법을 다룹니다.

예제 *.editorconfig* 파일:

```ini
# CSharp code style settings:
[*.cs]
csharp_style_pattern_matching_over_is_with_cast_check = true:suggestion
csharp_style_pattern_matching_over_as_with_null_check = true:suggestion
```

#### <a name="csharp_style_pattern_matching_over_is_with_cast_check"></a>csharp\_style\_pattern\_matching\_over\_is\_with\_cast_check

|속성|값|
|-|-|
| **규칙 이름** | csharp_style_pattern_matching_over_is_with_cast_check |
| **규칙 ID** | IDE0020 |
| **해당 언어** | C# 7.0+ |
| **값** | `true` - 형식 캐스트가 포함된 `is` 식보다 패턴 일치를 선호합니다.<br /><br />`false` - 패턴 일치보다 형식 캐스트가 포함된 `is` 식을 선호합니다. |
| **Visual Studio 기본값** | `true:suggestion` |

코드 예제:

```csharp
// csharp_style_pattern_matching_over_is_with_cast_check = true
if (o is int i) {...}

// csharp_style_pattern_matching_over_is_with_cast_check = false
if (o is int) {var i = (int)o; ... }
```

#### <a name="csharp_style_pattern_matching_over_as_with_null_check"></a>csharp\_style\_pattern\_matching\_over\_as\_with\_null_check

|속성|값|
|-|-|
| **규칙 이름** | csharp_style_pattern_matching_over_as_with_null_check |
| **규칙 ID** | IDE0019 |
| **해당 언어** | C# 7.0+ |
| **값** | `true` - 항목이 특정 형식인지 확인하는 경우 null 검사가 포함된 `as` 식보다 패턴 일치를 선호합니다.<br /><br />`false` - 항목이 특정 형식인지 확인하는 경우 패턴 일치보다 null 검사가 포함된 `as` 식을 선호합니다. |
| **Visual Studio 기본값** | `true:suggestion` |

코드 예제:

```csharp
// csharp_style_pattern_matching_over_as_with_null_check = true
if (o is string s) {...}

// csharp_style_pattern_matching_over_as_with_null_check = false
var s = o as string;
if (s != null) {...}
```

### <a name="inlined-variable-declarations"></a>인라인 변수 선언

이 스타일 규칙은 `out` 변수가 인라인을 선언했는지 여부에 대해 다룹니다. C# 7부터 별도 변수 선언이 아니라 [메서드 호출의 인수 목록에서 out 변수를 선언](/dotnet/csharp/language-reference/keywords/out-parameter-modifier#calling-a-method-with-an-out-argument)할 수 있습니다.

#### <a name="csharp_style_inlined_variable_declaration"></a>csharp\_style\_inlined\_variable_declaration

|속성|값|
|-|-|
| **규칙 이름** | csharp_style_inlined_variable_declaration |
| **규칙 ID** | IDE0018 |
| **해당 언어** | C# 7.0+ |
| **값** | `true` - 가능한 경우 메서드 호출의 인수 목록에서 `out` 변수를 인라인으로 선언합니다.<br /><br />`false` - 메서드 호출 전에 `out` 변수를 선언합니다. |
| **Visual Studio 기본값** | `true:suggestion` |

코드 예제:

```csharp
// csharp_style_inlined_variable_declaration = true
if (int.TryParse(value, out int i) {...}

// csharp_style_inlined_variable_declaration = false
int i;
if (int.TryParse(value, out i) {...}
```

예제 *.editorconfig* 파일:

```ini
# CSharp code style settings:
[*.cs]
csharp_style_inlined_variable_declaration = true:suggestion
```

### <a name="c-expression-level-preferences"></a>C# 식 수준 기본 설정

이 섹션의 스타일 규칙은 식 수준 기본 설정을 고려합니다.

예제 *.editorconfig* 파일:

```ini
# CSharp code style settings:
[*.cs]
csharp_prefer_simple_default_expression = true:suggestion
```

#### <a name="csharp_prefer_simple_default_expression"></a>csharp\_prefer\_simple\_default_expression

이 스타일 규칙을 사용 하 여 관련는 [`default` 기본값 식에 대 한 리터럴](/dotnet/csharp/language-reference/operators/default#default-literal) 때 컴파일러는 식의 형식을 유추할 수 있습니다.

|속성|값|
|-|-|
| **규칙 이름** | csharp_prefer_simple_default_expression |
| **규칙 ID** | IDE0034 |
| **해당 언어** | C# 7.1+  |
| **값** | `true` - `default(T)`보다 `default`를 선호합니다.<br /><br />`false` - `default`보다 `default(T)`를 선호합니다. |
| **Visual Studio 기본값** | `true:suggestion` |

코드 예제:

```csharp
// csharp_prefer_simple_default_expression = true
void DoWork(CancellationToken cancellationToken = default) { ... }

// csharp_prefer_simple_default_expression = false
void DoWork(CancellationToken cancellationToken = default(CancellationToken)) { ... }
```

### <a name="c-null-checking-preferences"></a>C# null 검사 기본 설정

이러한 스타일 규칙은 `throw` 식 또는 `throw` 문 사용을 비롯한 `null` 검사 관련 구문 및 [람다 식](/dotnet/csharp/lambda-expressions)을 호출할 때를 null 검사를 수행하거나 조건부 병합 연산자(`?.`)를 사용할지에 대해 다룹니다.

예제 *.editorconfig* 파일:

```ini
# CSharp code style settings:
[*.cs]
csharp_style_throw_expression = true:suggestion
csharp_style_conditional_delegate_call = false:suggestion
```

#### <a name="csharp_style_throw_expression"></a>csharp\_style\_throw_expression

|속성|값|
|-|-|
| **규칙 이름** | csharp_style_throw_expression |
| **규칙 ID** | IDE0016 |
| **해당 언어** | C# 7.0+ |
| **값** | `true` - `throw` 문 대신 `throw` 식을 사용합니다.<br /><br />`false` - `throw` 식 대신 `throw` 문을 사용합니다. |
| **Visual Studio 기본값** | `true:suggestion` |

코드 예제:

```csharp
// csharp_style_throw_expression = true
this.s = s ?? throw new ArgumentNullException(nameof(s));

// csharp_style_throw_expression = false
if (s == null) { throw new ArgumentNullException(nameof(s)); }
this.s = s;
```

#### <a name="csharp_style_conditional_delegate_call"></a>csharp\_style\_conditional\_delegate_call

|속성|값|
|-|-|
| **규칙 이름** | csharp_style_conditional_delegate_call |
| **규칙 ID** | IDE0041 |
| **해당 언어** | C# 6.0+  |
| **값** | `true` - null 검사를 수행하는 대신 람다 식 호출 시 조건부 병합 연산자(`?.`)를 사용합니다.<br /><br />`false` - 조건부 병합 연산자(`?.`)를 사용하는 대신 람다 식 호출 전에 null 검사를 수행합니다. |
| **Visual Studio 기본값** | `true:suggestion` |

코드 예제:

```csharp
// csharp_style_conditional_delegate_call = true
func?.Invoke(args);

// csharp_style_conditional_delegate_call = false
if (func != null) { func(args); }
```

### <a name="code-block-preferences"></a>코드 블록 기본 설정

이 스타일 규칙은 코드 블록을 묶는 데 중괄호 `{ }`를 사용하는 방법을 다룹니다.

예제 *.editorconfig* 파일:

```ini
# CSharp code style settings:
[*.cs]
csharp_prefer_braces = true:silent
```

#### <a name="csharp_prefer_braces"></a>csharp\_prefer\_braces

|속성|값|
|-|-|
| **규칙 이름** | csharp_prefer_braces |
| **규칙 ID** | IDE0011 |
| **해당 언어** | C# |
| **값** | `true` - 코드 한 줄에서도 중괄호를 선호합니다.<br /><br />`false` - 허용되는 경우 중괄호를 선호하지 않습니다.<br /><br />`when_multiline` -여러 줄에 중괄호를 사용합니다. |
| **Visual Studio 기본값** | `true:silent` |

코드 예제:

```csharp
// csharp_prefer_braces = true
if (test) { this.Display(); }

// csharp_prefer_braces = false
if (test) this.Display();
```

### <a name="unused-value-preferences"></a>사용되지 않는 값 기본 설정

이러한 스타일 규칙은 사용되지 않는 식과 값 할당을 고려합니다.

예제 *.editorconfig* 파일:

```ini
# CSharp code style settings:
[*.cs]
csharp_style_unused_value_expression_statement_preference = discard_variable:silent
csharp_style_unused_value_assignment_preference = discard_variable:suggestion
```

#### <a name="csharp_style_unused_value_expression_statement_preference"></a>csharp_style_unused_value_expression_statement_preference

|속성|값|
|-|-|
| **규칙 이름** | csharp_style_unused_value_expression_statement_preference |
| **규칙 ID** | IDE0058 |
| **해당 언어** | C# |
| **값** | `discard_variable` - 사용되지 않는 식을 [무시 항목](/dotnet/csharp/discards)으로 할당합니다. <br /><br />`unused_local_variable` - 사용되지 않는 식을 지역 변수로 할당합니다. |
| **Visual Studio 기본값** | `discard_variable:silent` |

코드 예제:

```csharp
// Original code:
System.Convert.ToInt32("35");

// After code fix for IDE0058:

// csharp_style_unused_value_expression_statement_preference = discard_variable
_ = System.Convert.ToInt32("35");

// csharp_style_unused_value_expression_statement_preference = unused_local_variable
var unused = Convert.ToInt32("35");
```

#### <a name="csharp_style_unused_value_assignment_preference"></a>csharp_style_unused_value_assignment_preference

|속성|값|
|-|-|
| **규칙 이름** | csharp_style_unused_value_assignment_preference |
| **규칙 ID** | IDE0059 |
| **해당 언어** | C# |
| **값** | `discard_variable` - 사용되지 않는 값을 할당 시 [무시 항목](/dotnet/csharp/discards)을 사용합니다.<br /><br />`unused_local_variable` - 사용되지 않는 값을 할당 시 지역 변수를 사용합니다. |
| **Visual Studio 기본값** | `discard_variable:suggestion` |

코드 예제:

```csharp
// csharp_style_unused_value_assignment_preference = discard_variable
int GetCount(Dictionary<string, int> wordCount, string searchWord)
{
    _ = wordCount.TryGetValue(searchWord, out var count);
    return count;
}

// csharp_style_unused_value_assignment_preference = unused_local_variable
int GetCount(Dictionary<string, int> wordCount, string searchWord)
{
    var unused = wordCount.TryGetValue(searchWord, out var count);
    return count;
}
```

### <a name="index-and-range-preferences"></a>인덱스 및 범위 기본 설정

이러한 스타일 규칙은 C# 8.0 이상에서 사용할 수 있는 인덱스와 범위 연산자의 사용을 고려합니다.

예제 *.editorconfig* 파일:

```ini
# CSharp code style settings:
[*.cs]
csharp_style_prefer_index_operator = true:suggestion
csharp_style_prefer_range_operator = true:suggestion
```

#### <a name="csharp_style_prefer_index_operator"></a>csharp\_style\_prefer\_index_operator

|속성|값|
|-|-|
| **규칙 이름** | csharp_style_prefer_index_operator |
| **규칙 ID** | IDE0056 |
| **해당 언어** | C# 8.0 이상 |
| **값** | `true` - 컬렉션의 끝에서 인덱스를 계산할 때 `^` 연산자를 사용합니다.<br /><br />`false` - 컬렉션의 끝에서 인덱스를 계산할 때 `^` 연산자를 사용하지 않습니다. |
| **Visual Studio 기본값** | `true:suggestion` |

코드 예제:

```csharp
// csharp_style_prefer_index_operator = true
string[] names = { "Archimedes", "Pythagoras", "Euclid" };
var index = names[^1];

// csharp_style_prefer_index_operator = false
string[] names = { "Archimedes", "Pythagoras", "Euclid" };
var index = names[names.Length - 1];
```

#### <a name="csharp_style_prefer_range_operator"></a>csharp\_style\_prefer\_range_operator

|속성|값|
|-|-|
| **규칙 이름** | csharp_style_prefer_range_operator |
| **규칙 ID** | IDE0057 |
| **해당 언어** | C# 8.0 이상 |
| **값** | `true` - 컬렉션의 "조각"을 추출할 때 범위 연산자 `..`을 사용합니다.<br /><br />`false` - 컬렉션의 "조각"을 추출할 때 범위 연산자 `..`을 사용하지 않습니다. |
| **Visual Studio 기본값** | `true:suggestion` |

코드 예제:

```csharp
// csharp_style_prefer_range_operator = true
string sentence = "the quick brown fox";
var sub = sentence[0..^4];

// csharp_style_prefer_range_operator = false
string sentence = "the quick brown fox";
var sub = sentence.Substring(0, sentence.Length - 4);
```

### <a name="miscellaneous-preferences"></a>기타 기본 설정

이 섹션에는 기타 스타일 규칙이 포함되어 있습니다.

예제 *.editorconfig* 파일:

```ini
# CSharp code style settings:
[*.cs]
csharp_style_deconstructed_variable_declaration = true:suggestion
csharp_style_pattern_local_over_anonymous_function = true:suggestion
csharp_using_directive_placement = outside_namespace:silent
csharp_prefer_static_local_function = true:suggestion
csharp_prefer_simple_using_statement = true:suggestion
csharp_style_prefer_switch_expression = true:suggestion
```

#### <a name="csharp_style_deconstructed_variable_declaration"></a>csharp\_style\_deconstructed\_variable_declaration

|속성|값|
|-|-|
| **규칙 이름** | csharp_style_deconstructed_variable_declaration |
| **규칙 ID** | IDE0042 |
| **해당 언어** | C# 7.0+ |
| **값** | `true` - 분해된 변수 선언을 선호합니다.<br /><br />`false` - 변수 선언에서 분해를 선호하지 않습니다. |
| **Visual Studio 기본값** | `true:suggestion` |

코드 예제:

```csharp
// csharp_style_deconstructed_variable_declaration = true
var (name, age) = GetPersonTuple();
Console.WriteLine($"{name} {age}");

(int x, int y) = GetPointTuple();
Console.WriteLine($"{x} {y}");

// csharp_style_deconstructed_variable_declaration = false
var person = GetPersonTuple();
Console.WriteLine($"{person.name} {person.age}");

(int x, int y) point = GetPointTuple();
Console.WriteLine($"{point.x} {point.y}");
```

#### <a name="csharp_style_pattern_local_over_anonymous_function"></a>csharp\_style\_pattern\_local\_over\_anonymous_function

C# 7.0부터 C#에서는 [로컬 함수](/dotnet/csharp/programming-guide/classes-and-structs/local-functions)를 지원합니다. 로컬 함수는 다른 멤버에 중첩된 형식의 private 메서드입니다.

|속성|값|
|-|-|
| **규칙 이름** | csharp_style_pattern_local_over_anonymous_function |
| **규칙 ID** | IDE0039 |
| **해당 언어** | C# 7.0+ |
| **값** | `true` - 익명 함수보다 로컬 함수를 선호합니다.<br /><br />`false` - 로컬 함수보다 익명 함수를 선호합니다. |
| **Visual Studio 기본값** | `true:suggestion` |

코드 예제:

```csharp
// csharp_style_pattern_local_over_anonymous_function = true
int fibonacci(int n)
{
    return n <= 1 ? 1 : fibonacci(n-1) + fibonacci(n-2);
}

// csharp_style_pattern_local_over_anonymous_function = false
Func<int, int> fibonacci = null;
fibonacci = (int n) =>
{
    return n <= 1 ? 1 : fibonacci(n - 1) + fibonacci(n - 2);
};
```

#### <a name="csharp_using_directive_placement"></a>csharp\_using\_directive_placement

|속성|값|
|-|-|
| **규칙 이름** | csharp_using_directive_placement |
| **규칙 ID** | IDE0065 |
| **해당 언어** | C# |
| **값** | `outside_namespace` - `using` 지시문이 네임스페이스 밖에 위치하도록 합니다.<br /><br />`inside_namespace` - `using` 지시문이 네임스페이스 안에 위치하도록 합니다. |
| **Visual Studio 기본값** | `outside_namespace:silent` |

코드 예제:

```csharp
// csharp_using_directive_placement = outside_namespace
using System;

namespace Conventions
{
    ...
}

// csharp_using_directive_placement = inside_namespace
namespace Conventions
{
    using System;
    ...
}
```

#### <a name="csharp_prefer_static_local_function"></a>csharp\_prefer\_static\_local_function

|속성|값|
|-|-|
| **규칙 이름** | csharp_prefer_static_local_function |
| **규칙 ID** | IDE0062 |
| **해당 언어** | C# 8.0 이상 |
| **값** | `true` - 로컬 함수가 `static`으로 표시되도록 합니다.<br /><br />`false` - 로컬 함수가 `static`으로 표시되도록 하지 않습니다. |
| **Visual Studio 기본값** | `true:suggestion` |

코드 예제:

```csharp
// csharp_prefer_static_local_function = true
void M()
{
    Hello();
    static void Hello()
    {
        Console.WriteLine("Hello");
    }
}

// csharp_prefer_static_local_function = false
void M()
{
    Hello();
    void Hello()
    {
        Console.WriteLine("Hello");
    }
}
```

#### <a name="csharp_prefer_simple_using_statement"></a>csharp\_prefer\_simple\_using_statement

|속성|값|
|-|-|
| **규칙 이름** | csharp_prefer_simple_using_statement |
| **규칙 ID** | IDE0063 |
| **해당 언어** | C# 8.0 이상 |
| **값** | `true` - *단순* `using` 문을 사용합니다.<br /><br />`false` - *단순* `using` 문을 사용하지 않습니다. |
| **Visual Studio 기본값** | `true:suggestion` |

코드 예제:

```csharp
// csharp_prefer_simple_using_statement = true
using var a = b;

// csharp_prefer_simple_using_statement = false
using (var a = b) { }
```

#### <a name="csharp_style_prefer_switch_expression"></a>csharp\_style\_prefer\_switch_expression

|속성|값|
|-|-|
| **규칙 이름** | csharp_style_prefer_switch_expression |
| **규칙 ID** | IDE0066 |
| **해당 언어** | C# 8.0 이상 |
| **값** | `true` - `switch` 식을 사용하는 것이 좋습니다(C# 8.0에서 도입됨).<br /><br />`false` - [switch 문](/dotnet/csharp/language-reference/keywords/switch)을 사용하는 것이 좋습니다. |
| **Visual Studio 기본값** | `true:suggestion` |
| **도입된 버전** | Visual Studio 2019 버전 16.2 |

코드 예제:

```csharp
// csharp_style_prefer_switch_expression = true
return x switch
{
    1 => 1 * 1,
    2 => 2 * 2,
    _ => 0,
};

// csharp_style_prefer_switch_expression = false
switch (x)
{
    case 1:
        return 1 * 1;
    case 2:
        return 2 * 2;
    default:
        return 0;
}
```

## <a name="see-also"></a>참조

- [서식 지정 규칙](editorconfig-formatting-conventions.md)
- [명명 규칙](editorconfig-naming-conventions.md)
- [EditorConfig에 대한 .NET 코딩 규칙 설정](editorconfig-code-style-settings-reference.md)
