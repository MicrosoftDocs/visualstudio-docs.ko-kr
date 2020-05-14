---
title: C# 편집기 서식 지정 옵션
ms.date: 08/14/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Spacing
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.NewLines
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Indentation
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Wrapping
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.CSharp.Code_Style.Formatting.General
helpviewer_keywords:
- formatting options [C#]
- Text editor Options dialog box, formatting
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 1176232eb3354a9b425e9432eb83037367ee7706
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79307300"
---
# <a name="options-dialog-box-text-editor--c--code-style--formatting"></a>옵션 대화 상자: 텍스트 편집기 \> C# \> 코드 스타일 \> 서식

**서식 지정** 옵션 페이지와 하위 페이지([**들여쓰기**](#indentation-page), **줄 추가**, **여백**, **래핑**)를 사용하여 코드 편집기에서 코드 서식 지정을 위한 옵션을 설정합니다.

이 옵션 페이지에 액세스하려면 메뉴 모음에서 **도구** > **옵션**을 선택합니다. **옵션** 대화 상자에서 **텍스트 편집기** > **C#**  > **코드 스타일** > **서식 지정**을 선택합니다.

> [!TIP]
> **들여쓰기**, **줄 추가**, **간격** 및 **래핑** 하위 페이지의 아래에는 각 옵션의 효과를 나타내는 미리 보기 창이 표시됩니다. 미리 보기 창을 사용하려면 서식 옵션을 선택합니다. 미리 보기 창에는 선택된 옵션의 예제가 표시됩니다. 라디오 단추 또는 확인란을 선택하여 설정을 변경하면 미리 보기 창이 업데이트되어 새 설정의 효과가 표시됩니다.

## <a name="formatting-general-page"></a>서식 지정(일반) 페이지

### <a name="general-settings"></a>일반 설정

이 설정은 코드 편집기가 서식 옵션을 코드에 적용하는 *시기*에 영향을 미칩니다.

|레이블|설명|
|-----------|-----------------|
|**입력할 때 서식 자동 지정**|이 옵션을 선택 취소하면 **입력 시 문 서식 지정;** 및 **입력 시 블록 서식 지정}** 옵션이 비활성화됩니다.|
|**입력 시 문 서식 자동 지정;**|이 옵션을 선택하면 편집기에 대해 선택된 서식 옵션에 따라 완성 시 문에 서식이 지정됩니다.|
|**입력 시 블록 서식 자동 지정}**|이 옵션을 선택하면 코드 블록을 완료하면 바로 편집기에 대해 선택된 서식 옵션에 따라 코드 블록에 서식이 지정됩니다.|
|**반환할 때 서식 자동 지정**|이 옵션을 선택하면 **Enter** 키를 누를 때 텍스트가 편집기에 대해 선택된 서식 옵션에 맞게 서식 지정됩니다.|
|**붙여넣을 때 서식 자동 지정**|이 옵션을 선택하면 편집기에 대해 선택된 서식 옵션에 맞게 편집기에 붙여넣는 텍스트에 서식이 지정됩니다.|

::: moniker range="vs-2019"

이전에 Visual Studio 2017에서 **Format Document** 명령을 사용하여 C# 파일에 코드 스타일 설정을 적용한 경우 이제 이 기능을 [**Code Cleanup**](../code-styles-and-code-cleanup.md#apply-code-styles)으로 사용할 수 있습니다.

::: moniker-end

::: moniker range="vs-2017"

### <a name="format-document-settings"></a>문서 서식 설정

이러한 설정은 파일에서 추가 코드 정리를 수행하는 **문서 서식** 명령을 구성합니다. 이러한 설정을 적용하는 방법에 대한 자세한 내용은 [문서 서식 명령](../code-styles-and-code-cleanup.md#apply-code-styles)을 참조하세요.

|레이블|설명|해당 EditorConfig 및 도구 > 옵션 규칙|
|-----------|-----------------|-----------------|-----------------|
|**모든 C# 서식 규칙 적용(들여쓰기, 줄 바꿈, 간격)**|**문서 서식** 명령은 항상 서식 지정 문제를 수정합니다. 이 설정은 변경할 수 없습니다.| [핵심 EditorConfig 옵션](../../ide/create-portable-custom-editor-options.md)<br/>[.NET EditorConfig 서식 지정 옵션](../../ide/editorconfig-formatting-conventions.md)<br/><br/>**도구** > **옵션** > **텍스트 편집기** > **C#**  > **서식 지정** > [**들여쓰기** 또는 **새 줄** 또는 **간격** 또는 **래핑**]|
|**서식을 지정하는 동안 추가 코드 정리 수행**|이 옵션을 선택하면 **Edit.FormatDocument** 명령 아래에 지정된 규칙에 대한 수정 사항을 적용합니다.| N/A |
|**불필요한 Using 제거**|이 옵션을 선택하면 **Edit.FormatDocument**를 트리거할 때 불필요한 `using` 지시문을 제거합니다.| N/A |
|**using 정렬**|이 옵션을 선택하면 **Edit.FormatDocument**를 트리거할 때 `using` 지시문을 정렬합니다.| dotnet_sort_system_directives_first<br/><br/>**도구** > **옵션** > **텍스트 편집기** > **C#**  > **고급** > **using 정렬 시 먼저 'System' 지시문 정렬** |
|**단일 줄 제어문에 대해 중괄호 추가/제거**|옵션을 선택하면 **Edit.FormatDocument**를 트리거할 때 단일 줄 제어문에서 중괄호를 추가하거나 제거합니다.| csharp_prefer_braces<br/><br/>**도구** > **옵션** > **텍스트 편집기** > **C#**  > **코드 스타일** > **코드 블록 기본 설정** > **중괄호 기본 사용** |
|**내게 필요한 옵션 한정자 추가**|옵션을 선택하면 **Edit.FormatDocument**를 트리거할 때 누락된 내게 필요한 옵션 한정자를 추가합니다.| dotnet_style_require_accessibility_modifiers |
|**내게 필요한 옵션 한정자 정렬**|옵션을 선택하면 **Edit.FormatDocument**를 트리거할 때 내게 필요한 옵션 한정자를 정렬합니다.| csharp_preferred_modifier_order<br/>visual_basic_preferred_modifier_order |
|**식/블록 본문 기본 설정 적용**|옵션을 선택하면 **Edit.FormatDocument**를 트리거할 때 본문을 차단하거나 반대로 수행하도록 식 본문 멤버를 변환합니다.| [식 본문 멤버 EditorConfig 옵션](../../ide/editorconfig-language-conventions.md#expression-bodied-members)<br/><br/>**도구** > **옵션** > **텍스트 편집기** > **C#**  > **코드 스타일** > **식 기본 설정** > **메서드, 생성자 등에 식 본문 사용** |
|**암시적/명시적 형식 기본 설정 적용**|옵션을 선택하면 **Edit.FormatDocument**를 트리거할 때 `var`를 명시적 형식 또는 반대로 변환합니다.| [명시적 형식 EditorConfig 옵션](../../ide/editorconfig-language-conventions.md#implicit-and-explicit-types)<br/><br/>**도구** > **옵션** > **텍스트 편집기** > **C#**  > **코드 스타일** >  **'var' 기본 설정** |
|**인라인 'out' 변수 기본 설정 적용**|옵션을 선택하면 **Edit.FormatDocument**를 트리거할 때 가능한 경우 `out` 변수를 인라인합니다.| csharp_style_inlined_variable_declaration<br/><br/>**도구** > **옵션** > **텍스트 편집기** > **C#**  > **코드 스타일** > **변수 기본 설정** > **인라인 변수 선언 기본 사용** |
|**언어/프레임워크 형식 기본 설정 적용**|옵션을 선택하면 **Edit.FormatDocument**를 트리거할 때 언어 형식을 프레임워크 형식으로 또는 반대로 변환합니다.| dotnet_style_predefined_type_for_locals_parameters_members<br/>dotnet_style_predefined_type_for_member_access<br/><br/>**도구** > **옵션** > **텍스트 편집기** > **C#**  > **코드 스타일** > **미리 정의된 형식 기본 설정** |
|**개체/컬렉션 초기화 기본 설정 적용**|옵션을 선택하면 **Edit.FormatDocument**를 트리거할 때 가능한 경우 개체 및 컬렉션 이니셜라이저를 사용합니다.| dotnet_style_object_initializer<br/>dotnet_style_collection_initializer<br/><br/>**도구** > **옵션** > **텍스트 편집기** > **C#**  > **코드 스타일** > **식 기본 설정** > **개체 이니셜라이저 기본 사용** 또는 **컬렉션 이니셜라이저 기본 사용** |
|**'this.' 한정자 기본 설정 적용**|이 옵션을 선택하면 **Edit.FormatDocument**를 트리거할 때 `this.` 기본 설정을 적용합니다.| [this. 한정자 EditorConfig 옵션](../../ide/editorconfig-language-conventions.md#this-and-me)<br/><br/>**도구** > **옵션** > **텍스트 편집기** > **C#**  > **코드 스타일** >  **'this.' 기본 설정** |
|**가능한 경우 전용 필드를 읽기 전용으로 만들기**|옵션을 선택하면 **Edit.FormatDocument**를 트리거할 때 가능한 경우 전용 필드를 `readonly`로 만듭니다.| dotnet_style_readonly_field<br/><br/>**도구** > **옵션** > **텍스트 편집기** > **C#**  > **코드 스타일** > **필드 기본 설정** > **읽기 전용 기본 사용** |
|**불필요한 캐스트 제거**|이 옵션을 선택하면 **Edit.FormatDocument**를 트리거할 때 불필요한 캐스트를 제거합니다.| N/A |
|**사용하지 않는 변수 제거**|이 옵션을 선택하면 **Edit.FormatDocument**를 트리거할 때 사용하지 않는 변수를 제거합니다.| N/A |

![Visual Studio에서 C#에 대한 코드 정리 설정](media/format-document-settings.png)

::: moniker-end

## <a name="indentation-page"></a>들여쓰기 페이지

이 페이지의 들여쓰기 옵션은 코드 서식이 자동으로 지정되는 경우 적용됩니다. **붙여넣을 때 서식 자동 지정**을 선택했을 때 파일에 코드를 붙여넣으면 코드의 서식이 자동으로 지정되는 것을 예로 들 수 있습니다. (**붙여넣을 때 서식 자동 지정** 옵션은 **서식 지정** > **일반**에 있습니다.)

![Visual Studio의 C# 텍스트 편집기 들여쓰기 옵션](media/csharp-indentation-options.png)

> [!TIP]
> 들여쓰기 옵션도 **텍스트 편집기** > **C#**  > **탭** 옵션 페이지에 있습니다. 이러한 옵션은 줄 끝에서 **Enter** 키를 누를 때 코드 편집기에서 커서를 배치하는 위치만을 결정합니다.
>
> ![Visual Studio의 C# 텍스트 편집기 탭 옵션](media/csharp-tabs-options.png)

## <a name="see-also"></a>참조

- [일반, 환경, 옵션 대화 상자](../../ide/reference/general-environment-options-dialog-box.md)
