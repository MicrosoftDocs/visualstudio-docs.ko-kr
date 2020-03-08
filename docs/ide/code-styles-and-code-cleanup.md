---
title: 코드 스타일 옵션 및 코드 정리
ms.date: 04/25/2019
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Code_Style.General
- VS.ToolsOptionsPages.Text_Editor.Basic.Code_Style.General
ms.workload:
- multiple
ms.openlocfilehash: 9d540339ca25fc42fc05df4818a6d05204ccae0e
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78408501"
---
# <a name="code-style-preferences"></a>코드 스타일 기본 설정

[EditorConfig 파일](#code-styles-in-editorconfig-files)을 사용하거나 텍스트 편집기 [**옵션** 페이지](#code-styles-in-the-options-dialog-box)의 Visual Studio에서 편집하는 모든 코드에 대해 프로젝트별 코드 스타일 설정을 정의할 수 있습니다. C# 코드의 경우 **코드 정리**(Visual Studio 2019) 및 **문서 서식**(Visual Studio 2017) 명령을 사용하여 이러한 코드 스타일 기본 설정을 적용하도록 Visual Studio를 구성할 수도 있습니다.

> [!NOTE]
> 이 토픽은 Windows용 Visual Studio에만 적용됩니다. Mac용 Visual Studio는 [Mac용 Visual Studio의 편집기 동작](/visualstudio/mac/editor-behavior)을 참조하세요.

## <a name="code-styles-in-editorconfig-files"></a>EditorConfig의 코드 스타일

[EditorConfig](create-portable-custom-editor-options.md) 파일을 프로젝트에 추가하여 .NET에 대한 [코드 스타일 설정](../ide/editorconfig-code-style-settings-reference.md)을 지정할 수 있습니다. EditorConfig 파일은 Visual Studio 개인 설정 계정이 아니라 코드베이스와 연결되어 있습니다. EditorConfig 파일의 설정은 **옵션** 대화 상자에 지정된 코드 스타일보다 우선합니다. 모든 기여자의 코딩 스타일을 리포지토리 또는 프로젝트에 적용하려면 EditorConfig 파일을 사용합니다.

::: moniker range=">=vs-2019"

EditorConfig 파일을 수동으로 채우거나, Visual Studio **옵션** 대화 상자에서 설정한 코드 스타일 설정에 따라 파일을 자동으로 생성할 수 있습니다. 이 옵션 페이지는 **도구** > **옵션** > **텍스트 편집기** > [**C#**  또는 **기본**] > **코드 스타일** > **일반**에서 사용할 수 있습니다. 이 **옵션** 페이지의 설정에 따라 코딩 스타일 *.editorconfig* 파일을 자동으로 생성하려면 **설정에서 .editorconfig 파일 생성**을 클릭합니다.

![Visual Studio 2019의 설정에서 editorconfig 파일 생성](media/vs-2019/generate-editorconfig-file-small.png)

::: moniker-end

## <a name="code-styles-in-the-options-dialog-box"></a>옵션 대화 상자의 코드 스타일

**도구** 메뉴에서 **옵션** 대화 상자를 열어 모든 C# 및 Visual Basic 프로젝트에 대한 코드 스타일 기본 설정을 설정할 수 있습니다. **옵션** 대화 상자에서 **텍스트 편집기** > [**C#** 또는 **기본**] > **코드 스타일** > **일반**을 선택합니다.

목록의 각 항목에는 선택한 기본 설정의 미리 보기가 표시됩니다.

::: moniker range="vs-2017"

![코드 스타일 옵션](media/code-style-quick-actions-dialog.png)

::: moniker-end

::: moniker range=">=vs-2019"

![코드 스타일 옵션](media/vs-2019/code-style-quick-actions-dialog.png)

::: moniker-end

이 창에서 설정된 옵션은 Visual Studio 개인 설정 계정에 적용되며, 특정 프로젝트 또는 코드베이스에 연결되어 있지 않습니다. 또한 해당 옵션은 CI(연속 통합) 빌드를 포함하여 빌드할 때 적용되지 않습니다. 코드 스타일 기본 설정을 프로젝트에 연결하고 빌드하는 동안 스타일을 적용하려면 프로젝트와 연결된 [.editorconfig 파일](#code-styles-in-editorconfig-files)에서 기본 설정을 지정합니다.

### <a name="preference-and-severity"></a>기본 설정 및 심각도

이 페이지의 각 코드 스타일 설정에 대해, 각 줄에 있는 드롭다운을 사용하여 **기본 설정** 및 **심각도** 값을 설정할 수 있습니다. 심각도는 **리팩터링만**, **제안**, **경고** 또는 **오류**로 설정할 수 있습니다. 코드 스타일에 대해 [빠른 작업](../ide/quick-actions.md)을 사용하려면 **심각도** 설정이 **리팩터링만** 이외의 값으로 설정되어 있는지 확인합니다. 선호하지 않는 스타일이 사용될 경우 **빠른 작업** 전구 ![전구](media/light-bulb-dropdown.png), 오류 전구 ![오류 전구](media/error-bulb.png) 또는 스크루드라이버 ![스크루드라이버](media/screwdriver.png) 아이콘이 표시되고, **빠른 작업** 목록에서 옵션을 선택하면 코드를 원하는 스타일로 자동으로 다시 작성할 수 있습니다.

## <a name="apply-code-styles"></a>코드 스타일 적용

::: moniker range="vs-2017"

**Format Document** 명령(**편집** > **고급** > **문서 서식**)을 구성하여 코드 스타일 설정(EditorConfig 파일 또는 **코드 스타일** 옵션에서)을 일반 형식(예: 들여쓰기)과 함께 적용할 수 있습니다. 프로젝트용 *.editorconfig* 파일이 있는 경우 해당 설정이 우선합니다.

> [!NOTE]
> **문서 서식** 명령을 사용하여 코드 스타일을 적용하는 것은 C# 코드 파일에만 사용할 수 있습니다. 이는 실험적인 기능입니다.

[서식 지정 옵션 페이지](reference/options-text-editor-csharp-formatting.md#format-document-settings)에 적용할 **문서 서식**을 원하는 설정으로 구성합니다.

![Visual Studio 2017의 형식 문서에 대한 코드 스타일 설정](media/format-document-settings-experiment.png)

> [!TIP]
> 심각도가 **없음**으로 구성된 규칙은 코드 정리에 참여하지 않지만 **빠른 작업 및 리팩터링** 메뉴를 통해 개별적으로 적용될 수 있습니다.

처음으로 **문서 서식** 명령을 트리거하면 노란색 정보 표시줄에 코드 정리 설정을 구성하라는 메시지가 표시됩니다.

::: moniker-end

::: moniker range=">=vs-2019"

C# 코드 파일의 경우 Visual Studio 2019에는 편집기 하단에 **코드 정리** 단추(키보드: **Ctrl**+**K**, **Ctrl**+**E**)가 있어 EditorConfig 파일 또는 **코드 스타일** 옵션 페이지에서 코드 스타일을 적용할 수 있습니다. 프로젝트용 *.editorconfig* 파일이 있는 경우 해당 설정이 우선합니다.

![Visual Studio 2019에서 코드 정리 실행](media/execute-code-cleanup.png)

> [!TIP]
> 심각도가 **없음**으로 구성된 규칙은 코드 정리에 참여하지 않지만 **빠른 작업 및 리팩터링** 메뉴를 통해 개별적으로 적용될 수 있습니다.

먼저 **코드 정리 구성** 대화 상자에서 두 프로필 중 하나의 적용할 코드 스타일을 구성합니다. 이 대화 상자를 열려면 코드 정리 broom 아이콘 옆에 있는 확장 화살표를 클릭한 다음, **코드 정리 구성**을 선택합니다.

![Visual Studio 2019에서 코드 정리 구성](media/configure-code-cleanup.png)

코드 정리를 구성한 후 빗자루 아이콘을 클릭하거나 **Ctrl**+**K**, **Ctrl**+**E**를 눌러 코드 정리를 실행합니다. 전체 프로젝트 또는 솔루션에서 코드 정리를 실행할 수도 있습니다. **솔루션 탐색기**에서 프로젝트 또는 솔루션 이름을 마우스 오른쪽 단추로 클릭하고 **분석 및 코드 정리**를 선택한 다음, **코드 정리 실행**을 선택합니다.

![전체 프로젝트 또는 솔루션에서 코드 정리 실행](media/run-code-cleanup-project-solution.png)

파일을 저장할 때마다 코드 스타일 설정을 적용하려면 [저장 시 코드 정리](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.CodeCleanupOnSave) 확장을 사용할 수 있습니다.

::: moniker-end

## <a name="see-also"></a>참조

- [빠른 작업](../ide/quick-actions.md)
- [EditorConfig에 대한 .NET 코딩 규칙 설정](../ide/editorconfig-code-style-settings-reference.md)
- [편집기 동작(Mac용 Visual Studio)](/visualstudio/mac/editor-behavior)
