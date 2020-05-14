---
title: 분석기 규칙 심각도 및 억제
ms.date: 03/04/2020
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 67fd157ad4db24acbc1676ea0a9a1d79e9eb34f9
ms.sourcegitcommit: 92361aac3665a934faa081e1d1ea89a067b01c5b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79431412"
---
# <a name="use-code-analyzers"></a>코드 분석기 사용

.NET 컴파일러 플랫폼("Roslyn") 코드 분석기는 입력할 때 C# 또는 Visual Basic 코드를 분석합니다. 각 *진단* 또는 규칙에는 프로젝트에 대해 덮어쓸 수 있는 기본 심각도 및 억제 상태가 있습니다. 이 문서에서는 규칙 심각도 설정, 규칙 집합 사용 및 위반 억제에 대해 다룹니다.

## <a name="analyzers-in-solution-explorer"></a>솔루션 탐색기의 분석기

**솔루션 탐색기에서**분석기 진단의 사용자 지정을 많이 수행할 수 있습니다. 분석기를 NuGet 패키지로 [설치하면](../code-quality/install-roslyn-analyzers.md) **분석기** 노드가 **솔루션 탐색기의** **참조** 또는 **종속성** 노드 아래에 나타납니다. **분석기를**확장한 다음 분석기 어셈블리 중 하나를 확장하면 어셈블리의 모든 진단 유틸리티가 표시됩니다.

![솔루션 탐색기의 분석기 노드](media/analyzers-expanded-in-solution-explorer.png)

속성 **창에서** 설명 및 기본 심각도를 포함하여 진단의 속성을 볼 수 있습니다. 속성을 보려면 규칙을 마우스 오른쪽 단추로 클릭하고 **속성을**선택하거나 규칙을 선택한 다음 **Alt**+Enter 를**누릅니다.**

![속성 창의 진단 속성](media/analyzer-diagnostic-properties.png)

진단에 대한 온라인 설명서를 보려면 진단을 마우스 오른쪽 단추로 클릭하고 **도움말 보기를**선택합니다.

**솔루션 탐색기의** 각 진단 옆에 있는 아이콘은 편집기에서 열 때 규칙 집합에 표시되는 아이콘에 해당합니다.

- 원의 "x"는 **오류의** [심각도를](#rule-severity) 나타냅니다.
- 삼각형의 "!" 경고의 [심각도를](#rule-severity) **나타냅니다.**
- 원의 "i"는 **정보의** [심각도를](#rule-severity) 나타냅니다.
- 밝은 색상의 배경에 있는 원의 "i"는 **숨겨진** 의 [심각도를](#rule-severity) 나타냅니다.
- 원의 아래쪽 을 가리키는 화살표는 진단이 억제되어 있음을 나타냅니다.

![솔루션 탐색기의 진단 아이콘](media/diagnostics-icons-solution-explorer.png)

## <a name="rule-severity"></a>규칙 심각도

::: moniker range=">=vs-2019"

분석기를 NuGet 패키지로 설치하는 경우 [분석기](../code-quality/install-roslyn-analyzers.md) 규칙 또는 *진단*의 심각도를 구성할 수 있습니다. Visual Studio 2019 버전 16.3부터 [는 EditorConfig 파일에서](#set-rule-severity-in-an-editorconfig-file)규칙의 심각도를 구성할 수 있습니다. [솔루션 탐색기](#set-rule-severity-from-solution-explorer) 또는 규칙 집합 [파일에서](#set-rule-severity-in-the-rule-set-file)규칙의 심각도를 변경할 수도 있습니다.

::: moniker-end

::: moniker range="vs-2017"

분석기를 NuGet 패키지로 설치하는 경우 [분석기](../code-quality/install-roslyn-analyzers.md) 규칙 또는 *진단*의 심각도를 구성할 수 있습니다. [솔루션 탐색기](#set-rule-severity-from-solution-explorer) 또는 규칙 집합 [파일에서](#set-rule-severity-in-the-rule-set-file)규칙의 심각도를 변경할 수 있습니다.

::: moniker-end

다음 표에서는 다양한 심각도 옵션을 보여 주며 다음과 같은 옵션을 보여 주실 수 있습니다.

| 심각도(솔루션 탐색기) | 심각도(편집기구성 파일) | 빌드 시간 동작 | 편집기 동작 |
|-|-|-|
| Error | `error` | 위반은 오류 목록 및 명령줄 빌드 출력의 *오류로* 나타나고 빌드가 실패합니다.| 잘못된 코드에는 빨간색 물결선이 밑줄로 표시되고 스크롤 막대에 작은 빨간색 상자가 표시됩니다. |
| Warning | `warning` | 위반은 오류 목록 및 명령줄 빌드 출력에 *경고로* 표시되지만 빌드가 실패하지는 않습니다. | 잘못된 코드에는 녹색 물결선이 밑줄로 표시되고 스크롤 막대에 작은 녹색 상자가 표시됩니다. |
| 정보 | `suggestion` | 위반은 오류 목록에 *메시지로* 표시되며 명령줄 빌드 출력에는 전혀 나타나지 않습니다. | 잘못된 코드에는 회색 물결선이 밑줄로 표시되고 스크롤 막대에 작은 회색 상자가 표시됩니다. |
| 숨김 | `silent` | 사용자에게 보이지 않습니다. | 사용자에게 보이지 않습니다. 그러나 진단 유틸리티는 IDE 진단 엔진에 보고됩니다. |
| None | `none` | 완전히 억제되었습니다. | 완전히 억제되었습니다. |
| 기본값 | `default` | 규칙의 기본 심각도에 해당 합니다. 규칙의 기본값을 확인하려면 속성 창을 참조하십시오. | 규칙의 기본 심각도에 해당 합니다. |

코드 편집기의 다음 스크린샷은 서로 다른 상한을 가진 세 가지 위반을 보여 주며 있습니다. 물결모양의 색상과 오른쪽 스크롤 막대의 작고 컬러된 사각형을 확인합니다.

![코드 편집기의 오류, 경고 및 정보 위반](media/diagnostics-severity-colors.png)

다음 스크린샷은 오류 목록에 나타나는 세 가지 위반사항을 보여 주며 다음과 같습니다.

![오류 목록의 오류, 경고 및 정보 위반](media/diagnostics-severities-in-error-list.png)

::: moniker range=">=vs-2019"

### <a name="set-rule-severity-in-an-editorconfig-file"></a>편집기구성 파일에서 규칙 심각도 설정

(비주얼 스튜디오 2019 버전 16.3 이상)

다음과 같은 구문을 사용하여 EditorConfig 파일에서 컴파일러 경고 또는 분석기 규칙에 대한 심각도를 설정할 수 있습니다.

`dotnet_diagnostic.<rule ID>.severity = <severity>`

EditorConfig 파일에서 규칙의 심각도를 설정하는 것은 규칙 집합 또는 솔루션 탐색기에서 설정된 모든 심각도보다 우선합니다. EditorConfig 파일에서 심각도를 [수동으로](#manually-configure-rule-severity) 구성하거나 위반 옆에 나타나는 전구를 통해 [자동으로](#automatically-configure-rule-severity) 구성할 수 있습니다.

### <a name="set-rule-severity-of-multiple-analyzer-rules-at-once-in-an-editorconfig-file"></a>EditorConfig 파일에서 한 번에 여러 분석기 규칙의 규칙 심각도 설정

(비주얼 스튜디오 2019 버전 16.5 이상)

특정 분석기 규칙 범주 또는 EditorConfig 파일의 단일 항목이 있는 모든 분석기 규칙에 대한 심각도를 설정할 수 있습니다.

- 분석기 규칙 범주에 대한 규칙 심각도 설정:

`dotnet_analyzer_diagnostic.category-<rule category>.severity = <severity>`

- 모든 분석기 규칙에 대한 규칙 심각도 설정:

`dotnet_analyzer_diagnostic.severity = <severity>`

특정 규칙 ID에 적용할 수 있는 항목이 여러 개인 경우 다음의 우선 순위에 따라 해당 항목을 선택합니다.

- ID별 개별 규칙에 대한 심각도 항목은 범주에 대한 심각도 항목보다 우선합니다.
- 범주에 대한 심각도 항목은 모든 분석기 규칙에 대한 심각도 항목보다 우선합니다.

[CA1822에](https://docs.microsoft.com/visualstudio/code-quality/ca1822) "성능" 범주가 있는 다음 편집기Config 예제를 살펴보겠습니다.

   ```ini
   [*.cs]
   dotnet_diagnostic.CA1822.severity = error
   dotnet_analyzer_diagnostic.category-performance.severity = warning
   dotnet_analyzer_diagnostic.severity = suggestion
   ```

앞의 예제에서는 세 항목 모두 CA1822에 적용할 수 있습니다. 그러나 지정된 우선 순위 규칙을 사용하면 첫 번째 규칙 ID 기반 심각도 항목이 다음 항목에서 승리합니다. 이 예제에서 CA1822는 "오류"의 유효 심각도를 갖습니다. "성능" 범주가 있는 나머지 모든 규칙에는 심각도 "경고"가 있습니다. "성능" 범주가 없는 나머지 모든 분석기 규칙에는 심각도 "제안"이 있습니다.

#### <a name="manually-configure-rule-severity"></a>규칙 심각도 수동으로 구성

1. 프로젝트에 대한 EditorConfig 파일이 아직 없는 경우 [하나를 추가합니다.](../ide/create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project)

2. 해당 파일 확장자 아래에 구성하려는 각 규칙에 대한 항목을 추가합니다. 예를 들어 [CA1822의](ca1822.md) 심각도를 `error` C# 파일로 설정하려면 항목은 다음과 같습니다.

   ```ini
   [*.cs]
   dotnet_diagnostic.CA1822.severity = error
   ```

> [!NOTE]
> IDE 코드 스타일 분석기의 경우 다른 구문을 사용하여 EditorConfig 파일에서 구성할 `dotnet_style_qualification_for_field = false:suggestion`수도 있습니다. 그러나 `dotnet_diagnostic` 구문을 사용 하 여 심각도 설정 하는 경우 우선 합니다. 자세한 내용은 [EditorConfig 에 대한 언어 규칙을](../ide/editorconfig-language-conventions.md)참조하십시오.

#### <a name="convert-an-existing-ruleset-file-to-editorconfig-file"></a>기존 규칙 집합 파일을 편집기구성 파일로 변환

Visual Studio 2019 버전 16.5부터 규칙 집합 파일은 관리되는 코드에 대한 분석기 구성에 대한 EditorConfig 파일에 더 이상 사용되지 않습니다. 분석기 규칙 심각도 구성에 대한 대부분의 Visual Studio 도구는 규칙 집합 파일 대신 EditorConfig 파일에서 작동하도록 업데이트되었습니다. EditorConfig 파일을 사용하면 Visual Studio IDE 코드 스타일 옵션을 포함하여 분석기 규칙 사용 설명과 분석기 옵션을 모두 구성할 수 있습니다. 기존 규칙 집합 파일을 EditorConfig 파일로 변환하는 것이 좋습니다. 또한 Repo의 루트 또는 솔루션 폴더에 EditorConfig 파일을 저장하는 것이 좋습니다. 리포지토리 또는 솔루션 폴더의 루트를 사용하면 이 파일의 심각도 설정이 전체 리포지토리 또는 솔루션에 각각 자동으로 적용되도록 합니다.

기존 규칙 집합 파일을 EditorConfig 파일로 변환하는 방법에는 몇 가지가 있습니다.

- 비주얼 스튜디오의 규칙 편집기에서 (Visual Studio 2019 16.5 이상 필요). 프로젝트에서 이미 특정 규칙 집합 파일을 `CodeAnalysisRuleSet`사용하여 경우 Visual Studio 내의 규칙 편집기에서 해당 EditorConfig 파일로 변환할 수 있습니다.

    1. 솔루션 탐색기에서 규칙 집합 파일을 두 번 클릭합니다.

       규칙 집합 파일은 규칙 편집기에서 열립니다. 규칙 집합 편집기 상단에 클릭 가능한 **정보 표시줄이** 표시됩니다.

       ![규칙 편집기에서 규칙 집합을 편집기 구성 파일로 변환](media/convert-ruleset-to-editorconfig-file-ruleset-editor.png)

    2. 정보 표시줄 링크를 **클릭합니다.**

       이렇게 하면 EditorConfig 파일을 생성할 디렉터리를 선택할 수 있는 **As 저장** 대화 상자가 열립니다.

    3. **저장** 단추를 **클릭하여** 편집기구성 파일을 생성합니다.

       생성된 편집기Config는 편집기에서 열어야 합니다. 또한 MSBuild 속성은 `CodeAnalysisRuleSet` 더 이상 원래 규칙 집합 파일을 참조하지 않도록 프로젝트 파일에서 업데이트됩니다.

- 명령줄에서:

    1. NuGet 패키지를 설치 [Microsoft.CodeAnalysis.RulesetToEditorconfiger](https://www.nuget.org/packages/Microsoft.CodeAnalysis.RulesetToEditorconfigConverter).

    2. 규칙 `RulesetToEditorconfigConverter.exe` 집합 파일 및 EditorConfig 파일을 명령줄 인수로 사용하여 설치된 패키지에서 실행합니다.

   ```
   Usage: RulesetToEditorconfigConverter.exe <%ruleset_file%> [<%path_to_editorconfig%>]
   ```

변환할 예제 규칙 집합 파일은 다음과 같습니다.

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

변환된 편집기Config 파일은 다음과 같습니다.

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

#### <a name="automatically-configure-rule-severity"></a>규칙 심각도 자동 구성

##### <a name="configure-from-light-bulb-menu"></a>전구 메뉴에서 구성

Visual Studio는 [빠른 작업](../ide/quick-actions.md) 전구 메뉴에서 규칙의 심각도를 구성하는 편리한 방법을 제공합니다.

1. 위반이 발생하면 편집기의 위반 물결선 위로 마우스를 가져가전구 메뉴를 엽니다. 또는 커서를 줄에 놓고 **Ctrl을**+누릅니다.**.** 누릅니다.

2. 전구 메뉴에서 **문제** > 구성 또는 **억제를 \<선택규칙 ID> 심각도입니다.**

   ![Visual Studio의 전구 메뉴에서 규칙 심각도 구성](media/configure-rule-severity.png)

3. 거기에서 심각도 옵션 중 하나를 선택합니다.

   ![규칙 심각도를 제안으로 구성](media/configure-rule-severity-suggestion.png)

   Visual Studio는 Preview 상자에 표시된 대로 편집기Config 파일에 항목을 추가하여 요청된 수준으로 규칙을 구성합니다.

   > [!TIP]
   > 프로젝트에 EditorConfig 파일이 아직 없는 경우 Visual Studio에서 생성합니다.

##### <a name="configure-from-error-list"></a>오류 목록에서 구성

또한 Visual Studio는 오류 목록 컨텍스트 메뉴에서 규칙의 심각도를 구성하는 편리한 방법을 제공합니다.

1. 위반이 발생하면 오류 목록에서 진단 항목을 마우스 오른쪽 단추로 클릭합니다.

2. 컨텍스트 메뉴에서 **심각도 설정을**선택합니다.

   ![Visual Studio의 오류 목록에서 규칙 심각도 구성](media/configure-rule-severity-error-list.png)

3. 거기에서 심각도 옵션 중 하나를 선택합니다.

   Visual Studio는 편집기Config 파일에 항목을 추가하여 규칙을 요청된 수준으로 구성합니다.

   > [!TIP]
   > 프로젝트에 EditorConfig 파일이 아직 없는 경우 Visual Studio에서 생성합니다.

::: moniker-end

### <a name="set-rule-severity-from-solution-explorer"></a>솔루션 탐색기에서 규칙 심각도 설정

1. 솔루션 탐색기에서 **참조** > **분석기(또는** .NET Core 프로젝트에 대한 **종속성** > **분석기)를** 확장합니다.

2. 심각도를 설정할 규칙이 포함된 어셈블리를 확장합니다.

::: moniker range=">=vs-2019"
3. 규칙을 마우스 오른쪽 단추로 클릭하고 **심각도 설정을**선택합니다. 컨텍스트 메뉴에서 심각도 옵션 중 하나를 선택합니다.

   Visual Studio는 편집기Config 파일에 항목을 추가하여 규칙을 요청된 수준으로 구성합니다. 프로젝트에서 EditorConfig 파일 대신 규칙 집합 파일을 사용하는 경우 심각도 항목이 규칙 집합 파일에 추가됩니다.

   > [!TIP]
   > 프로젝트에 EditorConfig 파일 또는 규칙 집합 파일이 아직 없는 경우 Visual Studio에서 새 EditorConfig 파일을 만듭니다.
::: moniker-end

::: moniker range="vs-2017"
3. 규칙을 마우스 오른쪽 단추로 클릭하고 **규칙 설정 심각도 를**선택합니다. 컨텍스트 메뉴에서 심각도 옵션 중 하나를 선택합니다.

   규칙의 심각도는 활성 규칙 집합 파일에 저장됩니다.
::: moniker-end

### <a name="set-rule-severity-in-the-rule-set-file"></a>규칙 집합 파일에서 규칙 심각도 설정

![솔루션 탐색기의 규칙 집합 파일](media/ruleset-in-solution-explorer.png)

1. **솔루션 탐색기에서**활성 규칙 집합 파일을 두 번 클릭하거나 **참조** > **분석기** 노드의 마우스 오른쪽 단추 클릭 메뉴에서 **활성 규칙 집합 열기를** 선택하거나 프로젝트의 **코드 분석** 속성 페이지에서 **열기를** 선택하여 활성 규칙 집합 파일을 엽니다.

   규칙 집합을 처음 편집할 때 Visual Studio는 기본 규칙 집합 파일의 복사본을 만들고 * \<projectname>* 이름을 지정하고 프로젝트에 추가합니다. 이 사용자 지정 규칙 집합은 프로젝트에 대한 활성 규칙 집합이 됩니다.

   > [!NOTE]
   > .NET Core 및 .NET 표준 프로젝트는 **솔루션 탐색기에서**규칙 집합에 대한 메뉴 명령을 지원하지 않습니다( 예: **활성 규칙 집합 열기)** .NET Core 또는 .NET 표준 프로젝트에 대한 기본이 아닌 규칙 집합을 지정하려면 [ **CodeAnalysisRuleSet** 속성을](using-rule-sets-to-group-code-analysis-rules.md#specify-a-rule-set-for-a-project) 프로젝트 파일에 수동으로 추가합니다. Visual Studio 규칙 집합 편집기 UI에서 설정된 규칙 내에서 규칙을 구성할 수 있습니다.

1. 포함된 어셈블리를 확장하여 규칙을 찾아봅습니다.

1. **작업** 열에서 값을 선택하여 드롭다운 목록을 열고 목록에서 원하는 심각도를 선택합니다.

   ![편집기에서 열린 규칙 집합 파일](media/ruleset-file-in-editor.png)

## <a name="suppress-violations"></a>위반 억제

규칙 위반을 억제하는 방법에는 여러 가지가 있습니다.

::: moniker range=">=vs-2019"

- **편집기구성 파일에서**

  심각도를 `none`에 설정합니다. `dotnet_diagnostic.CA1822.severity = none`

- **분석** 메뉴에서

  메뉴 모음에서 빌드 및 활성 문제 **억제를** > **Build and Suppress Active Issues** 선택하여 현재의 모든 위반을 억제합니다. 이를 "베이스라이닝"이라고도 합니다.

::: moniker-end

::: moniker range="vs-2017"

- **분석** 메뉴에서

  실행 코드 분석 **분석을** > 선택하고 메뉴 모음에서**활성 문제 억제를** 선택하여 현재의 모든 위반을 억제합니다. 이를 "베이스라이닝"이라고도 합니다.

::: moniker-end

- **솔루션 탐색기에서**

  규칙의 심각도를 **없음으로**설정합니다.

- 규칙 **집합 편집기에서**

  이름 옆에 있는 확인란을 선택 취소하거나 **작업을** **없음으로**설정합니다.

- 코드 **편집기에서**

  위반이 있는 코드 줄에 커서를 놓고 **Ctrl**+**기간(.)을** 눌러 빠른 작업 메뉴를 **엽니다.**  > **소스/억제 파일에서** **CAXXXX 억제를**선택합니다.

  ![빠른 작업 메뉴에서 진단 억제](media/suppress-diagnostic-from-editor.png)

- 오류 **목록에서**

  억제할 규칙을 선택한 다음 마우스 오른쪽 단추를 클릭하고**소스/억제 파일에서** **억제를** > 선택합니다.

  - **소스에서**표시하지 않으면 **소스에** 추가된 C# [#pragma 경고](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning) 또는 Visual Basic [#Disable 경고](/dotnet/visual-basic/language-reference/directives/directives) 지시문에 대한 미리 보기가 열리고 변경 내용 미리 보기가 열립니다.

    ![코드 파일에 #pragma 경고 추가 미리 보기](media/pragma-warning-preview.png)

  - **억제 파일에서**를 선택하면 **변경 내용 미리 보기** 대화 상자가 <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> 열리고 전역 억제 파일에 추가된 특성의 미리 보기가 표시됩니다.

    ![억제 파일에 표시하기 메시지 표시 속성 추가 미리 보기](media/preview-changes-in-suppression-file.png)

  미리 **보기 변경** 대화 상자에서 **적용을**선택합니다.

  > [!NOTE]
  > **솔루션 탐색기에서** **메뉴 표시 절해제** 옵션이 표시되지 않으면 위반이 빌드에서 시작되고 라이브 분석이 아닌 것일 수 있습니다. **오류 목록에는** 라이브 코드 분석 및 빌드 모두에서 진단 또는 규칙 위반이 표시됩니다. 예를 들어 위반을 해결하기 위해 코드를 편집했지만 다시 빌드하지 않은 경우 빌드 진단이 부실할 수 있으므로 오류 **목록에서**이러한 진단을 표시할 수 없습니다. 라이브 분석 또는 IntelliSense의 진단은 항상 현재 소스와 최신 상태이며 오류 **목록에서**억제할 수 있습니다. 빌드 *진단을* 선택 항목에서 제외하려면 **오류 목록** 소스 필터를 빌드 + **IntelliSense에서** **IntelliSense 만**으로 전환합니다. 그런 다음 억제할 진단을 선택하고 앞에 설명한 대로 진행합니다.
  >
  > ![비주얼 스튜디오에서 오류 목록 소스 필터](media/error-list-filter.png)

## <a name="command-line-usage"></a>명령줄 사용

명령줄에서 프로젝트를 빌드할 때 다음과 같은 조건이 충족되면 규칙 위반이 빌드 출력에 나타납니다.

- 분석기는 VSIX 확장이 아닌 NuGet 패키지로 설치됩니다.

- 프로젝트 코드에서 하나 이상의 규칙이 위반됩니다.

- 위반된 규칙의 [심각도는](#rule-severity) **경고로**설정되며, 이 경우 위반으로 인해 빌드가 실패하지 않거나 **오류가 발생하며,** 이 경우 위반으로 인해 빌드가 실패하게 됩니다.

빌드 출력의 자세한 내용은 규칙 위반이 표시되는지 여부에 영향을 주지 않습니다. **조용한** 세부 사항이 있더라도 규칙 위반은 빌드 출력에 나타납니다.

> [!TIP]
> *FxCopCmd.exe또는* **RunCodeAnalysis** 플래그가 있는 msbuild를 통해 명령줄에서 레거시 분석을 실행하는 데 익숙한 경우 코드 분석기로 이 작업을 수행하는 방법은 다음과 같습니다.

msbuild를 사용하여 프로젝트를 빌드할 때 명령줄에서 분석기 위반을 보려면 다음과 같은 명령을 실행하십시오.

```cmd
msbuild myproject.csproj /target:rebuild /verbosity:minimal
```

다음 이미지에서는 분석기 규칙 위반을 포함하는 프로젝트 빌드의 명령줄 빌드 출력을 보여줍니다.

![규칙 위반을 사용하여 MSBuild 출력](media/command-line-build-analyzers.png)

## <a name="dependent-projects"></a>종속 프로젝트

.NET Core 프로젝트에서 NuGet 분석기가 있는 프로젝트에 대한 참조를 추가하면 해당 분석기도 종속 프로젝트에 자동으로 추가됩니다. 예를 들어 종속 프로젝트가 단위 테스트 프로젝트인 경우 이 동작을 사용하지 않도록 설정하려면 **PrivateAssets** 특성을 설정하여 참조된 프로젝트의 *.csproj* 또는 *.vbproj* 파일에서 NuGet 패키지를 비공개로 표시합니다.

```xml
<PackageReference Include="Microsoft.CodeAnalysis.FxCopAnalyzers" Version="2.9.0" PrivateAssets="all" />
```

## <a name="see-also"></a>참고 항목

- [비주얼 스튜디오의 코드 분석기 개요](../code-quality/roslyn-analyzers-overview.md)
- [코드 분석기 버그 제출](https://github.com/dotnet/roslyn-analyzers/issues)
- [규칙 집합 사용](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
- [코드 분석 경고 억제](../code-quality/in-source-suppression-overview.md)
