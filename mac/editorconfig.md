---
title: EditorConfig
description: EditorConfig 파일을 사용하여 Mac용 Visual Studio에서 일관된 프로젝트 코딩 스타일 활성화.
author: cobey
ms.author: cobey
ms.date: 05/06/2018
ms.technology: vs-ide-install
ms.assetid: 26A0DE31-2FBF-4E1B-99FB-083111AA1680
ms.openlocfilehash: 6f6241c114d636cc8cb01cf5c4bf9ba2b5106701
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/20/2020
ms.locfileid: "73716894"
---
# <a name="creating-and-editing-a-custom-editorconfig-file"></a>사용자 지정 EditorConfig 파일 만들기 및 편집

Mac용 Visual Studio에서는 프로젝트 또는 솔루션에 [EditorConfig](https://editorconfig.org/) 파일을 추가하여 코드베이스에서 작업하는 모든 사람들의 코딩 스타일을 일관적으로 유지할 수 있습니다. EditorConfig 파일에 선언된 설정은 글로벌 Mac용 Visual Studio 텍스트 편집기 설정에 우선합니다. 프로젝트 또는 코드베이스 내에서 EditorConfig 파일을 사용하여 프로젝트의 코딩 스타일, 기본 설정 및 경고를 지정할 수 있습니다. 파일은 코드베이스의 일부이기 때문에 사용하는 IDE 또는 코드 편집기에 관계없이 모든 사용자가 프로젝트의 코딩 방법을 쉽게 준수할 수 있습니다.

[EditorConfig](https://editorconfig.org/) 파일은 Visual Studio를 비롯한 여러 IDE 및 코드 편집기에서 지원됩니다.

## <a name="supported-settings"></a>지원되는 설정

Mac용 Visual Studio의 편집기는 다음과 같은 [EditorConfig 속성](https://editorconfig.org/#supported-properties)의 핵심 집합을 지원합니다.

- `indent_style`
- `indent_size`
- `tab_width`
- `end_of_line`
- `charset`
- `trim_trailing_whitespace`
- `insert_final_newline`
- `root`

EditorConfig는 C#에서 [코딩 규칙](/visualstudio/ide/editorconfig-code-style-settings-reference)도 지원합니다.

## <a name="add-an-editorconfig-file-to-a-project"></a>프로젝트에 EditorConfig 파일 추가

### <a name="adding-a-new-editorconfig-file"></a>새 EditorConfig 파일 추가

1. Mac용 Visual Studio에서 프로젝트를 엽니다. EditorConfig 파일을 추가할 솔루션 또는 프로젝트 노드를 선택합니다. 솔루션 디렉터리에 파일을 추가하면 솔루션의 모든 프로젝트에 .editorconfig 설정이 적용됩니다.

2. 노드를 마우스 오른쪽 단추로 클릭하고 **추가 > 새 파일**을 선택하여 **새 파일** 대화 상자를 엽니다.

    ![콘텐츠 메뉴 항목](media/editorconfig-image0.png)

3. **기타 > 빈 텍스트 파일**을 선택하고 **이름**에 `.editorconfig`를 지정합니다. **새로 만들기**를 눌러 파일을 만들고 편집기에서 엽니다.

    ![새 파일 대화 상자](media/editorconfig-image1.png)

    솔루션 수준에서 항목을 추가하면 해당 항목이 자동으로 생성되고 **솔루션 항목** 폴더에 중첩됩니다.

    ![솔루션 패드에 표시되는 솔루션 항목](media/editorconfig-image1a.png)

4. 파일을 편집합니다. 예를 들어:

    ```EditorConfig
    # This file is the top-most EditorConfig file
    root = true

    # All Files
    [*]
    indent_style = space
    indent_size = 8
    insert_final_newline = false
    trim_trailing_whitespace = false

    [*.cs]
    csharp_new_line_before_open_brace = none
    ```

4. `.editorconfig` 파일의 설정은 작성하는 모든 새 코드에 적용되지만 기존 코드를 새 설정과 일치하도록 다시 포맷해야 할 수 있습니다. `.editorconfig` 파일의 설정을 기존 원본 파일에 적용하려면 파일을 열고 메뉴 모음에서 **편집 > 서식 > 문서 서식**을 선택합니다.

    ![문서 서식 메뉴 항목](media/editorconfig-image2.png)

### <a name="adding-an-existing-editorconfig-file"></a>기존 EditorConfig 파일 추가

`.editorconfig` 파일이 이미 포함된 프로젝트 또는 솔루션으로 작업 중인 경우 설정을 적용하기 위해 해야 할 일이 없습니다. 새로운 코드 줄은 EditorConfig 설정에 따라 서식이 지정됩니다.

기존의 `.editorconfig` 파일을 프로젝트에서 재사용하는 것이 좋습니다. 기존 파일을 추가하려면 다음을 수행합니다.

1. 기존 파일을 추가하려는 폴더를 마우스 오른쪽 단추로 클릭하고 **추가 > 파일 추가**를 선택합니다.

2. 필요한 파일의 디렉터리로 이동합니다.

3. `.` (예: `.editorconfig`)로 시작하는 파일은 macOS의 숨겨진 파일이므로 **Command + Shift +.** 를 누릅니다. `.editorconfig` 파일을 표시하려면

4. `.editorconfig` 파일을 선택하고 **열기**를 클릭합니다.

    ![새 파일 창 추가](media/editorconfig-image3b.png)

5. 다음 대화 상자가 표시되면 **디렉터리에 파일 복사** 옵션을 선택하고 **확인**을 선택합니다.

    ![대화 상자 옵션 폴더에 파일 추가](media/editorconfig-image3.png)

### <a name="reflecting-editorconfig-settings"></a>.editorconfig 설정 반영

EditorConfig 파일을 코드베이스에 추가하면 추가된 모든 새 코드가 지정된 설정에 따라 자동으로 포맷됩니다. 코드베이스를 포맷하지 않으면 기존 코드는 자동으로 설정을 반영하지 않습니다.

`.editorconfig` 파일의 설정을 반영하려면 솔루션 노드를 선택하고 메뉴 모음에서 **편집 > 서식 > 문서 서식**을 선택합니다.

![메뉴 모음에서 문서 서식](media/editorconfig-image3a.png)

## <a name="editing-an-editorconfig-file"></a>EditorConfig 파일 편집

EditorConfig 파일은 직관적인 파일 레이아웃을 사용하여 설정을 지정합니다. 이전 예를 사용한 이에 대한 설명이 아래에 나와 있습니다.

```EditorConfig
# This file is the top-most EditorConfig file
root = true

# All Files
[*]
indent_style = space
indent_size = 4
insert_final_newline = false
trim_trailing_whitespace = false

[*.cs]
csharp_new_line_before_open_brace = none
```

`root`를 `true`로 설정하면 [EditorConfig 설정 재정의](#override-editorconfig-settings) 섹션에 설명된 대로 이 파일을 코드베이스의 최상위 파일 플래그로 지정하고, 프로젝트의 모든 상위 `.editorconfig` 파일을 무시합니다.

각 섹션은 꺾쇠 괄호( **[ ]** )로 표시되며, 다음 속성과 관련된 파일 형식에 대한 정보를 나타냅니다.

위의 예에서 일부 설정은 프로젝트의 모든 파일에 적용되며, 다른 설정은 C# 파일에만 추가됩니다. 아래 스크린샷은 `.editorconfig` 설정 적용 전후를 보여줍니다.

**이전**:

![editorconfig 설정이 적용되기 전](media/editorconfig-image4.png)

**이후**:

![editorconfig 설정이 적용된 후](media/editorconfig-image5.png)

사용 가능한 EditorConfig 설정에 대한 자세한 내용은 [EditorConfig에 대한 .NET 코딩 규칙 설정](/visualstudio/ide/editorconfig-code-style-settings-reference) 아티클과 공식 문서의 [지원되는 속성](https://editorconfig.org/#supported-properties) 섹션을 참조하세요.

## <a name="override-editorconfig-settings"></a>EditorConfig 설정 재정의

각 솔루션에는 `.editorconfig` 파일이 여러 개 있을 수 있습니다. Mac용 Visual Studio는 `.editorconfig` 파일을 솔루션의 위쪽에서 아래쪽으로 읽으며 진행 중인 설정을 추가하고 재정의합니다. 즉, 편집 중인 파일에 ‘가장 가까운’ `.editorconfig`의 설정이 우선합니다.  설정은 `.editorconfig` 파일에서 동일한 폴더(있는 경우)로 가져온 다음, 부모 폴더의 `.editorconfig`(있는 경우) 등에서 가져옵니다. 찾을 때까지 `root=true`입니다.

모든 상위 수준 `.editorconfig` 파일에서 이 코드베이스 부분에 적용된 설정이 _없음_을 확인하려면 `root=true` 속성을 하위 수준 `.editorconfig` 파일의 최상위에 추가합니다.

```EditorConfig
# top-most EditorConfig file
root = true
```

## <a name="see-also"></a>참조

- [EditorConfig를 사용하여 사용자 지정 편집기 설정 만들기(Windows의 Visual Studio)](/visualstudio/ide/create-portable-custom-editor-options)