---
title: EditorConfig 설정
ms.date: 09/02/2020
ms.topic: how-to
helpviewer_keywords:
- editorconfig [Visual Studio]
author: mikadumont
ms.author: midumont
manager: jillfra
ms.openlocfilehash: 59e226fc0cc09b1eda5197d6accddfa9bd1a20ed
ms.sourcegitcommit: 703c68667261df5985a73282c1cbb0541118989c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "89402259"
---
# <a name="create-portable-custom-editor-settings-with-editorconfig"></a>EditorConfig를 사용하여 휴대용, 사용자 지정 편집기 설정 만들기

프로젝트 또는 코드베이스에 EditorConfig 파일을 추가하여 코드베이스에서 작업하는 모든 사람들의 코딩 스타일을 일관적으로 유지할 수 있습니다. EditorConfig 설정은 전역 Visual Studio 텍스트 편집기 설정에 우선합니다. 따라서 해당 프로젝트와 관련된 텍스트 편집기 설정을 사용하도록 각 코드베이스를 조정할 수 있습니다. Visual Studio **옵션** 대화 상자에서 사용자 고유의 개인 편집기 기본 설정을 지정할 수 있습니다. 사용자가 *.editorconfig* 파일 없이 코드베이스에서 작업을 수행하거나 *.editorconfig* 파일이 특정 설정을 재정의하지 않은 경우 이러한 설정이 적용됩니다. 이러한 기본 설정의 예로 들여쓰기 스타일(탭 또는 공백)을 들 수 있습니다.

Visual Studio를 포함하여 다양한 코드 편집기와 IDE에서 EditorConfig 설정이 지원됩니다. 코드를 이용하여 휴대할 수 있는 구성 요소이며 Visual Studio 외부에서도 코딩 스타일을 적용할 수 있습니다.

::: moniker range=">=vs-2019"

Visual Studio에서 프로젝트에 EditorConfig 파일을 추가하면, 새 코드 줄에는 EditorConfig 설정에 따라 서식이 지정됩니다. 기존 코드의 서식은 다음 명령 중 하나를 실행해야만 변경됩니다.

 - [코드 정리](../ide/code-styles-and-code-cleanup.md)(**Ctrl**+**K**, **Ctrl**+**E**) - 들여쓰기 스타일 등의 공백 설정과 `using` 지시문 정렬 방법 등의 선택한 코드 스타일 설정을 적용합니다.
 - **편집** > **고급** > **문서 서식**(또는 기본 프로필의 **Ctrl**+**K**, **Ctrl**+**D**) - 들여쓰기 스타일 등의 공백 설정만 적용합니다.

 ::: moniker-end

::: moniker range="=vs-2017"

Visual Studio에서 프로젝트에 EditorConfig 파일을 추가하면, 새 코드 줄에는 EditorConfig 설정에 따라 서식이 지정됩니다. 기존 코드의 서식은 문서 서식을 지정해야 변경됩니다(**편집** > **고급** > **문서 서식** 또는 기본 프로필의 **Ctrl**+**K**, **Ctrl**+**D**). [추가 코드 정리를 수행](../ide/code-styles-and-code-cleanup.md#apply-code-styles)하도록 문서 서식을 구성하지 않은 경우, 문서 서식은 들여쓰기 스타일 등의 공백 설정에만 영향을 줍니다.

 ::: moniker-end

::: moniker range="vs-2017"

**문서 서식**을 [**서식 지정** 옵션 페이지](reference/options-text-editor-csharp-formatting.md#format-document-settings)에 적용하려는 EditorConfig 설정을 정의할 수 있습니다.

::: moniker-end

> [!NOTE]
> 이 토픽은 Windows용 Visual Studio에만 적용됩니다. Mac용 Visual Studio는 [Mac용 Visual Studio의 EditorConfig](/visualstudio/mac/editorconfig)를 참조하세요.

## <a name="code-consistency"></a>코드 일관성

EditorConfig 파일의 설정을 사용하면 사용하는 편집기나 IDE에 관계없이 코드베이스에서 들여 쓰기 스타일, 탭 너비, 줄의 끝 문자, 인코딩 등과 같은 일관된 코딩 스타일과 설정을 유지할 수 있습니다. 예를 들어 C#으로 코딩하는 경우 코드베이스에 들여쓰기가 항상 공백 문자 5개로 구성되고, 문서에서 UTF-8 인코딩을 사용하고, 각 줄이 항상 CR/LF로 끝나도록 하는 규칙이 있다면 *.editorconfig* 파일을 해당 규칙에 따라 구성할 수 있습니다.

개인 프로젝트에서 사용하는 코딩 규칙과 팀 프로젝트에서 사용되는 규칙이 서로 다를 수 있습니다. 예를 들어, 코딩할 때 들여쓰기를 하면 탭 문자가 추가되는 것을 선호할 수 있습니다. 그러나 팀에서는 들여쓰기 시 탭 문자 대신 공백 문자 4개가 추가되는 것을 선호할 수 있습니다. EditorConfig 파일을 통해 각 시나리오에 맞게 구성하면 이 문제를 해결할 수 있습니다.

설정은 코드베이스의 파일에 포함되므로 해당 코드베이스와 함께 전송됩니다. EditorConfig 규격 편집기에서 코드 파일을 열기만 하면 텍스트 편집기 설정이 구현됩니다. EditorConfig 파일에 대한 자세한 내용은 [EditorConfig.org](https://editorconfig.org/) 웹 사이트를 참조하세요.

> [!NOTE]
> EditorConfig 파일에서 설정된 규칙은 현재, 빌드 오류 또는 경고로 인해 CI/CD 파이프라인에서 적용할 수 없습니다. 모든 스타일 편차는 Visual Studio 편집기 및 **오류 목록**에만 나타납니다.

## <a name="supported-settings"></a>지원되는 설정

Visual Studio의 편집기는 다음과 같은 [EditorConfig 속성](https://editorconfig.org/#supported-properties)의 핵심 집합을 지원합니다.

- indent_style
- indent_size
- tab_width
- end\_of_line
- 문자 집합
- trim\_trailing_whitespace
- insert\_final_newline
- 루트

EditorConfig 편집기 설정은 XML을 제외하고 Visual Studio가 지원하는 모든 언어에서 지원됩니다. 또한 EditorConfig는 C# 및 Visual Basic에 대해 [언어](../ide/editorconfig-language-conventions.md), [서식 지정](../ide/editorconfig-formatting-conventions.md), [명명](../ide/editorconfig-naming-conventions.md) 규칙을 비롯한 [코드 스타일](../ide/editorconfig-code-style-settings-reference.md) 규칙을 지원합니다.

## <a name="add-and-remove-editorconfig-files"></a>EditorConfig 파일 추가 및 제거

프로젝트 또는 코드베이스에 EditorConfig 파일을 추가하면, 새로 작성하는 코드 줄에는 EditorConfig 파일에 따라 서식이 지정됩니다. 그러나 EditorConfig 파일을 추가해도 문서 서식을 지정하거나 [코드 정리](../ide/code-styles-and-code-cleanup.md)를 실행하기 전에는 기존 스타일이 새 스타일로 변환되지 않습니다. 예를 들어 파일에 탭으로 서식이 지정된 들여쓰기가 있는 경우 공백으로 들여쓰기를 적용하는 EditorConfig 파일을 추가해도 들여쓰기 문자가 공백으로 자동 변환되지는 않습니다. 문서 서식을 지정하면(**편집** > **고급** > **문서 서식** 또는 **Ctrl**+**K**, **Ctrl**+**D**), EditorConfig 파일의 공백 설정이 기존 코드 줄에 적용됩니다.

프로젝트 또는 코드베이스에서 EditorConfig 파일을 제거하고 새 코드 줄에 전역 편집기 설정에 따라 서식을 지정하려는 경우 열려 있는 코드 파일을 모두 닫았다가 다시 열어야 합니다.

### <a name="add-an-editorconfig-file-to-a-project"></a>프로젝트에 EditorConfig 파일 추가

1. Visual Studio에서 프로젝트 또는 솔루션을 엽니다. *.editorconfig* 설정을 솔루션의 모든 프로젝트에 적용할지 아니면 하나에만 적용할지에 따라 프로젝트 또는 솔루션 노드 중 하나를 선택합니다. 프로젝트 또는 솔루션에서 폴더를 선택하여 *.editorconfig* 파일을 추가할 수 있습니다.

1. 메뉴 모음에서 **프로젝트** > **새 항목 추가**를 선택하거나 **Ctrl**+**Shift**+**A**를 누릅니다.

   **새 항목 추가** 대화 상자가 열립니다.

1. 검색 상자에서 **editorconfig**를 검색합니다.

   두 개의 **editorconfig 파일** 항목 템플릿이 검색 결과에 표시됩니다.

   ![Visual Studio의 EditorConfig 파일 항목 템플릿](media/editorconfig-item-templates.png)

1. **editorconfig 파일(기본값)** 템플릿을 선택하여 들여쓰기 스타일 및 크기에 대한 두 가지 핵심 EditorConfig 옵션으로 미리 채워져 있는 EditorConfig 파일을 추가합니다. 또는 **editorconfig 파일(.NET)** 템플릿을 선택하여 기본 [.NET 코드 스타일, 서식 및 명명 규칙](../ide/editorconfig-code-style-settings-reference.md)으로 미리 채워져 있는 EditorConfig 파일을 추가합니다.

   *.editorconfig* 파일이 솔루션 탐색기에 표시되고 편집기에서 열립니다.

   ![솔루션 탐색기 및 편집기의 .editorconfig 파일](media/editorconfig-dotnet.png)

1. 원하는 대로 파일을 편집합니다.

### <a name="other-ways-to-add-an-editorconfig-file"></a>EditorConfig 파일을 추가하는 기타 방법

다음과 같은 몇 가지 기타 방법으로 EditorConfig 파일을 프로젝트에 추가할 수도 있습니다.

- IntelliCode for Visual Studio의 [코드 유추 기능](/visualstudio/intellicode/code-style-inference)은 기존 코드에서 코드 스타일을 유추합니다. 그런 다음, 이미 정의된 코드 스타일 기본 설정을 사용하여 비어 있지 않은 EditorConfig 파일을 만듭니다.

- Visual Studio 2019부터 **도구** > **옵션**에서 [코드 스타일 설정에 따라 EditorConfig 파일을 생성](code-styles-and-code-cleanup.md#code-styles-in-editorconfig-files)할 수 있습니다.

## <a name="file-hierarchy-and-precedence"></a>파일 계층 구조 및 우선 순위

파일 계층 구조의 폴더에 *.editorconfig* 파일을 추가하는 경우 해당 설정이 이 수준과 그 아래에 있는 모든 파일에 적용됩니다. 코드베이스의 다른 부분과는 다른 규칙을 사용하는, 특정 프로젝트, 코드베이스 또는 코드베이스 일부에 대한 EditorConfig 설정을 재정의할 수 있습니다. 이는 다른 위치에서 코드를 통합하면서 해당 규칙을 변경하지 않으려는 경우에 유용할 수 있습니다.

EditorConfig 설정의 일부 또는 전부를 재정의하려면 이러한 재정의된 설정을 적용할 파일 계층 구조 수준에서 *.editorconfig* 파일을 추가합니다. 새 EditorConfig 파일 설정은 동일한 수준 및 모든 하위 디렉터리의 파일에 적용됩니다.

![EditorConfig 계층 구조](../ide/media/vside_editorconfig_hierarchy.png)

설정의 전부가 아닌 일부를 재정의하려는 경우 *.editorconfig* 파일에서 해당 설정만 지정하면 됩니다. 하위 수준 파일에 명시적으로 나열된 속성만 재정의됩니다. 상위 수준 *.editorconfig* 파일의 다른 설정은 계속 적용됩니다. _모든_ 상위 수준 *.editorconfig* 파일에서 이 코드베이스 부분에 적용된 설정이 _없음_을 확인하려면 ```root=true``` 속성을 하위 수준 *.editorconfig* 파일에 추가합니다.

```ini
# top-most EditorConfig file
root = true
```

EditorConfig 파일은 위쪽에서 아래쪽으로 읽습니다. 동일한 이름의 속성이 여러 개 있는 경우 가장 최근에 발견된 해당 이름의 속성이 우선 적용됩니다.

## <a name="edit-editorconfig-files"></a>EditorConfig 파일 편집

Visual Studio를 통해 IntelliSense 완성 목록을 제공하여 *.editorconfig* 파일을 편집할 수 있습니다.

![.editorconfig 파일의 IntelliSense](media/editorconfig-intellisense-no-extension.png)

EditorConfig 파일을 편집한 후 새 설정을 적용하려면 코드 파일을 다시 로드해야 합니다.

다양한 *.editorconfig* 파일을 편집하는 경우 [EditorConfig 언어 서비스 확장](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig)이 유용할 수 있습니다. 이 확장의 기능 중 일부에는 구문 강조 표시, 향상된 IntelliSense, 유효성 검사 및 코드 서식 지정이 포함되어 있습니다.

![EditorConfig 언어 서비스 확장을 사용한 IntelliSense](media/editorconfig-intellisense.png)

## <a name="example"></a>예제

다음 예제에서는 *.editorconfig* 파일을 프로젝트에 추가하기 전과 후의 C# 코드 조각 들여쓰기 상태를 보여줍니다. Visual Studio 텍스트 편집기에 대한 **옵션** 대화 상자의 **탭** 설정은 **Tab** 키를 누를 때 공백 문자를 생성하도록 설정되어 있습니다.

![텍스트 편집기 탭 설정](../ide/media/vside_editorconfig_tabsetting.png)

예상대로 다음 줄에서 **Tab** 키를 누르면 공백 문자 4개가 추가되어 줄이 들여쓰기됩니다.

![EditorConfig를 사용하기 전의 코드](../ide/media/vside_editorconfig_before.png)

다음 콘텐츠를 포함하여 *.editorconfig*라는 새 파일을 프로젝트에 추가합니다. `[*.cs]` 설정은 이 변경 내용이 이 프로젝트의 C# 코드 파일에만 적용된다는 것을 의미합니다.

```ini
# Top-most EditorConfig file
root = true

# Tab indentation
[*.cs]
indent_style = tab
```

이제 **Tab** 키를 누르면 공백 대신 탭 문자가 추가됩니다.

![Tab 키가 탭 문자 추가](../ide/media/vside_editorconfig_tab.png)

## <a name="troubleshoot-editorconfig-settings"></a>EditorConfig 설정 문제 해결

프로젝트 위에 또는 그 이상에 있는 디렉터리 구조의 어디엔가 EditorConfig 파일이 있다면 Visual Studio는 해당 파일의 편집기 설정을 사용자의 편집기에 적용합니다. 이 경우에는 상태 표시줄에서 다음 메시지가 보일 수 있습니다.

   **"이 파일 형식에 대한 사용자 기본 설정이 이 프로젝트의 코딩 규칙으로 재정의됩니다."**

즉, **도구** > **옵션** > **텍스트 편집기**의 편집기 설정(예: 들여쓰기 크기 및 스타일, 탭 크기 또는 코딩 규칙)이 디렉터리 구조에서 프로젝트 또는 위의 EditorConfig 파일에 지정되어 있는 경우 EditorConfig 파일의 규칙은 **옵션**의 설정을 재정의합니다. **도구** > **옵션** > **텍스트 편집기**에서 **프로젝트 코딩 규칙 따름** 옵션을 전환하여 이 동작을 제어할 수 있습니다. 옵션을 선택 취소하면 Visual Studio에 대한 EditorConfig 지원이 해제됩니다.

![도구 옵션 - 프로젝트 코딩 규칙 따름](media/coding_conventions_option.png)

명령 프롬프트를 열고 사용자의 프로젝트가 포함된 디스크의 루트에서 다음 명령을 실행하여 부모 디렉터리에서 *.editorconfig* 파일을 찾을 수 있습니다.

```Shell
dir .editorconfig /s
```

리포지토리의 루트 또는 프로젝트가 상주하는 디렉터리의 *.editorconfig* 파일에서 ```root=true``` 속성을 설정하여 EditorConfig 규칙의 범위를 제어할 수 있습니다. Visual Studio는 열린 파일의 디렉터리와 모든 부모 디렉터리에서 *.editorconfig*라는 파일을 찾습니다. 루트 파일 경로에 도달하거나 ```root=true```인 *.editorconfig* 파일이 발견되면 검색이 종료됩니다.

## <a name="see-also"></a>참조

- [.NET 코드 스타일 규칙](../ide/editorconfig-code-style-settings-reference.md)
- [언어 서비스를 위한 EditorConfig 지원](../extensibility/supporting-editorconfig.md)
- [EditorConfig.org](https://editorconfig.org/)
- [코드 편집기의 기능](writing-code-in-the-code-and-text-editor.md)
- [EditorConfig(Mac용 Visual Studio)](/visualstudio/mac/editorconfig)
