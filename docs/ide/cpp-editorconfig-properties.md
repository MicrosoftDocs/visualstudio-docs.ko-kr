---
title: C++ EditorConfig 서식 지정 규칙
titleSuffix: ''
description: Visual Studio에서 EditorConfig를 사용하여 C++ 코드의 서식을 지정하는 방법을 알아봅니다.
ms.date: 9/14/2020
author: jureid
ms.author: jureid
manager: jillfra
dev_langs:
- CPP
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: reference
ms.workload:
- cplusplus
monikerRange: vs-2019
ms.openlocfilehash: 31a7db73a4487267c2a74fe628d28b577d339aba
ms.sourcegitcommit: 14637be49401f56341c93043eab560a4ff6b57f6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/14/2020
ms.locfileid: "90078985"
---
# <a name="c-editorconfig-formatting-conventions"></a>C++ EditorConfig 서식 지정 규칙

Visual Studio C++ 포맷터에는 전역적으로 적용할 수 있는 다양한 구성 가능한 설정이 있습니다. 특정 작업 영역에 대한 C++ 서식 설정을 지정하려면 [clangformat](https://clang.llvm.org/docs/ClangFormat.html) 또는 [EditorConfig](https://editorconfig.org/)를 사용합니다. Visual Studio 및 Visual Studio Code는 각 전역 Visual Studio C++ 서식 설정에 대한 EditorConfig 지원을 기본적으로 제공하며 EditorConfig 설정은 우선적으로 적용됩니다. 즉, 작업 영역에 EditorConfig 파일을 추가하여 더 세부적인 수준에서 C++ 서식 지정을 구성하고 프로젝트에 참가하는 모든 사용자에게 일관된 코드 스타일을 적용할 수 있습니다.

## <a name="c-formatting-conventions"></a>C++ 서식 지정 규칙

EditorConfig C++ 서식 설정에는 `_cpp__` 접두사가 붙습니다. 다음은 EditorConfig 파일 예제입니다.

```ini
[\*.{c++,cc,cpp,cxx,h,h++,hh,hpp,hxx,inl,ipp,tlh,tli}]

cpp_indent_case_contents_when_block = true
cpp_new_line_before_open_brace_namespace = same_line
```

이 문서의 나머지 부분에는 Visual Studio 및 VS Code에서 지원하는 모든 EditorConfig C++ 서식 설정이 나열되어 있습니다.

### <a name="indentation-settings"></a>들여쓰기 설정

**중괄호 들여쓰기**

- 이름: `cpp_indent_braces`
- 값: `true`, `false`

**다음에 상대적으로 각 줄 들여쓰기**

- 이름: `cpp_indent_multi_line_relative_to`
- 값
  - `outermost_parenthesis` - 새 줄이 입력되면 가장 바깥쪽 여는 괄호에 상대적으로 줄을 들여씁니다.
  - `innermost_parenthesis` - 새 줄이 입력되면 가장 안쪽의 여는 괄호에 상대적으로 줄을 들여씁니다.
  - `statement_begin` - 새 줄이 입력되면 현재 문의 시작 부분에 상대적으로 줄을 들여씁니다.

**괄호 안에서 새 줄 입력 시 맞춤**

- 이름: `cpp_indent_within_parentheses`
- 값
  - `align_to_parenthesis` - 여는 괄호에 내용을 맞춥니다.
  - `indent` - 새 줄을 들여씁니다.

**기존 코드에서 괄호 안의 새 줄 맞춤에 대한 설정을 사용하지 않음**

- 이름: `cpp_indent_preserve_within_parentheses`
- 값: `true`, `false`

**case 내용 들여쓰기**

- 이름: `cpp_indent_case_contents`
- 값: `true`, `false`

**case 레이블 들여쓰기**

- 이름: `cpp_indent_case_labels`
- 값: `true`, `false`

**case 문 다음에 중괄호 들여쓰기**

- 이름: `cpp_indent_case_contents_when_block`
- 값: `true`, `false`

**매개 변수로 사용되는 람다의 중괄호 들여쓰기**

- 이름: `cpp_indent_lambda_braces_when_parameter`
- 값: `true`, `false`

**goto 레이블의 위치**

- 이름: `cpp_indent_goto_labels`
- 값
  - `one_left` - 왼쪽으로 한 수준 들여씁니다.
  - `leftmost_column` - 맨 왼쪽 열로 이동합니다.
  - `none` - 들여쓰기를 유지합니다.

**전처리기 지시문의 위치**

- 이름: `cpp_indent_preprocessor`
- 값
  - `one_left` - 왼쪽으로 한 수준 들여씁니다.
  - `leftmost_column` - 맨 왼쪽 열로 이동합니다.
  - `none` - 들여쓰기를 유지합니다.

**액세스 지정자 들여쓰기**

- 이름: `cpp_indent_access_specifiers`
- 값: `true`, `false`

**네임스페이스 내용 들여쓰기**

- 이름: `cpp_indent_namespace_contents`
- 값: `true`, `false`

**주석의 들여쓰기 유지**

- 이름: `cpp_indent_preserve_comments`
- 값: `true`, `false`

### <a name="newline-settings"></a>줄 바꿈 설정

**네임스페이스의 여는 중괄호 위치**

- 이름: `cpp_new_line_before_open_brace_namespace`
- 값
  - `new_line` - 새 줄로 이동합니다.
  - `same_line` - 같은 줄에 유지하되 앞에 공백을 추가합니다.
  - `ignore` - 위치를 자동으로 변경하지 않습니다.

**형식의 여는 중괄호 위치**

- 이름: `cpp_new_line_before_open_brace_type`
- 값
  - `new_line` - 새 줄로 이동합니다.
  - `same_line` - 같은 줄에 유지하되 앞에 공백을 추가합니다.
  - `ignore` - 위치를 자동으로 변경하지 않습니다.

**함수의 여는 중괄호 위치**

- 이름: `cpp_new_line_before_open_brace_function`
- 값
  - `new_line` - 새 줄로 이동합니다.
  - `same_line` - 같은 줄에 유지하되 앞에 공백을 추가합니다.
  - `ignore` - 위치를 자동으로 변경하지 않습니다.

**제어 블록의 여는 중괄호 위치**

- 이름: `cpp_new_line_before_open_brace_block`
- 값
  - `new_line` - 새 줄로 이동합니다.
  - `same_line` - 같은 줄에 유지하되 앞에 공백을 추가합니다.
  - `ignore` - 위치를 자동으로 변경하지 않습니다.

**람다의 여는 중괄호 위치**

- 이름: `cpp_new_line_before_open_brace_lambda`
- 값
  - `new_line` - 새 줄로 이동합니다.
  - `same_line` - 같은 줄에 유지하되 앞에 공백을 추가합니다.
  - `ignore` - 위치를 자동으로 변경하지 않습니다.
 
**범위 중괄호를 별도의 줄에 배치**

- 이름: `cpp_new_line_scope_braces_on_separate_lines`
- 값: `true`, `false`

**빈 형식의 경우 닫는 중괄호를 여는 중괄호와 같은 줄로 이동**

- 이름: `cpp_new_line_close_brace_same_line_empty_type`
- 값: `true`, `false`

**빈 함수 본문의 경우 닫는 중괄호를 여는 중괄호와 같은 줄로 이동**

- 이름: `cpp_new_line_close_brace_same_line_empty_function`
- 값: `true`, `false`

**'catch' 및 유사한 키워드를 새 줄에 배치**

- 이름: `cpp_new_line_before_catch`
- 값: `true`, `false`

**'else'를 새 줄에 배치**

- 이름: `cpp_new_line_before_else`
- 값: `true`, `false`

**do-while 루프의 'while'을 새 줄에 배치**

- 이름: `cpp_new_line_before_while_in_do_while`
- 값: `true`, `false`

### <a name="spacing-settings"></a>간격 설정

**함수 이름과 인수 목록의 여는 괄호 사이의 간격**

- 이름: `cpp_space_before_function_open_parenthesis`
- 값
  - `insert` - 공백을 삽입합니다.
  - `remove` - 공백을 제거합니다.
  - `ignore` - 공백을 변경하지 않습니다.

**인수 목록의 괄호 내부에 공백 삽입**

- 이름: `cpp_space_within_parameter_list_parentheses` 값: `true`, `false`

**인수 목록이 비어 있을 때 괄호 사이에 공백 삽입**

- 이름: `cpp_space_between_empty_parameter_list_parentheses`
- 값: `true`, `false`

**제어 흐름 문의 키워드와 여는 괄호 사이에 공백 삽입**

- 이름: `cpp_space_after_keywords_in_control_flow_statements`
- 값: `true`, `false`

**제어 문의 괄호 내부에 공백 삽입**

- 이름: `cpp_space_within_control_flow_statement_parentheses`
- 값: `true`, `false`

**람다 인수 목록의 여는 괄호 앞에 공백 삽입**

- 이름: `cpp_space_before_lambda_open_parenthesis`
- 값: `true`, `false`

**식 괄호 내부에 공백 삽입**

- 이름: `cpp_space_within_cast_parentheses`
- 값: `true`, `false`

**C 스타일 캐스트의 닫는 괄호 뒤에 공백 삽입**

- 이름: `cpp_space_after_cast_close_parenthesis`
- 값: `true`, `false`

**괄호로 묶은 식의 괄호 내부에 공백 삽입**

- 이름: `cpp_space_within_expression_parentheses`
- 값: `true`, `false`

**블록의 여는 중괄호 앞에 공백 삽입**

- 이름: `cpp_space_before_block_open_brace`
- 값: `true`, `false`

**빈 중괄호 사이에 공백 삽입**

- 이름: `cpp_space_between_empty_braces`
- 값: `true`, `false`

**균일한 초기화 및 이니셜라이저 목록의 여는 중괄호 앞에 공백 삽입**

- 이름: `cpp_space_before_initializer_list_open_brace`
- 값: `true`, `false`

**균일한 초기화 및 이니셜라이저 목록의 중괄호 내부에 공백 삽입**

- 이름: `cpp_space_within_initializer_list_braces`
- 값: `true`, `false`

**균일한 초기화 및 이니셜라이저 목록 내부에 공백 유지**

- 이름: `cpp_space_preserve_in_initializer_list`
- 값: `true`, `false`

**여는 대괄호 앞에 공백 삽입**

- 이름: `cpp_space_before_open_square_bracket`
- 값: `true`, `false`

**대괄호 내부에 공백 삽입**

- 이름: `cpp_space_within_square_brackets`
- 값: `true`, `false`

**빈 대괄호 앞에 공백 삽입**

- 이름: `cpp_space_before_empty_square_brackets`
- 값: `true`, `false`

**빈 대괄호 사이에 공백 삽입**

- 이름: `cpp_space_between_empty_square_brackets`
- 값: `true`, `false`

**다차원 배열을 위한 대괄호를 그룹으로 묶음**

- 이름: `cpp_space_group_square_brackets`
- 값: `true`, `false`

**람다의 대괄호 내부에 공백 삽입**

- 이름: `cpp_space_within_lambda_brackets`
- 값: `true`, `false`

**SpaceBetweenEmptyLambdaBrackets**

- 이름: `cpp_space_between_empty_lambda_brackets`
- 값: `true`, `false`

**쉼표 앞에 공백 삽입**

- 이름: `cpp_space_before_comma`
- 값: `true`, `false`

**쉼표 뒤에 공백 삽입**

- 이름: `cpp_space_after_comma`
- 값: `true`, `false`

**멤버 연산자 앞뒤의 공백 제거**

- 이름: `cpp_space_remove_around_member_operators`
- 값: `true`, `false`

**형식 선언에서 기본에 대한 콜론 앞에 공백 삽입**

- 이름: `cpp_space_before_inheritance_colon`
- 값: `true`, `false`

**생성자의 콜론 앞에 공백 삽입**

- 이름: `cpp_space_before_constructor_colon`
- 값: `true`, `false`

**세미콜론 앞의 공백 제거**

- 이름: `cpp_space_remove_before_semicolon`
- 값: `true`, `false`

**세미콜론 뒤에 공백 삽입**

- 이름: `cpp_space_after_semicolon`
- 값: `true`, `false`

**단항 연산자와 해당 피연산자 사이의 공백 제거**

- 이름: `cpp_space_remove_around_unary_operator`
- 값: `true`, `false`

**이항 연산자의 간격**

- 이름: `cpp_space_around_binary_operator`
- 값
  - `insert` - 이항 연산자의 앞뒤에 공백을 삽입합니다.
  - `remove` - 이항 연산자 주위의 공백을 제거합니다.
  - `ignore` - 이항 연산자 주위의 공백을 변경하지 않습니다.

**대입 연산자의 간격**

- 이름: `cpp_space_around_assignment_operator`
- 값
  - `insert` - 대입 연산자 주위에 공백을 삽입합니다.
  - `remove` - 대입 연산자 주위의 공백을 제거합니다.
  - `ignore` - 대입 연산자 주위의 공백을 변경하지 않습니다.

**포인터/참조 맞춤**

- 이름: `cpp_space_pointer_reference_alignment`
- 값
  - `left` - 왼쪽에 맞춥니다.
  - `center` - 가운데에 맞춥니다.
  - `right` - 오른쪽에 맞춥니다.
  - `ignore` - 변경하지 않은 상태로 유지합니다.

**조건 연산자의 간격**

- 이름: `cpp_space_around_ternary_operator`
- 값
  - `insert` - 조건 연산자 주위에 공백을 삽입합니다.
  - `remove` - 조건 연산자 주위의 공백을 제거합니다.
  - `ignore` - 조건 연산자 주위의 공백을 변경하지 않습니다.

### <a name="wrapping-options"></a>래핑 옵션

**블록에 대한 래핑 옵션**

- 이름: `cpp_wrap_preserve_blocks`
- 값
  - `one_liners` - 한 줄 코드 블록을 자동으로 래핑하지 않습니다.
  - `all_one_line_scopes` - 여는 중괄호와 닫는 중괄호가 다음 줄에 있는 코드 블록을 자동 래핑하지 않습니다.
  - `never` - 블록에 항상 줄 바꿈 설정을 적용합니다.

## <a name="see-also"></a>추가 정보

- [EditorConfig.org](https://editorconfig.org/)
- [언어 서비스를 위한 EditorConfig 지원](../extensibility/supporting-editorconfig.md)
- [코드 편집기의 기능](writing-code-in-the-code-and-text-editor.md)
