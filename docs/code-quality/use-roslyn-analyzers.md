---
title: 분석기 구성
ms.date: 09/02/2020
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 6a950a005a4669e74722742b23527a9e85ab5f02
ms.sourcegitcommit: d77da260d79471ab139973c51d65b04e0f80fe2e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90560751"
---
# <a name="overview"></a>개요

각 Roslyn analyzer *진단* 또는 규칙에는 프로젝트에 대해 덮어쓰기 및 사용자 지정할 수 있는 기본 심각도 및 비 표시 상태가 있습니다. 이 문서에서는 분석기 심각도 설정 및 분석기 위반 표시를 설명 합니다.

## <a name="configure-severity-levels"></a>심각도 수준 구성

::: moniker range=">=vs-2019"

Visual Studio 2019 버전 16.3 부터는 [Editorconfig 파일](#set-rule-severity-in-an-editorconfig-file), 전구 [메뉴](#set-rule-severity-from-the-light-bulb-menu)및 오류 목록에서 분석기 규칙 또는 *진단*의 심각도를 구성할 수 있습니다.

::: moniker-end

::: moniker range="vs-2017"

분석기를 NuGet 패키지로 [설치](../code-quality/install-roslyn-analyzers.md) 하는 경우 분석기 규칙의 심각도 또는 *진단을*구성할 수 있습니다. 규칙의 심각도를 [솔루션 탐색기](#set-rule-severity-from-solution-explorer) 또는 [규칙 집합 파일](#set-rule-severity-in-the-rule-set-file)에서 변경할 수 있습니다.

::: moniker-end

다음 표에서는 다양 한 심각도 옵션을 보여 줍니다.

| 심각도 (솔루션 탐색기) | 심각도 (EditorConfig 파일) | 빌드 타임 동작 | 편집기 동작 |
|-|-|-|
| Error | `error` | 위반은 오류 목록 및 명령줄 빌드 출력에 *오류로* 표시 되 고 빌드가 실패 합니다.| 잘못 된 코드는 빨간색 물결선으로 밑줄이 표시 되 고 스크롤 막대에 작은 빨간색 상자로 표시 됩니다. |
| 경고 | `warning` | 위반은 오류 목록 및 명령줄 빌드 출력에 *경고* 로 표시 되지만 빌드가 실패 하지는 않습니다. | 잘못 된 코드는 녹색 물결선으로 밑줄이 표시 되 고 스크롤 막대에 작은 녹색 상자로 표시 됩니다. |
| 정보 | `suggestion` | 위반은 명령줄 빌드 출력이 아닌 오류 목록의 *메시지로* 표시 됩니다. | 잘못 된 코드는 회색 물결선으로 밑줄이 표시 되 고 스크롤 막대에 작은 회색 상자로 표시 됩니다. |
| 숨김 | `silent` | 사용자에 게 표시 되지 않습니다. | 사용자에 게 표시 되지 않습니다. 그러나 진단이 IDE 진단 엔진에 보고 됩니다. |
| None | `none` | 완전히 표시 되지 않습니다. | 완전히 표시 되지 않습니다. |
| 기본값 | `default` | 규칙의 기본 심각도에 해당 합니다. 규칙의 기본값을 확인 하려면 속성 창를 확인 합니다. | 규칙의 기본 심각도에 해당 합니다. |

분석기에서 규칙 위반을 발견하면 코드 편집기(위반 코드 아래에 *오류 표시선*이 표시됨) 및 오류 목록 창에 규칙 위반이 보고됩니다.

오류 목록에 보고 된 분석기 위반이 규칙의 [심각도 수준 설정과](../code-quality/use-roslyn-analyzers.md#configure-severity-levels) 일치 합니다. 분석기 위반은 위반 하는 코드 아래에 물결선로 코드 편집기에 표시 됩니다. 다음 이미지는 &mdash; 오류 (빨간색 물결선), 경고 (녹색 물결선) 및 제안 1 개 (회색 점 3 개)의 세 가지 위반을 보여 줍니다.

![Visual Studio 코드 편집기의 오류 표시선](media/diagnostics-severity-colors.png)

다음 스크린샷은 오류 목록에 표시 되는 것과 동일한 세 가지 위반을 보여 줍니다.

![오류 목록에서 오류, 경고 및 정보 위반](media/diagnostics-severities-in-error-list.png)

많은 분석기 규칙 또는 *진단*에는 규칙 위반을 해결 하기 위해 적용할 수 있는 하나 이상의 관련 된 *코드 수정* 이 있습니다. 코드 수정은 다른 형식의 [빠른 작업](../ide/quick-actions.md)과 함께 전구 아이콘 메뉴에 표시됩니다. 이러한 코드 수정에 대한 정보는 [일반적인 빠른 작업](../ide/quick-actions.md)을 참조하세요.

![분석기 위반 및 빠른 작업 코드 수정](../code-quality/media/built-in-analyzer-code-fix.png)

### <a name="hidden-severity-versus-none-severity"></a>' Hidden ' 심각도와 ' None ' 심각도 비교

`Hidden` 기본적으로 사용 하도록 설정 된 심각도 규칙은 `None` 두 가지 방법에서 사용 안 함 또는 심각도 규칙과 다릅니다.

- 심각도 규칙에 대해 코드 수정이 등록 된 경우에는 `Hidden` 숨겨진 진단이 사용자에 게 표시 되지 않더라도 수정 내용이 Visual Studio에서 전구 코드 리팩터링 동작으로 제공 됩니다. 비활성화 된 심각도 규칙의 경우는 그렇지 않습니다 `None` .
- `Hidden` 심각도 규칙은 [EditorConfig 파일에서 한 번에 여러 분석기 규칙의 규칙 심각도를 설정](#set-rule-severity-of-multiple-analyzer-rules-at-once-in-an-editorconfig-file)하는 항목에 의해 대량으로 구성 될 수 있습니다. `None` 이러한 방식으로는 심각도 규칙을 구성할 수 없습니다. 대신 [각 규칙 ID에 대 한 EditorConfig 파일에서 규칙 심각도를 설정](#set-rule-severity-in-an-editorconfig-file)하는 항목을 통해 구성 해야 합니다.

::: moniker range=">=vs-2019"

### <a name="set-rule-severity-in-an-editorconfig-file"></a>EditorConfig 파일에서 규칙 심각도 설정

(Visual Studio 2019 버전 16.3 이상)

다음 구문을 사용 하 여 EditorConfig 파일에서 컴파일러 경고 또는 분석기 규칙의 심각도를 설정할 수 있습니다.

`dotnet_diagnostic.<rule ID>.severity = <severity>`

EditorConfig 파일에서 규칙의 심각도를 설정 하는 것은 규칙 집합 또는 솔루션 탐색기에서 설정 된 심각도 보다 우선 합니다. EditorConfig 파일에서 [수동으로](#manually-configure-rule-severity-in-an-editorconfig-file) 또는 위반 옆에 나타나는 전구를 통해 [자동으로](#set-rule-severity-from-the-light-bulb-menu) 심각도를 구성할 수 있습니다.

### <a name="set-rule-severity-of-multiple-analyzer-rules-at-once-in-an-editorconfig-file"></a>EditorConfig 파일에서 한 번에 여러 분석기 규칙의 규칙 심각도 설정

(Visual Studio 2019 버전 16.5 이상)

EditorConfig 파일에서 단일 항목을 사용 하는 모든 분석기 규칙 또는 분석기 규칙의 특정 범주에 대 한 심각도를 설정할 수 있습니다.

- 분석기 규칙의 범주에 대 한 규칙 심각도 설정:

`dotnet_analyzer_diagnostic.category-<rule category>.severity = <severity>`

- 모든 분석기 규칙의 규칙 심각도를 설정 합니다.

`dotnet_analyzer_diagnostic.severity = <severity>`

> [!NOTE]
> 한 번에 여러 분석기 규칙을 구성 하는 항목은 *기본적으로 사용*되는 규칙에만 적용 됩니다. 분석기 패키지에서 기본적으로 사용 하지 않도록 설정 된 것으로 표시 된 분석기 규칙은 명시적 항목을 통해 사용 하도록 설정 해야 합니다 `dotnet_diagnostic.<rule ID>.severity = <severity>` .

특정 규칙 ID에 적용 되는 항목이 여러 개 있는 경우 해당 항목을 선택 하는 우선 순위는 다음과 같습니다.

- ID 별로 개별 규칙의 심각도 항목은 범주에 대 한 심각도 항목 보다 우선 합니다.
- 범주에 대 한 심각도 항목은 모든 분석기 규칙에 대 한 심각도 항목 보다 우선적으로 적용 됩니다.

[CA1822](./ca1822.md) 에 "Performance" 범주가 있는 다음과 같은 editorconfig 예제를 생각해 보세요.

   ```ini
   [*.cs]
   dotnet_diagnostic.CA1822.severity = error
   dotnet_analyzer_diagnostic.category-performance.severity = warning
   dotnet_analyzer_diagnostic.severity = suggestion
   ```

앞의 예제에서 CA1822에 세 개의 항목을 모두 적용할 수 있습니다. 그러나 지정 된 우선 순위 규칙을 사용 하 여 첫 번째 규칙 ID 기반 심각도 항목은 다음 항목에 대해 적용 됩니다. 이 예제에서 CA1822는 "error"의 유효 심각도를 갖습니다. "성능" 범주가 있는 나머지 모든 규칙에는 심각도 "warning"이 포함 됩니다. "성능" 범주가 없는 나머지 모든 분석기 규칙에는 심각도 "제안"이 있습니다.

#### <a name="manually-configure-rule-severity-in-an-editorconfig-file"></a>EditorConfig 파일에서 규칙 심각도 수동 구성

1. 프로젝트에 대 한 EditorConfig 파일이 아직 없는 경우 [하나를 추가](../ide/create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project)합니다.

2. 구성 하려는 각 규칙에 해당 하는 파일 확장명으로 항목을 추가 합니다. 예를 들어 c # 파일의 [CA1822](ca1822.md) 에 대 한 심각도를 설정 하기 위해 `error` 항목은 다음과 같습니다.

   ```ini
   [*.cs]
   dotnet_diagnostic.CA1822.severity = error
   ```

> [!NOTE]
> IDE 코드 스타일 분석기의 경우 다른 구문 (예:)을 사용 하 여 EditorConfig 파일에서 구성할 수도 있습니다 `dotnet_style_qualification_for_field = false:suggestion` . 그러나 구문을 사용 하 여 심각도를 설정 하는 경우에는 `dotnet_diagnostic` 우선 순위가 우선적으로 적용 됩니다. 자세한 내용은 [EditorConfig에 대 한 언어 규칙](../ide/editorconfig-language-conventions.md)을 참조 하세요.

### <a name="set-rule-severity-from-the-light-bulb-menu"></a>전구 메뉴에서 규칙 심각도 설정

Visual Studio는 [빠른 작업](../ide/quick-actions.md) 전구 메뉴에서 규칙의 심각도를 구성 하는 편리한 방법을 제공 합니다.

1. 위반이 발생 한 후 편집기에서 위반 물결선을 마우스로 가리켜 전구 메뉴를 엽니다. 또는 줄에 커서를 놓고 Ctrl 키를 누릅니다 **Ctrl** + **.** 누릅니다.

2. 전구 메뉴에서 **문제 구성 또는 표시 안 함** 을 선택 하 여 > ** \<rule ID> 심각도를 구성**합니다.

   ![Visual Studio의 전구 메뉴에서 규칙 심각도 구성](media/configure-rule-severity.png)

3. 여기에서 심각도 옵션 중 하나를 선택 합니다.

   ![규칙 심각도를 제안으로 구성](media/configure-rule-severity-suggestion.png)

   Visual Studio는 미리 보기 상자에 표시 된 것 처럼 EditorConfig 파일에 항목을 추가 하 여 요청 된 수준에 대 한 규칙을 구성 합니다.

   > [!TIP]
   > 프로젝트에 EditorConfig 파일이 아직 없는 경우 Visual Studio에서 해당 파일을 만듭니다.

### <a name="set-rule-severity-from-the-error-list-window"></a>오류 목록 창에서 규칙 심각도 설정

Visual Studio는 또한 오류 목록 상황에 맞는 메뉴에서 규칙의 심각도를 구성 하는 편리한 방법을 제공 합니다.

1. 위반이 발생 한 후 오류 목록에서 진단 항목을 마우스 오른쪽 단추로 클릭 합니다.

2. 상황에 맞는 메뉴에서 **심각도 설정**을 선택 합니다.

   ![Visual Studio의 오류 목록에서 규칙 심각도 구성](media/configure-rule-severity-error-list.png)

3. 여기에서 심각도 옵션 중 하나를 선택 합니다.

   Visual Studio에서 EditorConfig 파일에 항목을 추가 하 여 요청 된 수준에 대 한 규칙을 구성 합니다.

   > [!TIP]
   > 프로젝트에 EditorConfig 파일이 아직 없는 경우 Visual Studio에서 해당 파일을 만듭니다.

::: moniker-end

### <a name="set-rule-severity-from-solution-explorer"></a>솔루션 탐색기에서 규칙 심각도 설정

**솔루션 탐색기**에서 analyzer 진단의 사용자 지정을 대부분 수행할 수 있습니다. [분석기](../code-quality/install-roslyn-analyzers.md) 를 NuGet 패키지로 설치 하는 경우 **솔루션 탐색기**의 **참조** 또는 **종속성** 노드 아래에 **분석기** 노드가 나타납니다. **분석기를 확장**한 다음 분석기 어셈블리 중 하나를 확장 하면 어셈블리에 모든 진단이 표시 됩니다.

![솔루션 탐색기의 분석기 노드](media/analyzers-expanded-in-solution-explorer.png)

**속성** 창에서 설명 및 기본 심각도를 포함 하 여 진단 속성을 볼 수 있습니다. 속성을 보려면 해당 규칙을 마우스 오른쪽 단추로 클릭 하 고 **속성**을 선택 하거나 규칙을 선택 하 고 **Alt** + **enter**를 누릅니다.

![속성 창의 진단 속성](media/analyzer-diagnostic-properties.png)

진단에 대 한 온라인 설명서를 보려면 진단을 마우스 오른쪽 단추로 클릭 하 고 **도움말 보기**를 선택 합니다.

**솔루션 탐색기** 의 각 진단 옆에 있는 아이콘은 편집기에서 열 때 규칙 집합에 표시 되는 아이콘에 해당 합니다.

- 원의 "x"는 **오류의** [심각도](#configure-severity-levels) 를 나타냅니다.
- 삼각형의 "!"는 **경고** 의 [심각도](#configure-severity-levels) 를 나타냅니다.
- 원의 "i"는 **정보의** [심각도](#configure-severity-levels) 를 나타냅니다.
- 옅은 색 배경의 원에 있는 "i"는 **숨겨진** 의 [심각도](#configure-severity-levels) 를 나타냅니다.
- 원의 아래쪽 화살표는 진단이 억제 됨을 나타냅니다.

![솔루션 탐색기의 진단 아이콘](media/diagnostics-icons-solution-explorer.png)

::: moniker range=">=vs-2019"

#### <a name="convert-an-existing-ruleset-file-to-editorconfig-file"></a>기존 규칙 집합 파일을 EditorConfig 파일로 변환

Visual Studio 2019 버전 16.5부터, 규칙 집합 파일은 관리 코드에 대 한 분석기 구성에 대 한 EditorConfig 파일을 사용 하 여 더 이상 사용 되지 않습니다. 분석기 규칙 심각도 구성에 대 한 대부분의 Visual Studio 도구는 규칙 집합 파일 대신 EditorConfig 파일에서 작동 하도록 업데이트 되었습니다. EditorConfig 파일을 사용 하면 Visual Studio IDE 코드 스타일 옵션을 포함 하 여 분석기 규칙 심각도 및 분석기 옵션을 모두 구성할 수 있습니다. 기존 규칙 집합 파일을 EditorConfig 파일로 변환 하는 것이 좋습니다. 또한 EditorConfig 파일을 리포지토리의 루트 또는 솔루션 폴더에 저장 하는 것이 좋습니다. 리포지토리 또는 솔루션 폴더의 루트를 사용 하 여이 파일의 심각도 설정이 각각 전체 리포지토리 또는 솔루션에 자동으로 적용 되는지 확인 합니다.

기존 규칙 집합 파일을 EditorConfig 파일로 변환 하는 몇 가지 방법이 있습니다.

- Visual Studio의 규칙 집합 편집기 (Visual Studio 2019 16.5 이상 필요). 프로젝트에서 특정 규칙 집합 파일을 이미 사용 하는 경우 `CodeAnalysisRuleSet` Visual Studio 내의 규칙 집합 편집기에서 해당 하는 EditorConfig 파일로 변환할 수 있습니다.

    1. 솔루션 탐색기에서 규칙 집합 파일을 두 번 클릭 합니다.

       규칙 집합 파일이 규칙 집합 편집기에서 열립니다. 규칙 집합 편집기 위쪽에 클릭 가능한 **정보 표시줄이** 표시 됩니다.

       ![규칙 집합 편집기에서 규칙 집합을 EditorConfig 파일로 변환](media/convert-ruleset-to-editorconfig-file-ruleset-editor.png)

    2. **정보 표시줄** 링크를 선택 합니다.

       그러면 EditorConfig 파일을 생성 하려는 디렉터리를 선택할 수 있는 다른 **이름으로 저장** 대화 상자가 열립니다.

    3. **저장** 단추를 선택 하 여 editorconfig 파일을 생성 합니다.

       생성 된 EditorConfig가 편집기에서 열립니다. 또한 MSBuild 속성은 `CodeAnalysisRuleSet` 프로젝트 파일에서 업데이트 되어 원래 규칙 집합 파일을 더 이상 참조 하지 않습니다.

- 명령줄에서:

    1. NuGet 패키지를 설치 합니다. [RulesetToEditorconfigConverter](https://www.nuget.org/packages/Microsoft.CodeAnalysis.RulesetToEditorconfigConverter).

    2. `RulesetToEditorconfigConverter.exe`규칙 집합 파일 및 EditorConfig 파일 경로를 사용 하 여 설치 된 패키지에서 명령줄 인수로 실행 합니다.

   ```
   Usage: RulesetToEditorconfigConverter.exe <%ruleset_file%> [<%path_to_editorconfig%>]
   ```

변환할 규칙 집합 파일의 예는 다음과 같습니다.

```xml
<?xml version="1.0" encoding="utf-8"?>
<RuleSet Name="Rules for ConsoleApp" Description="Code analysis rules for ConsoleApp.csproj." ToolsVersion="16.0">
  <Rules AnalyzerId="Microsoft.Analyzers.ManagedCodeAnalysis" RuleNamespace="Microsoft.Rules.Managed">
    <Rule Id="CA1001" Action="Warning" />
    <Rule Id="CA1821" Action="Warning" />
    <Rule Id="CA2213" Action="Warning" />
    <Rule Id="CA2231" Action="Warning" />
  </Rules>
</RuleSet>
```

변환 된 EditorConfig 파일은 다음과 같습니다.

```ini
# NOTE: Requires **VS2019 16.3** or later

# Rules for ConsoleApp
# Description: Code analysis rules for ConsoleApp.csproj.

# Code files
[*.{cs,vb}]


dotnet_diagnostic.CA1001.severity = warning

dotnet_diagnostic.CA1821.severity = warning

dotnet_diagnostic.CA2213.severity = warning

dotnet_diagnostic.CA2231.severity = warning
```
::: moniker-end

### <a name="set-rule-severity-from-solution-explorer"></a>솔루션 탐색기에서 규칙 심각도 설정

1. 솔루션 탐색기에서 **참조**  >  **분석기** (또는 **Dependencies**  >  .net Core 프로젝트에 대 한 종속성**분석기** )를 확장 합니다.

2. 심각도를 설정 하려는 규칙이 포함 된 어셈블리를 확장 합니다.

::: moniker range=">=vs-2019"
3. 규칙을 마우스 오른쪽 단추로 클릭 하 고 **심각도 설정**을 선택 합니다. 상황에 맞는 메뉴에서 심각도 옵션 중 하나를 선택 합니다.

   Visual Studio에서 EditorConfig 파일에 항목을 추가 하 여 요청 된 수준에 대 한 규칙을 구성 합니다. 프로젝트에서 EditorConfig 파일 대신 규칙 집합 파일을 사용 하는 경우 심각도 항목이 규칙 집합 파일에 추가 됩니다.

   > [!TIP]
   > 프로젝트에 EditorConfig 파일 또는 규칙 집합 파일이 아직 없는 경우 Visual Studio에서 새 EditorConfig 파일을 만듭니다.
::: moniker-end

::: moniker range="vs-2017"
3. 규칙을 마우스 오른쪽 단추로 클릭 하 고 **규칙 집합 심각도 설정**을 선택 합니다. 상황에 맞는 메뉴에서 심각도 옵션 중 하나를 선택 합니다.

   규칙에 대 한 심각도는 활성 규칙 집합 파일에 저장 됩니다.
::: moniker-end

### <a name="set-rule-severity-in-the-rule-set-file"></a>규칙 집합 파일에 규칙 심각도 설정

![솔루션 탐색기의 규칙 집합 파일](media/ruleset-in-solution-explorer.png)

1. 다음 방법 중 하나로 활성 규칙 집합 파일을 엽니다.

- **솔루션 탐색기**에서 파일을 두 번 클릭 하 고 **참조**  >  **분석기** 노드를 마우스 오른쪽 단추로 클릭 한 다음 **활성 규칙 집합 열기**를 선택 합니다.
- 프로젝트에 대 한 **코드 분석** 속성 페이지에서 **열기** 를 선택 합니다.

  처음으로 규칙 집합을 편집 하는 경우 Visual Studio에서 기본 규칙 집합 파일의 복사본을 만들고 이름을. a s t a .로 설정 하 고 프로젝트에 추가 합니다 * \<projectname> .* 또한이 사용자 지정 규칙 집합은 프로젝트에 대 한 활성 규칙 집합이 됩니다.

   > [!NOTE]
   > .NET Core 및 .NET Standard 프로젝트는 **솔루션 탐색기**에서 규칙 집합에 대 한 메뉴 명령을 지원 하지 않습니다 (예: **활성 규칙 집합 열기**). .NET Core 또는 .NET Standard 프로젝트에 대해 기본이 아닌 규칙 집합을 지정 하려면 프로젝트 파일에 [ **CodeAnalysisRuleSet** 속성](using-rule-sets-to-group-code-analysis-rules.md#specify-a-rule-set-for-a-project) 을 수동으로 추가 합니다. Visual Studio 규칙 집합 편집기 UI의 규칙 집합 내에서 규칙을 계속 구성할 수 있습니다.

1. 포함 하는 어셈블리를 확장 하 여 규칙을 찾습니다.

1. **작업** 열에서 값을 선택 하 여 드롭다운 목록을 열고 목록에서 원하는 심각도를 선택 합니다.

   ![편집기에 열려 있는 규칙 집합 파일](media/ruleset-file-in-editor.png)

::: moniker range=">=vs-2019"

## <a name="configure-generated-code"></a>생성 된 코드 구성

분석기는 프로젝트의 모든 소스 파일에서 실행 되며 위반을 보고 합니다. 그러나 디자이너에서 생성 된 코드 파일, 빌드 시스템에서 생성 된 임시 소스 파일 등 생성 된 코드 파일에는 이러한 위반이 유용 하지 않습니다. 사용자는 이러한 파일을 수동으로 편집할 수 없으며 이러한 종류의 도구 생성 파일에서 위반 문제를 해결 하는 것은 걱정 하지 않습니다.

기본적으로 분석기 드라이버 실행 분석기는 특정 이름, 파일 확장명 또는 자동 생성 된 파일 헤더를 사용 하 여 파일을 생성 된 코드 파일로 처리 합니다. 예를 들어 또는로 끝나는 파일 이름은 `.designer.cs` `.generated.cs` 생성 된 코드로 간주 됩니다. 그러나 이러한 추론은 사용자의 소스 코드에서 생성 된 모든 사용자 지정 코드 파일을 식별 하지 못할 수 있습니다.

Visual Studio 2019 16.5부터 최종 사용자는 [Editorconfig 파일](https://editorconfig.org/)에서 생성 된 코드로 처리할 특정 파일 및/또는 폴더를 구성할 수 있습니다. 이러한 구성을 추가 하려면 다음 단계를 따르세요.

1. 프로젝트에 대 한 EditorConfig 파일이 아직 없는 경우 [하나를 추가](../ide/create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project)합니다.

2. `generated_code = true | false`특정 파일 및/또는 폴더에 대 한 항목을 추가 합니다. 예를 들어 이름이 생성 된 코드로 끝나는 모든 파일을 처리 하려면 `.MyGenerated.cs` 항목은 다음과 같습니다.

   ```ini
   [*.MyGenerated.cs]
   generated_code = true
   ```

::: moniker-end

## <a name="suppress-violations"></a>위반 표시 안 함

규칙 위반을 표시 하지 않는 방법에는 여러 가지가 있습니다.

::: moniker range=">=vs-2019"

- **Editorconfig 파일** 에서

  심각도를로 설정 `none` 합니다 (예:) `dotnet_diagnostic.CA1822.severity = none` .

- **분석** 메뉴에서

  **Analyze**  >  메뉴 모음에서**빌드 분석 및 활성 문제 표시 안** 함을 선택 하 여 현재 위반을 모두 표시 하지 않습니다. 이를 "기준 기준선"이 라고도 합니다.

::: moniker-end

::: moniker range="vs-2017"

- **분석** 메뉴에서

  **Analyze**  >  메뉴 모음에서 분석**실행 코드 분석 및 활성 문제 표시 안 함** 을 선택 하 여 현재 위반을 모두 표시 하지 않습니다. 이를 "기준 기준선"이 라고도 합니다.

::: moniker-end

- **솔루션 탐색기** 에서

  규칙의 심각도를 **None**으로 설정 합니다.

- **규칙 집합 편집기** 에서

  이름 옆에 있는 확인란의 선택을 취소 하거나 **작업** 을 **없음**으로 설정 합니다.

- **코드 편집기** 에서

  위반 하는 코드 줄에 커서를 놓고 **Ctrl** + **마침표 (.)** 를 눌러 **빠른 작업** 메뉴를 엽니다. 원본/비 표시 제거 파일에서 **caxxxx를 표시 하지 않습니다**  >  **in Source/in Suppression File**.를 선택 합니다.

  ![빠른 작업 메뉴에서 진단 표시 안 함](media/suppress-diagnostic-from-editor.png)

- **오류 목록** 에서

  표시 하지 않을 규칙을 선택한 다음 마우스 오른쪽 단추를 클릭 하 고 소스/비 **표시 안 함 파일에서 표시 안 함**을 선택  >  **In Source/In Suppression File**합니다.

  - **소스에서**표시 하지 않는 경우 **변경 내용 미리 보기** 대화 상자가 열리고 소스 코드에 추가 된 c # [#pragma 경고](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning) 또는 Visual Basic [#Disable 경고](/dotnet/visual-basic/language-reference/directives/directives) 지시문의 미리 보기가 표시 됩니다.

    ![코드 파일에 #pragma 경고 추가의 미리 보기](media/pragma-warning-preview.png)

  - **비 표시 오류 (Suppression) 파일에서**를 선택 하면 **변경 내용 미리 보기** 대화 상자가 열리고 <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> 전역 비 표시 오류 파일에 추가 된 특성의 미리 보기가 표시 됩니다.

    ![SuppressMessage 특성을 비 표시 오류 (suppression) 파일에 추가 하는 미리 보기](media/preview-changes-in-suppression-file.png)

  **변경 내용 미리 보기** 대화 상자에서 **적용**을 선택 합니다.

  > [!NOTE]
  > **솔루션 탐색기**에 **표시 안 함** 메뉴 옵션이 표시 되지 않는 경우에는 위반이 발생 했을 수 있습니다. **오류 목록** 는 라이브 코드 분석과 빌드 모두에서 진단 또는 규칙 위반을 표시 합니다. 빌드 진단은 부실 할 수 있습니다. 예를 들어 위반 문제를 해결 하기 위해 코드를 편집 했지만 다시 빌드하지 않은 경우에는 **오류 목록**에서 이러한 진단을 표시 하지 않을 수 있습니다. 라이브 분석 또는 IntelliSense의 진단은 항상 최신 원본으로 최신 상태를 유지 하며 **오류 목록**에서 표시 되지 않을 수 있습니다. 선택에서 *빌드* 진단을 제외 하려면 **빌드 + Intellisense** 에서 **intellisense 전용**으로 **오류 목록** 원본 필터를 전환 합니다. 그런 다음 앞에서 설명한 대로 표시 하지 않을 진단을 선택 하 고 계속 진행 합니다.
  >
  > ![Visual Studio에서 원본 필터 오류 목록](media/error-list-filter.png)

## <a name="command-line-usage"></a>명령줄 사용

명령줄에서 프로젝트를 빌드하는 경우 다음 조건이 충족 되 면 빌드 출력에 규칙 위반이 표시 됩니다.

- 분석기는 VSIX 확장이 아니라 NuGet 패키지로 설치 됩니다.

- 프로젝트 코드에서 하나 이상의 규칙을 위반 했습니다.

- 위반 된 규칙의 [심각도](#configure-severity-levels) 는 **경고**로 설정 되며,이 경우 위반으로 인해 빌드가 실패 하거나 **오류가**발생 하지 않습니다 .이 경우 위반으로 인해 빌드가 실패 합니다.

빌드 출력의 자세한 정도는 규칙 위반이 표시 되는지 여부에 영향을 주지 않습니다. **자동** 자세한 정도를 사용 하더라도 규칙 위반은 빌드 출력에 표시 됩니다.

> [!TIP]
> *FxCopCmd.exe* 또는 **runcodeanalysis** 플래그를 사용 하 여 msbuild를 통해 명령줄에서 레거시 분석을 실행 하는 데 익숙한 경우 코드 분석기를 사용 하 여이 작업을 수행 하는 방법은 다음과 같습니다.

Msbuild를 사용 하 여 프로젝트를 빌드할 때 명령줄에서 분석기 위반을 확인 하려면 다음과 같이 명령을 실행 합니다.

```cmd
msbuild myproject.csproj /target:rebuild /verbosity:minimal
```

다음 이미지에서는 분석기 규칙 위반을 포함하는 프로젝트 빌드의 명령줄 빌드 출력을 보여줍니다.

![규칙 위반을 사용하여 MSBuild 출력](media/command-line-build-analyzers.png)

## <a name="dependent-projects"></a>종속 프로젝트

.NET Core 프로젝트에서 NuGet 분석기를 포함 하는 프로젝트에 대 한 참조를 추가 하면 해당 분석기도 자동으로 종속 프로젝트에 추가 됩니다. 이 동작을 사용 하지 않도록 설정 하려면 예를 들어, 종속 프로젝트가 단위 테스트 프로젝트인 경우 **PrivateAssets** 특성을 설정 하 여 참조 된 프로젝트의 *.csproj* 또는 *.vbproj* 파일에서 NuGet 패키지를 private으로 표시 합니다.

```xml
<PackageReference Include="Microsoft.CodeAnalysis.FxCopAnalyzers" Version="2.9.0" PrivateAssets="all" />
```

## <a name="see-also"></a>참고 항목

- [Visual Studio의 코드 분석기 개요](../code-quality/roslyn-analyzers-overview.md)
- [코드 분석기 버그 제출](https://github.com/dotnet/roslyn-analyzers/issues)
- [규칙 집합 사용](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
- [코드 분석 경고 표시 안 함](../code-quality/in-source-suppression-overview.md)