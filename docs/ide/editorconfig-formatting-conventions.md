---
title: EditorConfig에 대한 .NET 서식 지정 규칙
ms.date: 04/02/2020
ms.topic: reference
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- formatting conventions [EditorConfig]
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 0490912683fd683398c89e8e69b62dd3824ee04b
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85533473"
---
# <a name="formatting-conventions"></a>서식 지정 규칙

Visual Studio의 EditorConfig에 대한 서식 지정 규칙은 다음의 범주로 나뉩니다.

- [.NET 서식 지정 설정](#net-formatting-settings)

- [C# 서식 지정 설정](#c-formatting-settings)

## <a name="rule-format"></a>규칙 형식

서식 지정 규칙의 형식은 다음과 같습니다.

`rule_name = value`

대부분의 규칙에서, `value`에 대해 `true`(이 스타일 선호) 또는 `false`(이 스타일 선호 안 함)를 지정합니다. 다른 규칙의 경우 `flush_left`, `before_and_after` 등의 값을 지정하여 규칙을 적용할 시기 및 위치를 설명합니다. 심각도를 지정하지 않습니다.

## <a name="net-formatting-settings"></a>.NET 서식 지정 설정

이 섹션의 서식 지정 규칙은 C# 및 Visual Basic 코드에 적용됩니다.

- [using 구성](#organize-using-directives)
  - dotnet_sort_system_directives_first
  - dotnet_separate_import_directive_groups

### <a name="organize-using-directives"></a>using 지시문 구성

이러한 서식 지정 규칙은 `using` 지시문과 `Imports` 문의 정렬 및 표시를 제어합니다.

예제 *.editorconfig* 파일:

```ini
# .NET formatting settings
[*.{cs,vb}]
dotnet_sort_system_directives_first = true
dotnet_separate_import_directive_groups = true
```

#### <a name="dotnet_sort_system_directives_first"></a>dotnet\_sort\_system\_directives_first

|속성|값|
|-|-|
| **규칙 이름** | dotnet_sort_system_directives_first |
| **해당 언어** | C# 및 Visual Basic |
| **도입된 버전** | Visual Studio 2017 15.3 버전 |
| **값** | `true` - System.* `using` 지시문을 사전순으로 정렬하고 다른 using 지시문 앞에 배치합니다.<br /><br />`false` - System.* `using` 지시문을 다른 `using` 지시문 앞에 배치하지 않습니다. |

코드 예제:

```csharp
// dotnet_sort_system_directives_first = true
using System.Collections.Generic;
using System.Threading.Tasks;
using Octokit;

// dotnet_sort_system_directives_first = false
using System.Collections.Generic;
using Octokit;
using System.Threading.Tasks;
```

#### <a name="dotnet_separate_import_directive_groups"></a>dotnet\_separate\_import\_directive\_groups

|속성|값|
|-|-|
| **규칙 이름** | dotnet_separate_import_directive_groups |
| **해당 언어** | C# 및 Visual Basic |
| **도입된 버전** | Visual Studio 2017 15.5 버전 |
| **값** | `true` - `using` 지시문 그룹 사이에 빈 줄을 넣습니다.<br /><br />`false` - `using` 지시문 그룹 사이에 빈 줄을 넣지 않습니다. |

코드 예제:

```csharp
// dotnet_separate_import_directive_groups = true
using System.Collections.Generic;
using System.Threading.Tasks;

using Octokit;

// dotnet_separate_import_directive_groups = false
using System.Collections.Generic;
using System.Threading.Tasks;
using Octokit;
```

## <a name="c-formatting-settings"></a>C# 서식 지정 설정

이 섹션의 서식 설정 규칙은 C# 코드에만 적용됩니다.

- [줄 바꿈 옵션](#new-line-options)
  - csharp_new_line_before_open_brace
  - csharp_new_line_before_else
  - csharp_new_line_before_catch
  - csharp_new_line_before_finally
  - csharp_new_line_before_members_in_object_initializers
  - csharp_new_line_before_members_in_anonymous_types
  - csharp_new_line_between_query_expression_clauses
- [들여쓰기 옵션](#indentation-options)
  - csharp_indent_case_contents
  - csharp_indent_switch_labels
  - csharp_indent_labels
  - csharp_indent_block_contents
  - csharp_indent_braces
  - csharp_indent_case_contents_when_block
- [간격 옵션](#spacing-options)
  - csharp_space_after_cast
  - csharp_space_after_keywords_in_control_flow_statements
  - csharp_space_between_parentheses
  - csharp_space_before_colon_in_inheritance_clause
  - csharp_space_after_colon_in_inheritance_clause
  - csharp_space_around_binary_operators
  - csharp_space_between_method_declaration_parameter_list_parentheses
  - csharp_space_between_method_declaration_empty_parameter_list_parentheses
  - csharp_space_between_method_declaration_name_and_open_parenthesis
  - csharp_space_between_method_call_parameter_list_parentheses
  - csharp_space_between_method_call_empty_parameter_list_parentheses
  - csharp_space_between_method_call_name_and_opening_parenthesis
  - csharp_space_after_comma
  - csharp_space_before_comma
  - csharp_space_after_dot
  - csharp_space_before_dot
  - csharp_space_after_semicolon_in_for_statement
  - csharp_space_before_semicolon_in_for_statement
  - csharp_space_around_declaration_statements
  - csharp_space_before_open_square_brackets
  - csharp_space_between_empty_square_brackets
  - csharp_space_between_square_brackets
- [줄 바꿈 옵션](#wrap-options)
  - csharp_preserve_single_line_statements
  - csharp_preserve_single_line_blocks
- [지시문 옵션 사용](#using-directive-options) 
  - csharp_using_directive_placement

### <a name="new-line-options"></a>줄 바꿈 옵션

이러한 서식 지정 규칙은 코드의 서식을 지정하기 위해 새 줄을 사용합니다.

예제 *.editorconfig* 파일:

```ini
# CSharp formatting settings:
[*.cs]
csharp_new_line_before_open_brace = methods, properties, control_blocks, types
csharp_new_line_before_else = true
csharp_new_line_before_catch = true
csharp_new_line_before_finally = true
csharp_new_line_before_members_in_object_initializers = true
csharp_new_line_before_members_in_anonymous_types = true
csharp_new_line_between_query_expression_clauses = true
```

#### <a name="csharp_new_line_before_open_brace"></a>csharp\_new\_line\_before\_open_brace

이 규칙은 중괄호 `{`가 앞의 코드와 동일한 줄 또는 새 줄에 배치되어야 하는지를 다룹니다. 이 규칙의 경우 **모두**, **없음** 또는 하나 이상의 코드 요소(예: **메서드** 또는 **속성**)를 지정하여 이 규칙을 적용할 시점을 정의합니다. 여러 개의 코드 요소를 지정하려면 쉼표(,)로 구분합니다.

|속성|값|
|-|-|
| **규칙 이름** | csharp_new_line_before_open_brace |
| **해당 언어** | C# |
| **도입된 버전** | Visual Studio 2017 15.3 버전 |
| **값** | `all` - 모든 식에서 중괄호를 새 줄에 배치해야 합니다(“Allman” 스타일).<br /><br />`none` - 모든 식에서 중괄호를 동일한 줄에 배치해야 합니다(“K&R”).<br /><br />`accessors`, `anonymous_methods`, `anonymous_types`, `control_blocks`, `events`, `indexers`, `lambdas`, `local_functions`, `methods`, `object_collection_array_initializers`, `properties`, `types` - 지정된 코드 요소에서 중괄호를 새 줄에 배치해야 합니다(“Allman” 스타일). |

코드 예제:

```csharp
// csharp_new_line_before_open_brace = all
void MyMethod()
{
    if (...)
    {
        ...
    }
}

// csharp_new_line_before_open_brace = none
void MyMethod() {
    if (...) {
        ...
    }
}
```

#### <a name="csharp_new_line_before_else"></a>csharp\_new\_line\_before_else

|속성|값|
|-|-|
| **규칙 이름** | csharp_new_line_before_else |
| **해당 언어** | C# |
| **도입된 버전** | Visual Studio 2017 15.3 버전 |
| **값** | `true` - `else` 문을 새 줄에 배치합니다.<br /><br />`false` - `else` 문을 동일한 줄에 배치합니다. |

코드 예제:

```csharp
// csharp_new_line_before_else = true
if (...) {
    ...
}
else {
    ...
}

// csharp_new_line_before_else = false
if (...) {
    ...
} else {
    ...
}
```

#### <a name="csharp_new_line_before_catch"></a>csharp\_new\_line\_before_catch

|속성|값|
|-|-|
| **규칙 이름** | csharp_new_line_before_catch |
| **해당 언어** | C# |
| **도입된 버전** | Visual Studio 2017 15.3 버전 |
| **값** | `true` - `catch` 문을 새 줄에 배치합니다.<br /><br />`false` - `catch` 문을 동일한 줄에 배치합니다. |

코드 예제:

```csharp
// csharp_new_line_before_catch = true
try {
    ...
}
catch (Exception e) {
    ...
}

// csharp_new_line_before_catch = false
try {
    ...
} catch (Exception e) {
    ...
}
```

#### <a name="csharp_new_line_before_finally"></a>csharp\_new\_line\_before_finally

|속성|값|
|-|-|
| **규칙 이름** | csharp_new_line_before_finally |
| **해당 언어** | C# |
| **도입된 버전** | Visual Studio 2017 15.3 버전 |
| **값** | `true` - `finally` 문을 닫는 괄호 뒤의 새 줄에 배치해야 합니다.<br /><br />`false` - `finally` 문을 닫는 괄호와 동일한 줄에 배치해야 합니다. |

코드 예제:

```csharp
// csharp_new_line_before_finally = true
try {
    ...
}
catch (Exception e) {
    ...
}
finally {
    ...
}

// csharp_new_line_before_finally = false
try {
    ...
} catch (Exception e) {
    ...
} finally {
    ...
}
```

#### <a name="csharp_new_line_before_members_in_object_initializers"></a>csharp\_new\_line\_before\_members\_in\_object_initializers

|속성|값|
|-|-|
| **규칙 이름** | csharp_new_line_before_members_in_object_initializers |
| **해당 언어** | C# |
| **도입된 버전** | Visual Studio 2017 15.3 버전 |
| **값** | `true` - 개체 이니셜라이저의 멤버를 새 줄에 배치해야 합니다.<br /><br />`false` - 개체 이니셜라이저의 멤버를 동일한 줄에 배치해야 합니다. |

코드 예제:

```csharp
// csharp_new_line_before_members_in_object_initializers = true
var z = new B()
{
    A = 3,
    B = 4
}

// csharp_new_line_before_members_in_object_initializers = false
var z = new B()
{
    A = 3, B = 4
}
```

#### <a name="csharp_new_line_before_members_in_anonymous_types"></a>csharp\_new\_line\_before\_members\_in\_anonymous_types

|속성|값|
|-|-|
| **규칙 이름** | csharp_new_line_before_members_in_anonymous_types |
| **해당 언어** | C# |
| **도입된 버전** | Visual Studio 2017 15.3 버전 |
| **값** | `true` - 무명 형식의 멤버를 새 줄에 배치해야 합니다.<br /><br />`false` - 무명 형식의 멤버를 동일한 줄에 배치해야 합니다. |

코드 예제:

```csharp
// csharp_new_line_before_members_in_anonymous_types = true
var z = new
{
    A = 3,
    B = 4
}

// csharp_new_line_before_members_in_anonymous_types = false
var z = new
{
    A = 3, B = 4
}
```

#### <a name="csharp_new_line_between_query_expression_clauses"></a>csharp_new_line_between_query_expression_clauses

|속성|값|
|-|-|
| **규칙 이름** | csharp_new_line_between_query_expression_clauses |
| **해당 언어** | C# |
| **도입된 버전** | Visual Studio 2017 15.3 버전 |
| **값** | `true` - 쿼리 식 절의 요소를 새 줄에 배치해야 합니다.<br /><br />`false` - 쿼리 식 절의 요소를 동일한 줄에 배치해야 합니다. |

코드 예제:

```csharp
// csharp_new_line_between_query_expression_clauses = true
var q = from a in e
        from b in e
        select a * b;

// csharp_new_line_between_query_expression_clauses = false
var q = from a in e from b in e
        select a * b;
```

### <a name="indentation-options"></a>들여쓰기 옵션

이러한 서식 지정 규칙은 코드의 서식을 지정하기 위해 들여쓰기를 사용합니다.

예제 *.editorconfig* 파일:

```ini
# CSharp formatting settings:
[*.cs]
csharp_indent_case_contents = true
csharp_indent_switch_labels = true
csharp_indent_labels = flush_left
csharp_indent_block_contents = true
csharp_indent_braces = false
csharp_indent_case_contents_when_block = true
```

#### <a name="csharp_indent_case_contents"></a>csharp\_indent\_case_contents

|속성|값|
|-|-|
| **규칙 이름** | csharp_indent_case_contents |
| **해당 언어** | C# |
| **도입된 버전** | Visual Studio 2017 15.3 버전 |
| **값** | `true` - `switch` case 콘텐츠를 들여씁니다.<br /><br />`false` - `switch` case 콘텐츠를 들여 쓰지 않습니다. |

- 이 규칙을 **true**로 설정한 경우 i입니다.
- 이 규칙을 **false**로 설정한 경우 d입니다.

코드 예제:

```csharp
// csharp_indent_case_contents = true
switch(c) {
    case Color.Red:
        Console.WriteLine("The color is red");
        break;
    case Color.Blue:
        Console.WriteLine("The color is blue");
        break;
    default:
        Console.WriteLine("The color is unknown.");
        break;
}

// csharp_indent_case_contents = false
switch(c) {
    case Color.Red:
    Console.WriteLine("The color is red");
    break;
    case Color.Blue:
    Console.WriteLine("The color is blue");
    break;
    default:
    Console.WriteLine("The color is unknown.");
    break;
}
```

#### <a name="csharp_indent_switch_labels"></a>csharp\_indent\_switch_labels

|속성|값|
|-|-|
| **규칙 이름** | csharp_indent_switch_labels |
| **해당 언어** | C# |
| **도입된 버전** | Visual Studio 2017 15.3 버전 |
| **값** | `true` - `switch` 레이블을 들여씁니다.<br /><br />`false` - `switch` 레이블을 들여 쓰지 않습니다. |

코드 예제:

```csharp
// csharp_indent_switch_labels = true
switch(c) {
    case Color.Red:
        Console.WriteLine("The color is red");
        break;
    case Color.Blue:
        Console.WriteLine("The color is blue");
        break;
    default:
        Console.WriteLine("The color is unknown.");
        break;
}

// csharp_indent_switch_labels = false
switch(c) {
case Color.Red:
    Console.WriteLine("The color is red");
    break;
case Color.Blue:
    Console.WriteLine("The color is blue");
    break;
default:
    Console.WriteLine("The color is unknown.");
    break;
}
```

#### <a name="csharp_indent_labels"></a>csharp\_indent_labels

|속성|값|
|-|-|
| **규칙 이름** | csharp_indent_labels |
| **해당 언어** | C# |
| **도입된 버전** | Visual Studio 2017 15.3 버전 |
| **값** | `flush_left` - 레이블이 가장 왼쪽 열에 배치됩니다.<br /><br />`one_less_than_current` - 레이블이 현재 컨텍스트보다 한 수준 더 들여쓰기에 배치됩니다.<br /><br />`no_change` - 레이블이 현재 컨텍스트와 동일한 들여쓰기에 배치됩니다. |

코드 예제:

```csharp
// csharp_indent_labels= flush_left
class C
{
    private string MyMethod(...)
    {
        if (...) {
            goto error;
        }
error:
        throw new Exception(...);
    }
}

// csharp_indent_labels = one_less_than_current
class C
{
    private string MyMethod(...)
    {
        if (...) {
            goto error;
        }
    error:
        throw new Exception(...);
    }
}

// csharp_indent_labels= no_change
class C
{
    private string MyMethod(...)
    {
        if (...) {
            goto error;
        }
        error:
        throw new Exception(...);
    }
}
```

#### <a name="csharp_indent_block_contents"></a>csharp_indent_block_contents

|속성|값|
|-|-|
| **규칙 이름** | csharp_indent_block_contents |
| **해당 언어** | C# |
| **값** | `true` - <br /><br />`false` -  |

코드 예제:

```csharp
// csharp_indent_block_contents = true
static void Hello()
{
    Console.WriteLine("Hello");
}

// csharp_indent_block_contents = false
static void Hello()
{
Console.WriteLine("Hello");
}
```

#### <a name="csharp_indent_braces"></a>csharp_indent_braces

|속성|값|
|-|-|
| **규칙 이름** | csharp_indent_braces |
| **해당 언어** | C# |
| **값** | `true` - <br /><br />`false` -  |

코드 예제:

```csharp
// csharp_indent_braces = true
static void Hello()
    {
    Console.WriteLine("Hello");
    }

// csharp_indent_braces = false
static void Hello()
{
    Console.WriteLine("Hello");
}
```

#### <a name="csharp_indent_case_contents_when_block"></a>csharp_indent_case_contents_when_block

|속성|값|
|-|-|
| **규칙 이름** | csharp_indent_case_contents_when_block |
| **해당 언어** | C# |
| **값** | `true` - <br /><br />`false` -  |

코드 예제:

```csharp
// csharp_indent_case_contents_when_block = true
case 0:
    {
        Console.WriteLine("Hello");
        break;
    }

// csharp_indent_case_contents_when_block = false
case 0:
{
    Console.WriteLine("Hello");
    break;
}
```

### <a name="spacing-options"></a>간격 옵션

이러한 서식 지정 규칙은 코드의 서식을 지정하기 위해 공백 문자를 사용합니다.

예제 *.editorconfig* 파일:

```ini
# CSharp formatting settings:
[*.cs]
csharp_space_after_cast = true
csharp_space_after_keywords_in_control_flow_statements = true
csharp_space_between_parentheses = control_flow_statements, type_casts
csharp_space_before_colon_in_inheritance_clause = true
csharp_space_after_colon_in_inheritance_clause = true
csharp_space_around_binary_operators = before_and_after
csharp_space_between_method_declaration_parameter_list_parentheses = true
csharp_space_between_method_declaration_empty_parameter_list_parentheses = false
csharp_space_between_method_declaration_name_and_open_parenthesis = false
csharp_space_between_method_call_parameter_list_parentheses = true
csharp_space_between_method_call_empty_parameter_list_parentheses = false
csharp_space_between_method_call_name_and_opening_parenthesis = false
csharp_space_after_comma = true
csharp_space_before_comma = false
csharp_space_after_dot = false
csharp_space_before_dot = false
csharp_space_after_semicolon_in_for_statement = true
csharp_space_before_semicolon_in_for_statement = false
csharp_space_around_declaration_statements = false
csharp_space_before_open_square_brackets = false
csharp_space_between_empty_square_brackets = false
csharp_space_between_square_brackets = false
```

#### <a name="csharp_space_after_cast"></a>csharp\_space\_after_cast

|속성|값|
|-|-|
| **규칙 이름** | csharp_space_after_cast |
| **해당 언어** | C# |
| **도입된 버전** | Visual Studio 2017 15.3 버전 |
| **값** | `true` - 캐스트와 값 사이에 공백 문자를 배치합니다.<br /><br />`false` - 캐스트와 값 사이에서 공백을 제거합니다. |

코드 예제:

```csharp
// csharp_space_after_cast = true
int y = (int) x;

// csharp_space_after_cast = false
int y = (int)x;
```

#### <a name="csharp_space_after_keywords_in_control_flow_statements"></a>csharp_space_after_keywords_in_control_flow_statements

|속성|값|
|-|-|
| **규칙 이름** | csharp_space_after_keywords_in_control_flow_statements |
| **해당 언어** | C# |
| **도입된 버전** | Visual Studio 2017 15.3 버전 |
| **값** | `true` - `for` 루프와 같은 제어 흐름 문의 키워드 뒤에 공백 문자를 배치합니다.<br /><br />`false` - `for` 루프와 같은 제어 흐름 문의 키워드 뒤에서 공백을 제거합니다. |

코드 예제:

```csharp
// csharp_space_after_keywords_in_control_flow_statements = true
for (int i;i<x;i++) { ... }

// csharp_space_after_keywords_in_control_flow_statements = false
for(int i;i<x;i++) { ... }
```

#### <a name="csharp_space_between_parentheses"></a>csharp_space_between_parentheses

|속성|값|
|-|-|
| **규칙 이름** | csharp_space_between_parentheses |
| **해당 언어** | C# |
| **도입된 버전** | Visual Studio 2017 15.3 버전 |
| **값** | `control_flow_statements` - 제어 흐름 문의 괄호 사이에 공백을 넣습니다.<br /><br />`expressions` - 식의 괄호 사이에 공백을 넣습니다.<br /><br />`type_casts` - 형식 캐스트의 괄호 사이에 공백을 넣습니다. |

이 규칙을 생략하거나 `control_flow_statements`, `expressions` 또는 `type_casts` 이외의 값을 사용하면 설정이 적용되지 않습니다.

코드 예제:

```csharp
// csharp_space_between_parentheses = control_flow_statements
for ( int i = 0; i < 10; i++ ) { }

// csharp_space_between_parentheses = expressions
var z = ( x * y ) - ( ( y - x ) * 3 );

// csharp_space_between_parentheses = type_casts
int y = ( int )x;
```

#### <a name="csharp_space_before_colon_in_inheritance_clause"></a>csharp\_space\_before\_colon\_in\_inheritance_clause

|속성|값|
|-|-|
| **규칙 이름** | csharp_space_before_colon_in_inheritance_clause |
| **해당 언어** | C# |
| **도입된 버전** | Visual Studio 2017 버전 15.7 |
| **값** | `true` - 형식 선언에서 베이스 또는 인터페이스의 콜론 앞에 공백 문자를 배치합니다.<br /><br />`false` - 형식 선언에서 베이스 또는 인터페이스의 콜론 앞에서 공백을 제거합니다. |

코드 예제:

```csharp
// csharp_space_before_colon_in_inheritance_clause = true
interface I
{

}

class C : I
{

}

// csharp_space_before_colon_in_inheritance_clause = false
interface I
{

}

class C: I
{

}
```

#### <a name="csharp_space_after_colon_in_inheritance_clause"></a>csharp\_space\_after\_colon\_in\_inheritance_clause

|속성|값|
|-|-|
| **규칙 이름** | csharp_space_after_colon_in_inheritance_clause |
| **해당 언어** | C# |
| **도입된 버전** | Visual Studio 2017 버전 15.7 |
| **값** | `true` - 형식 선언에서 베이스 또는 인터페이스의 콜론 뒤에 공백 문자를 배치합니다.<br /><br />`false` - 형식 선언에서 베이스 또는 인터페이스의 콜론 뒤에서 공백을 제거합니다. |

코드 예제:

```csharp
// csharp_space_after_colon_in_inheritance_clause = true
interface I
{

}

class C : I
{

}

// csharp_space_after_colon_in_inheritance_clause = false
interface I
{

}

class C :I
{

}
```

#### <a name="csharp_space_around_binary_operators"></a>csharp\_space\_around\_binary_operators

|속성|값|
|-|-|
| **규칙 이름** | csharp_space_around_binary_operators |
| **해당 언어** | C# |
| **도입된 버전** | Visual Studio 2017 버전 15.7 |
| **값** | `before_and_after` - 이항 연산자 앞뒤에 공백을 삽입합니다.<br /><br />`none` - 이항 연산자 앞뒤의 공백을 제거합니다.<br /><br />`ignore` - 이항 연산자 주위의 공백을 무시합니다. |

이 규칙을 생략하거나 `before_and_after`, `none` 또는 `ignore` 이외의 값을 사용하는 경우 설정이 적용되지 않습니다.

코드 예제:

```csharp
// csharp_space_around_binary_operators = before_and_after
return x * (x - y);

// csharp_space_around_binary_operators = none
return x*(x-y);

// csharp_space_around_binary_operators = ignore
return x  *  (x-y);
```

#### <a name="csharp_space_between_method_declaration_parameter_list_parentheses"></a>csharp_space_between_method_declaration_parameter_list_parentheses

|속성|값|
|-|-|
| **규칙 이름** | csharp_space_between_method_declaration_parameter_list_parentheses |
| **해당 언어** | C# |
| **도입된 버전** | Visual Studio 2017 15.3 버전 |
| **값** | `true` - 여는 괄호 뒤 및 메서드 선언 매개 변수 목록의 닫는 괄호 앞에 공백 문자를 넣습니다.<br /><br />`false` - 여는 괄호 뒤 및 메서드 선언 매개 변수 목록의 닫는 괄호 앞에서 공백 문자를 제거합니다. |

코드 예제:

```csharp
// csharp_space_between_method_declaration_parameter_list_parentheses = true
void Bark( int x ) { ... }

// csharp_space_between_method_declaration_parameter_list_parentheses = false
void Bark(int x) { ... }
```

#### <a name="csharp_space_between_method_declaration_empty_parameter_list_parentheses"></a>csharp_space_between_method_declaration_empty_parameter_list_parentheses

|속성|값|
|-|-|
| **규칙 이름** | csharp_space_between_method_declaration_empty_parameter_list_parentheses |
| **해당 언어** | C# |
| **도입된 버전** | Visual Studio 2017 버전 15.7 |
| **값** | `true` - 메서드 선언에서 빈 매개 변수 목록 괄호 안에 공백을 삽입합니다.<br /><br />`false` - 메서드 선언에서 빈 매개 변수 목록 괄호 안의 공백을 제거합니다. |

코드 예제:

```csharp
// csharp_space_between_method_declaration_empty_parameter_list_parentheses = true
void Goo( )
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}

// csharp_space_between_method_declaration_empty_parameter_list_parentheses = false
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}
```

#### <a name="csharp_space_between_method_declaration_name_and_open_parenthesis"></a>csharp_space_between_method_declaration_name_and_open_parenthesis

|속성|값|
|-|-|
| **규칙 이름** | csharp_space_between_method_declaration_name_and_open_parenthesis |
| **해당 언어** | C# |
| **값** | `true` -메서드 선언에서 메서드 이름과 여는 괄호 사이에 공백 문자를 배치합니다.<br /><br />`false` -메서드 선언에서 메서드 이름과 여는 괄호 사이에서 공백 문자를 제거합니다. |

코드 예제:

```csharp
// csharp_space_between_method_declaration_name_and_open_parenthesis = true
void M () { }

// csharp_space_between_method_declaration_name_and_open_parenthesis = false
void M() { }
```

#### <a name="csharp_space_between_method_call_parameter_list_parentheses"></a>csharp_space_between_method_call_parameter_list_parentheses

|속성|값|
|-|-|
| **규칙 이름** | csharp_space_between_method_call_parameter_list_parentheses |
| **해당 언어** | C# |
| **도입된 버전** | Visual Studio 2017 15.3 버전 |
| **값** | `true` - 여는 괄호 뒤 및 메서드 호출의 닫는 괄호 앞에 공백 문자를 넣습니다.<br /><br />`false` - 여는 괄호 뒤 및 메서드 호출의 닫는 괄호 앞에서 공백 문자를 제거합니다. |

코드 예제:

```csharp
// csharp_space_between_method_call_parameter_list_parentheses = true
MyMethod( argument );

// csharp_space_between_method_call_parameter_list_parentheses = false
MyMethod(argument);
```

#### <a name="csharp_space_between_method_call_empty_parameter_list_parentheses"></a>csharp_space_between_method_call_empty_parameter_list_parentheses

|속성|값|
|-|-|
| **규칙 이름** | csharp_space_between_method_call_empty_parameter_list_parentheses |
| **해당 언어** | C# |
| **도입된 버전** | Visual Studio 2017 버전 15.7 |
| **값** | `true` - 빈 인수 목록 괄호 안에 공백을 삽입합니다.<br /><br />`false` - 빈 인수 목록 괄호 안의 공백을 제거합니다. |

코드 예제:

```csharp
// csharp_space_between_method_call_empty_parameter_list_parentheses = true
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo( );
}

// csharp_space_between_method_call_empty_parameter_list_parentheses = false
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}
```

#### <a name="csharp_space_between_method_call_name_and_opening_parenthesis"></a>csharp_space_between_method_call_name_and_opening_parenthesis

|속성|값|
|-|-|
| **규칙 이름** | csharp_space_between_method_call_name_and_opening_parenthesis |
| **해당 언어** | C# |
| **도입된 버전** | Visual Studio 2017 버전 15.7 |
| **값** | `true` - 메서드 호출 이름과 여는 괄호 사이에 공백을 삽입합니다.<br /><br />`false` - 메서드 호출 이름과 여는 괄호 사이의 공백을 제거합니다. |

코드 예제:

```csharp
// csharp_space_between_method_call_name_and_opening_parenthesis = true
void Goo()
{
    Goo (1);
}

void Goo(int x)
{
    Goo ();
}

// csharp_space_between_method_call_name_and_opening_parenthesis = false
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}
```

#### <a name="csharp_space_after_comma"></a>csharp_space_after_comma

|속성|값|
|-|-|
| **규칙 이름** | csharp_space_after_comma |
| **해당 언어** | C# |
| **값** | `true` - 쉼표 뒤에 공백을 삽입합니다.<br /><br />`false` - 쉼표 뒤의 공백을 제거합니다. |

코드 예제:

```csharp
// csharp_space_after_comma = true
int[] x = new int[] { 1, 2, 3, 4, 5 };

// csharp_space_after_comma = false
int[] x = new int[] { 1,2,3,4,5 }
```

#### <a name="csharp_space_before_comma"></a>csharp_space_before_comma

|속성|값|
|-|-|
| **규칙 이름** | csharp_space_before_comma |
| **해당 언어** | C# |
| **값** | `true` - 쉼표 앞에 공백을 삽입합니다.<br /><br />`false` - 쉼표 앞에서 공백을 제거합니다. |

코드 예제:

```csharp
// csharp_space_before_comma = true
int[] x = new int[] { 1 , 2 , 3 , 4 , 5 };

// csharp_space_before_comma = false
int[] x = new int[] { 1, 2, 3, 4, 5 };
```

#### <a name="csharp_space_after_dot"></a>csharp_space_after_dot

|속성|값|
|-|-|
| **규칙 이름** | csharp_space_after_dot |
| **해당 언어** | C# |
| **값** | `true` - 점 뒤에 공백을 삽입합니다.<br /><br />`false` - 점 뒤의 공백을 제거합니다. |

코드 예제:

```csharp
// csharp_space_after_dot = true
this. Goo();

// csharp_space_after_dot = false
this.Goo();
```

#### <a name="csharp_space_before_dot"></a>csharp_space_before_dot

|속성|값|
|-|-|
| **규칙 이름** | csharp_space_before_dot |
| **해당 언어** | C# |
| **값** | `true` - 점 앞에 공백을 삽입합니다. <br /><br />`false` - 점 앞에서 공백을 제거합니다. |

코드 예제:

```csharp
// csharp_space_before_dot = true
this .Goo();

// csharp_space_before_dot = false
this.Goo();
```

#### <a name="csharp_space_after_semicolon_in_for_statement"></a>csharp_space_after_semicolon_in_for_statement

|속성|값|
|-|-|
| **규칙 이름** | csharp_space_after_semicolon_in_for_statement |
| **해당 언어** | C# |
| **값** | `true` - `for` 문의 각 세미콜론 뒤에 공백을 삽입합니다.<br /><br />`false` - `for` 문의 각 세미콜론 뒤에서 공백을 제거합니다. |

코드 예제:

```csharp
// csharp_space_after_semicolon_in_for_statement = true
for (int i = 0; i < x.Length; i++)

// csharp_space_after_semicolon_in_for_statement = false
for (int i = 0;i < x.Length;i++)
```

##### <a name="csharp_space_before_semicolon_in_for_statement"></a>csharp_space_before_semicolon_in_for_statement

|속성|값|
|-|-|
| **규칙 이름** | csharp_space_before_semicolon_in_for_statement |
| **해당 언어** | C# |
| **값** | `true` - `for` 문의 각 세미콜론 앞에 공백을 삽입합니다. <br /><br />`false` - `for` 문의 각 세미콜론 앞에서 공백을 제거합니다. |

코드 예제:

```csharp
// csharp_space_before_semicolon_in_for_statement = true
for (int i = 0 ; i < x.Length ; i++)

// csharp_space_before_semicolon_in_for_statement = false
for (int i = 0; i < x.Length; i++)
```

#### <a name="csharp_space_around_declaration_statements"></a>csharp_space_around_declaration_statements

|속성|값|
|-|-|
| **규칙 이름** | csharp_space_around_declaration_statements |
| **해당 언어** | C# |
| **값** | `ignore` - 선언문에서 추가 공백 문자를 제거하지 않습니다.<br /><br />`false` - 선언문에서 추가 공백 문자를 제거합니다. |

코드 예제:

```csharp
// csharp_space_around_declaration_statements = ignore
int    x    =    0   ;

// csharp_space_around_declaration_statements = false
int x = 0;
```

#### <a name="csharp_space_before_open_square_brackets"></a>csharp_space_before_open_square_brackets

|속성|값|
|-|-|
| **규칙 이름** | csharp_space_before_open_square_brackets |
| **해당 언어** | C# |
| **값** | `true` - 여는 대괄호 `[` 앞에 공백을 삽입합니다. <br /><br />`false` - 여는 대괄호 `[` 앞에서 공백을 제거합니다. |

코드 예제:

```csharp
// csharp_space_before_open_square_brackets = true
int [] numbers = new int [] { 1, 2, 3, 4, 5 };

// csharp_space_before_open_square_brackets = false
int[] numbers = new int[] { 1, 2, 3, 4, 5 };
```

#### <a name="csharp_space_between_empty_square_brackets"></a>csharp_space_between_empty_square_brackets

|속성|값|
|-|-|
| **규칙 이름** | csharp_space_between_empty_square_brackets |
| **해당 언어** | C# |
| **값** | `true` - 빈 대괄호 `[ ]` 사이에 공백을 삽입합니다. <br /><br />`false` - 빈 대괄호 `[]` 사이에서 공백을 제거합니다. |

코드 예제:

```csharp
// csharp_space_between_empty_square_brackets = true
int[ ] numbers = new int[ ] { 1, 2, 3, 4, 5 };

// csharp_space_between_empty_square_brackets = false
int[] numbers = new int[] { 1, 2, 3, 4, 5 };
```

#### <a name="csharp_space_between_square_brackets"></a>csharp_space_between_square_brackets

|속성|값|
|-|-|
| **규칙 이름** | csharp_space_between_square_brackets |
| **해당 언어** | C# |
| **값** | `true` - 비어 있지 않은 대괄호 `[ 0 ]` 안에 공백 문자를 삽입합니다. <br /><br />`false` - 비어 있지 않은 대괄호 `[0]` 안에서 공백 문자를 제거합니다. |

코드 예제:

```csharp
// csharp_space_between_square_brackets = true
int index = numbers[ 0 ];

// csharp_space_between_square_brackets = false
int index = numbers[0];
```

### <a name="wrap-options"></a>줄 바꿈 옵션

이러한 서식 설정 규칙은 문 및 코드 블록에 단일 줄 및 별도 줄을 사용하는 것을 다룹니다.

예제 *.editorconfig* 파일:

```ini
# CSharp formatting settings:
[*.cs]
csharp_preserve_single_line_statements = true
csharp_preserve_single_line_blocks = true
```

#### <a name="csharp_preserve_single_line_statements"></a>csharp_preserve_single_line_statements

|속성|값|
|-|-|
| **규칙 이름** | csharp_preserve_single_line_statements |
| **해당 언어** | C# |
| **도입된 버전** | Visual Studio 2017 15.3 버전 |
| **값** | `true` - 문과 멤버 선언을 동일한 줄에 유지합니다.<br /><br />`false` - 문과 멤버 선언을 다른 줄에 유지합니다. |

코드 예제:

```csharp
//csharp_preserve_single_line_statements = true
int i = 0; string name = "John";

//csharp_preserve_single_line_statements = false
int i = 0;
string name = "John";
```

#### <a name="csharp_preserve_single_line_blocks"></a>csharp_preserve_single_line_blocks

|속성|값|
|-|-|
| **규칙 이름** | csharp_preserve_single_line_blocks |
| **해당 언어** | C# |
| **도입된 버전** | Visual Studio 2017 15.3 버전 |
| **값** | `true` - 코드 블록을 한 줄에 유지합니다.<br /><br />`false` - 코드 블록을 새 줄에 유지합니다. |

코드 예제:

```csharp
//csharp_preserve_single_line_blocks = true
public int Foo { get; set; }

//csharp_preserve_single_line_blocks = false
public int MyProperty
{
    get; set;
}
```

### <a name="using-directive-options"></a>지시문 옵션 사용

이 서식 지정 규칙은 네임스페이스 내부에 배치거나 외부에 배치되는 지시문을 사용하는 것과 관련이 있습니다.

예제 *.editorconfig* 파일:

```ini
# 'using' directive preferences
[*.cs]
csharp_using_directive_placement = outside_namespace
csharp_using_directive_placement = inside_namespace
```

#### <a name="csharp_using_directive_placement"></a>csharp_using_directive_placement

|속성|값|
|-|-|
| **규칙 이름** | csharp_using_directive_placement |
| **해당 언어** | C# |
| **도입된 버전** | Visual Studio 2019 버전 16.1 |
| **값** | `outside_namespace` - 네임스페이스 외부에서 지시문을 사용<br /><br />`inside_namespace` - 네임스페이스 내부에서 지시문을 사용 |

코드 예제:

```csharp
// csharp_using_directive_placement = outside_namespace
using System;

namespace Conventions
{

}

// csharp_using_directive_placement = inside_namespace
namespace Conventions
{
    using System;
}
```

## <a name="see-also"></a>참조

- [언어 규칙](editorconfig-language-conventions.md)
- [명명 규칙](editorconfig-naming-conventions.md)
- [EditorConfig에 대한 .NET 코딩 규칙 설정](editorconfig-code-style-settings-reference.md)
