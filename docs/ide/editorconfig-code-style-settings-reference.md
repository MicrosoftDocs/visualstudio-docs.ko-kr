---
title: EditorConfig에 대한 .NET 코딩 규칙 설정
ms.date: 03/17/2020
ms.topic: reference
helpviewer_keywords:
- coding conventions [EditorConfig]
- EditorConfig coding conventions
- language code style rules [EditorConfig]
- formatting conventions [EditorConfig]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 41d183a757aefd198c282ec84cd6cbe0ef37c933
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79508955"
---
# <a name="net-coding-convention-settings-for-editorconfig"></a>EditorConfig에 대한 .NET 코딩 규칙 설정

[EditorConfig](../ide/create-portable-custom-editor-options.md) 파일을 사용하여 코드베이스에서 일관된 코드 스타일을 정의하고 유지 관리할 수 있습니다. EditorConfig에는 `indent_style` 및 `indent_size`와 같은 여러 가지 주요 서식 지정 속성이 포함됩니다. Visual Studio에서 EditorConfig 파일을 사용하여 .NET 코딩 규칙 설정을 구성할 수도 있습니다. 개별 .NET 코딩 규칙을 사용하거나 사용하지 않도록 설정하고 심각도 수준을 통해 각 규칙을 적용하려는 수준을 구성할 수 있습니다.

> [!TIP]
> - EditorConfig 파일에서 코딩 규칙을 정의하는 경우, Visual Studio에 빌드된 [코드 스타일 분석기](../code-quality/roslyn-analyzers-overview.md)의 코드 분석 방법을 구성하는 것입니다. EditorConfig 파일은 이러한 분석기의 구성 파일입니다.
> - Visual Studio의 코드 스타일 기본 설정은 [텍스트 편집기 옵션](code-styles-and-code-cleanup.md) 대화 상자에서 설정할 수도 있습니다. 하지만 EditorConfig 설정이 우선 적용되며, **옵션**에서 설정한 기본 설정은 특정 프로젝트에 연결되지 않습니다.

## <a name="convention-categories"></a>규칙 범주

지원되는 .NET 코딩 규칙 범주에는 세 가지가 있습니다.

- [언어 규칙](../ide/editorconfig-language-conventions.md)

   C# 또는 Visual Basic 언어에 관련된 규칙입니다. 예를 들어 변수를 정의하거나 식 본문 멤버를 사용하는 것이 좋은 경우 `var` 또는 명시적 형식을 사용하여 규칙을 지정할 수 있습니다.

- [서식 지정 규칙](../ide/editorconfig-formatting-conventions.md)

   보다 쉽게 읽을 수 있기 위한 코드의 레이아웃 및 구조체와 관련된 규칙입니다. 예를 들어 제어 블록에서 Allman 중괄호 또는 공백을 사용하는 규칙을 지정할 수 있습니다.

- [명명 규칙](../ide/editorconfig-naming-conventions.md)

   코드 요소의 명명과 관련된 규칙입니다. 예를 들어 `async` 메서드가 "Async"로 끝나야 하는지를 지정할 수 있습니다.

## <a name="example-editorconfig-file"></a>예제 EditorConfig 파일

다음은 시작하는 데 도움이 되는 기본 옵션의 예제 *.editorconfig* 파일입니다. Visual Studio에서 이 파일을 생성하고 **도구** > **옵션** > **텍스트 편집기** > [**C#** 또는 **기본**] > **코드 스타일** > **일반**에서 프로젝트에 저장할 수 있습니다. 그런 다음 **설정에서 .editorconfig 파일 생성** 단추를 클릭합니다. 자세한 내용은 [코드 스타일 기본 설정](code-styles-and-code-cleanup.md)을 참조하세요.

```ini
# Remove the line below if you want to inherit .editorconfig settings from higher directories
root = true

# C# files
[*.cs]

#### Core EditorConfig Options ####

# Indentation and spacing
indent_size = 4
indent_style = space
tab_width = 4

# New line preferences
end_of_line = crlf
insert_final_newline = false

#### .NET Coding Conventions ####

# Organize usings
dotnet_separate_import_directive_groups = false
dotnet_sort_system_directives_first = false

# this. and Me. preferences
dotnet_style_qualification_for_event = false:silent
dotnet_style_qualification_for_field = false:silent
dotnet_style_qualification_for_method = false:silent
dotnet_style_qualification_for_property = false:silent

# Language keywords vs BCL types preferences
dotnet_style_predefined_type_for_locals_parameters_members = true:silent
dotnet_style_predefined_type_for_member_access = true:silent

# Parentheses preferences
dotnet_style_parentheses_in_arithmetic_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_other_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_other_operators = never_if_unnecessary:silent
dotnet_style_parentheses_in_relational_binary_operators = always_for_clarity:silent

# Modifier preferences
dotnet_style_require_accessibility_modifiers = for_non_interface_members:silent

# Expression-level preferences
dotnet_style_coalesce_expression = true:suggestion
dotnet_style_collection_initializer = true:suggestion
dotnet_style_explicit_tuple_names = true:suggestion
dotnet_style_null_propagation = true:suggestion
dotnet_style_object_initializer = true:suggestion
dotnet_style_prefer_auto_properties = true:silent
dotnet_style_prefer_compound_assignment = true:suggestion
dotnet_style_prefer_conditional_expression_over_assignment = true:silent
dotnet_style_prefer_conditional_expression_over_return = true:silent
dotnet_style_prefer_inferred_anonymous_type_member_names = true:suggestion
dotnet_style_prefer_inferred_tuple_names = true:suggestion
dotnet_style_prefer_is_null_check_over_reference_equality_method = true:suggestion
dotnet_style_prefer_simplified_interpolation = true:suggestion

# Field preferences
dotnet_style_readonly_field = true:suggestion

# Parameter preferences
dotnet_code_quality_unused_parameters = all:suggestion

#### C# Coding Conventions ####

# var preferences
csharp_style_var_elsewhere = false:silent
csharp_style_var_for_built_in_types = false:silent
csharp_style_var_when_type_is_apparent = false:silent

# Expression-bodied members
csharp_style_expression_bodied_accessors = true:silent
csharp_style_expression_bodied_constructors = false:silent
csharp_style_expression_bodied_indexers = true:silent
csharp_style_expression_bodied_lambdas = true:silent
csharp_style_expression_bodied_local_functions = false:silent
csharp_style_expression_bodied_methods = false:silent
csharp_style_expression_bodied_operators = false:silent
csharp_style_expression_bodied_properties = true:silent

# Pattern matching preferences
csharp_style_pattern_matching_over_as_with_null_check = true:suggestion
csharp_style_pattern_matching_over_is_with_cast_check = true:suggestion
csharp_style_prefer_switch_expression = true:suggestion

# Null-checking preferences
csharp_style_conditional_delegate_call = true:suggestion

# Modifier preferences
csharp_prefer_static_local_function = true:suggestion
csharp_preferred_modifier_order = public,private,protected,internal,static,extern,new,virtual,abstract,sealed,override,readonly,unsafe,volatile,async:silent

# Code-block preferences
csharp_prefer_braces = true:silent
csharp_prefer_simple_using_statement = true:suggestion

# Expression-level preferences
csharp_prefer_simple_default_expression = true:suggestion
csharp_style_deconstructed_variable_declaration = true:suggestion
csharp_style_inlined_variable_declaration = true:suggestion
csharp_style_pattern_local_over_anonymous_function = true:suggestion
csharp_style_prefer_index_operator = true:suggestion
csharp_style_prefer_range_operator = true:suggestion
csharp_style_throw_expression = true:suggestion
csharp_style_unused_value_assignment_preference = discard_variable:suggestion
csharp_style_unused_value_expression_statement_preference = discard_variable:silent

# 'using' directive preferences
csharp_using_directive_placement = outside_namespace:silent

#### C# Formatting Rules ####

# New line preferences
csharp_new_line_before_catch = true
csharp_new_line_before_else = true
csharp_new_line_before_finally = true
csharp_new_line_before_members_in_anonymous_types = true
csharp_new_line_before_members_in_object_initializers = true
csharp_new_line_before_open_brace = all
csharp_new_line_between_query_expression_clauses = true

# Indentation preferences
csharp_indent_block_contents = true
csharp_indent_braces = false
csharp_indent_case_contents = true
csharp_indent_case_contents_when_block = true
csharp_indent_labels = one_less_than_current
csharp_indent_switch_labels = true

# Space preferences
csharp_space_after_cast = false
csharp_space_after_colon_in_inheritance_clause = true
csharp_space_after_comma = true
csharp_space_after_dot = false
csharp_space_after_keywords_in_control_flow_statements = true
csharp_space_after_semicolon_in_for_statement = true
csharp_space_around_binary_operators = before_and_after
csharp_space_around_declaration_statements = false
csharp_space_before_colon_in_inheritance_clause = true
csharp_space_before_comma = false
csharp_space_before_dot = false
csharp_space_before_open_square_brackets = false
csharp_space_before_semicolon_in_for_statement = false
csharp_space_between_empty_square_brackets = false
csharp_space_between_method_call_empty_parameter_list_parentheses = false
csharp_space_between_method_call_name_and_opening_parenthesis = false
csharp_space_between_method_call_parameter_list_parentheses = false
csharp_space_between_method_declaration_empty_parameter_list_parentheses = false
csharp_space_between_method_declaration_name_and_open_parenthesis = false
csharp_space_between_method_declaration_parameter_list_parentheses = false
csharp_space_between_parentheses = false
csharp_space_between_square_brackets = false

# Wrapping preferences
csharp_preserve_single_line_blocks = true
csharp_preserve_single_line_statements = true

#### Naming styles ####

# Naming rules

dotnet_naming_rule.interface_should_be_begins_with_i.severity = suggestion
dotnet_naming_rule.interface_should_be_begins_with_i.symbols = interface
dotnet_naming_rule.interface_should_be_begins_with_i.style = begins_with_i

dotnet_naming_rule.types_should_be_pascal_case.severity = suggestion
dotnet_naming_rule.types_should_be_pascal_case.symbols = types
dotnet_naming_rule.types_should_be_pascal_case.style = pascal_case

dotnet_naming_rule.non_field_members_should_be_pascal_case.severity = suggestion
dotnet_naming_rule.non_field_members_should_be_pascal_case.symbols = non_field_members
dotnet_naming_rule.non_field_members_should_be_pascal_case.style = pascal_case

# Symbol specifications

dotnet_naming_symbols.interface.applicable_kinds = interface
dotnet_naming_symbols.interface.applicable_accessibilities = public, internal, private, protected, protected_internal, private_protected
dotnet_naming_symbols.interface.required_modifiers =

dotnet_naming_symbols.types.applicable_kinds = class, struct, interface, enum
dotnet_naming_symbols.types.applicable_accessibilities = public, internal, private, protected, protected_internal, private_protected
dotnet_naming_symbols.types.required_modifiers =

dotnet_naming_symbols.non_field_members.applicable_kinds = property, event, method
dotnet_naming_symbols.non_field_members.applicable_accessibilities = public, internal, private, protected, protected_internal, private_protected
dotnet_naming_symbols.non_field_members.required_modifiers =

# Naming styles

dotnet_naming_style.pascal_case.required_prefix =
dotnet_naming_style.pascal_case.required_suffix =
dotnet_naming_style.pascal_case.word_separator =
dotnet_naming_style.pascal_case.capitalization = pascal_case

dotnet_naming_style.begins_with_i.required_prefix = I
dotnet_naming_style.begins_with_i.required_suffix =
dotnet_naming_style.begins_with_i.word_separator =
dotnet_naming_style.begins_with_i.capitalization = pascal_case
```

> [!NOTE]
> 지원되는 .NET 코딩 규칙 범주에 대한 자세한 내용은 [언어 규칙](../ide/editorconfig-language-conventions.md), [서식 지정 규칙](../ide/editorconfig-formatting-conventions.md) 및 [명명 규칙](../ide/editorconfig-naming-conventions.md) 페이지를 참조하세요.

## <a name="see-also"></a>참조

- [빠른 작업](../ide/quick-actions.md)
- [휴대용, 사용자 지정 편집기 옵션 만들기](../ide/create-portable-custom-editor-options.md)
- [.NET Compiler Platform “Roslyn” .editorconfig 파일](https://github.com/dotnet/roslyn/blob/master/.editorconfig)
- [.NET Compiler Platform 런타임 .editorconfig 파일](https://github.com/dotnet/runtime/blob/master/.editorconfig)
