---
title: 코드 분석 위반 표시 안 함
ms.date: 05/10/2021
description: Visual Studio 코드 분석 위반을 표시하지 않습니다. 소스 내 비표시 표시에 SuppressMessageAttribute 특성을 사용하는 방법을 이해합니다.
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- source suppression, code analysis
- code analysis, source suppression
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.openlocfilehash: fd177a96b8789760927933fad5c0320553a72f57
ms.sourcegitcommit: 162be102d2c22a1c4ad2c447685abd28e0e85d15
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2021
ms.locfileid: "109973345"
---
# <a name="suppress-code-analysis-violations"></a>코드 분석 위반 표시 안 함

경고를 적용할 수 없음을 나타내는 것이 유용한 경우가 많습니다. 이는 코드가 검토되었으며 경고를 표시하지 않을 수 있음을 팀 멤버에게 나타냅니다. 이 문서에서는 Visual Studio IDE를 사용하여 코드 분석 위반을 표시하지 않을 수 있는 다양한 방법을 설명합니다.

::: moniker range=">=vs-2019"

## <a name="suppress-violations-using-the-editorconfig-file"></a>EditorConfig 파일을 사용하여 위반 표시 안 함

**EditorConfig 파일에서** 심각도를 로 `none` 설정합니다(예: `dotnet_diagnostic.CA1822.severity = none` ). EditorConfig 파일을 추가하려면 [프로젝트에 EditorConfig 파일 추가를](../ide/create-portable-custom-editor-options.md#add-and-remove-editorconfig-files)참조하세요.

::: moniker-end

## <a name="suppress-violations-in-source-code"></a>소스 코드에서 위반 표시 안 함

전처리기 지시문, [#pragma 경고(C#)](/dotnet/csharp/language-reference/preprocessor-directives.md#pragma-warning) 또는 사용 [안 함(Visual Basic)](/dotnet/visual-basic/language-reference/directives/disable-enable.md) 지시문을 사용하여 코드에서 위반을 억제하여 특정 코드 줄에 대해서만 경고를 표시하지 않을 수 있습니다. 또는 [SuppressMessage 특성](#in-source-suppression-and-the-suppressmessage-attribute)를 사용할 수 있습니다.

- 코드 **편집기에서**

  위반이 있는 코드 줄에 커서를 놓고 **Ctrl** + **기간(.)을** 눌러 **빠른 작업** 메뉴를 엽니다. **CAXXXX 표시 안 을** 선택한 다음 원본 또는 **원본(특성)에서** 를 선택합니다. 

  **원본 에서** 를 선택하면 코드에 추가될 전처리기 지시문의 미리 보기가 표시됩니다.

  ::: moniker range="vs-2017"
  :::image type="content" source="media/suppress-diagnostic-from-editor.png" alt-text="빠른 작업 메뉴에서 진단 표시 안 함":::
  ::: moniker-end
  ::: moniker range=">=vs-2019"
  :::image type="content" source="media/vs-2019/suppress-diagnostic-from-editor.png" alt-text="빠른 작업 메뉴에서 진단 표시 안 함":::

  **원본(특성)에서** 를 선택하면 코드에 추가될 [SuppressMessage 특성의](#in-source-suppression-and-the-suppressmessage-attribute) 미리 보기가 표시됩니다.

  :::image type="content" source="media/vs-2019/suppress-diagnostic-from-editor-attribute.png" alt-text="특성을 사용하여 빠른 작업 메뉴에서 진단 표시 안 함":::
  ::: moniker-end

- 오류 **목록에서**

  표시 하지 않을 규칙을 선택한 다음 마우스 오른쪽 단추를 클릭 하 고 소스 **에서 표시 안 함** 을 선택  >  합니다.

  - **소스에서** 표시 하지 않는 경우 **변경 내용 미리 보기** 대화 상자가 열리고 소스 코드에 추가 된 c # [#pragma 경고](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning) 또는 Visual Basic [#Disable 경고](/dotnet/visual-basic/language-reference/directives/directives) 지시문의 미리 보기가 표시 됩니다.

    ![코드 파일에 #pragma 경고 추가의 미리 보기](media/pragma-warning-preview.png)

  **변경 내용 미리 보기** 대화 상자에서 **적용** 을 선택 합니다.

  > [!NOTE]
  > **솔루션 탐색기** 에 **표시 안 함** 메뉴 옵션이 표시 되지 않는 경우에는 위반이 발생 했을 수 있습니다. **오류 목록** 는 라이브 코드 분석과 빌드 모두에서 진단 또는 규칙 위반을 표시 합니다. 빌드 진단은 부실 할 수 있습니다. 예를 들어 위반 문제를 해결 하기 위해 코드를 편집 했지만 다시 빌드하지 않은 경우에는 **오류 목록** 에서 이러한 진단을 표시 하지 않을 수 있습니다. 라이브 분석 또는 IntelliSense의 진단은 항상 최신 원본으로 최신 상태를 유지 하며 **오류 목록** 에서 표시 되지 않을 수 있습니다. 선택에서 *빌드* 진단을 제외 하려면 **빌드 + Intellisense** 에서 **intellisense 전용** 으로 **오류 목록** 원본 필터를 전환 합니다. 그런 다음 앞에서 설명한 대로 표시 하지 않을 진단을 선택 하 고 계속 진행 합니다.
  >
  > ![Visual Studio에서 원본 필터 오류 목록](media/error-list-filter.png)

## <a name="suppress-violations-using-a-global-suppression-file"></a>전역 비 표시 파일을 사용 하 여 위반 표시 안 함

[전역 비 표시 오류 (suppression) 파일](#global-level-suppressions) 은 [SuppressMessage 특성](#in-source-suppression-and-the-suppressmessage-attribute)을 사용 합니다.

- **오류 목록** 에서 표시 하지 않을 규칙을 선택한 다음 마우스 오른쪽 단추를 클릭 하 고 비 **표시 표시 안 함 파일에서 표시 안 함** 을 선택  >  합니다. **변경 내용 미리 보기** 대화 상자가 열리고 전역 비 표시 오류 ( <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> suppression) 파일에 추가 된 특성의 미리 보기가 표시 됩니다.

  ![SuppressMessage 특성을 비 표시 오류 (suppression) 파일에 추가 하는 미리 보기](media/preview-changes-in-suppression-file.png)

- 코드 **편집기에서** 위반이 있는 코드 줄에 커서를 놓고 **빠른 작업 및 리팩터링을** 누르거나 **Ctrl** + **기간(.)을** 눌러 **빠른 작업** 메뉴를 엽니다. **CAXXXX 표시 안 을** 선택한 다음, **비표시 파일 에서** 를 선택합니다. 만들거나 수정할 [전역 비제어 파일의](#global-level-suppressions) 미리 보기가 표시됩니다.

::: moniker range=">=vs-2019"

- **분석** 메뉴에서 빌드 **분석** 및 활성 문제 표시 안  >  **을** 선택하여 현재 위반을 모두 표시하지 않습니다. 이를 "기준선"이라고도 합니다.

::: moniker-end
::: moniker range="vs-2017"

- **분석** 메뉴에서 실행 Code Analysis **분석** 및 활성 문제 표시 안  >  **을** 선택하여 현재 위반을 모두 표시하지 않습니다. 이를 "기준선"이라고도 합니다.
::: moniker-end

## <a name="suppress-violations-using-project-settings"></a>프로젝트 설정을 사용하여 위반 표시 안 함

**솔루션 탐색기** 프로젝트의 속성을 열고(프로젝트를 마우스 오른쪽 단추로 클릭하고 **속성을** 선택하거나, **Alt+Enter를** 누른 상태에서) **Code Analysis** 탭을 사용하여 옵션을 구성합니다. 예를 들어 라이브 코드 분석을 사용하지 않도록 설정하거나 .NET 분석기를 사용하지 않도록 설정할 수 있습니다.

## <a name="suppress-violations-using-a-rule-set"></a>규칙 집합을 사용하여 위반 표시 안 함

규칙 **집합 편집기** 에서 이름 옆에 있는 확인란의 선택 취소를 선택하거나 **작업을** **없음으로** 설정합니다.

## <a name="in-source-suppression-and-the-suppressmessage-attribute"></a>원본 내 비표시 및 SuppressMessage 특성

ISS(In-Source Suppression)는 특성을 사용하여 <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> 경고를 표시하지 않습니다. 경고를 생성한 코드 세그먼트 가까이에 특성을 배치할 수 있습니다. <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute>특성을 입력하여 원본 파일에 추가하거나 **오류 목록의** 경고에 대한 바로 가기 메뉴를 사용하여 자동으로 추가할 수 있습니다.

특성은 CODE_ANALYSIS <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> 컴파일 기호가 컴파일 시간에 정의된 경우에만 관리 코드 어셈블리의 IL 메타데이터에 포함되는 조건부 특성입니다.

C++/CLI에서 헤더 파일의 CA SUPPRESS MESSAGE 또는 CA GLOBAL SUPPRESS_MESSAGE 매크로를 사용하여 \_ 특성을 \_ \_ \_ 추가합니다.

> [!NOTE]
> 소스 없는 비 표시 메타 데이터를 실수로 전달 하지 않도록 릴리스 빌드에서 소스 비 표시 오류를 사용 하면 안 됩니다. 또한 소스 비 표시 제거의 처리 비용으로 인해 응용 프로그램 성능이 저하 될 수 있습니다.

::: moniker range="vs-2017"

> [!NOTE]
> 프로젝트를 Visual Studio 2017로 마이그레이션하는 경우 많은 수의 코드 분석 경고가 발생 했을 수 있습니다. 경고를 수정할 준비가 되지 않은 경우 **분석**  >  **실행 코드 분석을 선택 하 고 활성 문제를 억제** 하 여 모든 경고를 표시 하지 않을 수 있습니다.
>
> ![Visual Studio에서 코드 분석을 실행 하 고 문제를 표시 하지 않습니다.](media/suppress-active-issues.png)

::: moniker-end

::: moniker range=">=vs-2019"

> [!NOTE]
> 프로젝트를 Visual Studio 2019로 마이그레이션하는 경우 많은 수의 코드 분석 경고가 발생 했을 수 있습니다. 경고를 수정할 준비가 되지 않은 경우 빌드 **분석** 을 선택 하  >  **고 활성 문제를 표시** 하지 않으면 모든 경고를 표시 하지 않을 수 있습니다.

::: moniker-end

### <a name="suppressmessage-attribute"></a>SuppressMessage 특성

**오류 목록** 에서 코드 분석 경고의 상황에 맞는 메뉴 또는 오른쪽 클릭 메뉴에서 **표시 안 함** 을 선택 하면 <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> 코드 또는 프로젝트의 전역 비 표시 오류 (suppression) 파일에 특성이 추가 됩니다.

<xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute>특성의 형식은 다음과 같습니다.

```vb
<Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")>
```

```csharp
[Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")]
```

```cpp
CA_SUPPRESS_MESSAGE("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")
```

특성의 속성은 다음과 같습니다.

- **범주** -규칙이 정의 된 범주입니다. 코드 분석 규칙 범주에 대 한 자세한 내용은 [관리 코드 경고](/dotnet/fundamentals/code-analysis/quality-rules/index)를 참조 하세요.

- **CheckId** -규칙의 식별자입니다. 지원에는 규칙 식별자에 대 한 짧은 이름과 긴 이름이 모두 포함 됩니다. 약식 이름은 CAXXXX입니다. 긴 이름은 CAXXXX: FriendlyTypeName입니다.

- **근거** -메시지를 표시 하지 않는 이유를 문서화 하는 데 사용 되는 텍스트입니다.

- **MessageId** -각 메시지의 문제에 대 한 고유 식별자입니다.

- **범위** -경고가 표시 되지 않는 대상입니다. 대상이 지정 되지 않은 경우 특성의 대상으로 설정 됩니다. 지원 되는 [범위](xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Scope) 는 다음과 같습니다.

  - [`module`](#module-suppression-scope) - 이 범위는 어셈블리에 대한 경고를 표시하지 않습니다. 전체 프로젝트에 적용되는 전역 비제어입니다.

  - `resource` - ([레거시 FxCop에만](../code-quality/static-code-analysis-for-managed-code-overview.md) 해당) 이 범위는 모듈(어셈블리)의 일부인 리소스 파일에 기록된 진단 정보의 경고를 표시하지 않습니다. 이 범위는 원본 파일만 분석하는 Roslyn 분석기 진단용 C#/VB 컴파일러에서 읽기/준수되지 않습니다.

  - `type` - 이 범위는 형식에 대한 경고를 표시하지 않습니다.

  - `member` - 이 범위는 멤버에 대한 경고를 표시하지 않습니다.

  - `namespace` - 이 범위는 네임스페이스 자체에 대한 경고를 표시하지 않습니다. 네임스페이스 내의 형식에 대한 경고를 표시하지 않습니다.

  - `namespaceanddescendants` - (컴파일러 버전 3.x 이상 및 Visual Studio 2019가 필요함) 이 범위는 네임스페이스 및 모든 하위 기호에서 경고를 표시하지 않습니다. `namespaceanddescendants`값은 레거시 분석에서 무시됩니다.

- **대상** - 경고가 표시되지 않는 대상을 지정하는 데 사용되는 식별자입니다. 정규화된 항목 이름을 포함해야 합니다.

Visual Studio 경고가 표시되면 `SuppressMessage` [전역 비제어 파일](../code-quality/use-roslyn-analyzers.md#suppress-violations)에 표시 안 함을 추가하여 의 예를 볼 수 있습니다. 비표시 특성 및 해당 필수 속성이 미리 보기 창에 표시됩니다.

### <a name="suppressmessage-usage"></a>SuppressMessage 사용량

Code Analysis 경고는 특성이 적용되는 수준에서 표시되지 <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> 않습니다. 예를 들어 어셈블리, 모듈, 형식, 멤버 또는 매개 변수 수준에서 특성을 적용할 수 있습니다. 이 작업의 목적은 위반이 발생하는 코드에 비제어 정보를 긴밀하게 결합하는 것입니다.

일반적인 형태의 비표시에는 규칙 이름에 대한 선택적 사람이 읽을 수 있는 표현을 포함하는 규칙 범주 및 규칙 식별자가 포함됩니다. 예를 들면 다음과 같습니다.

`[SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`

원본 내 비제어 메타데이터를 최소화하는 엄격한 성능 이유가 있는 경우 규칙 이름을 생략할 수 있습니다. 규칙 범주와 해당 규칙 ID는 모두 충분히 고유한 규칙 식별자를 구성 합니다. 예를 들면 다음과 같습니다.

`[SuppressMessage("Microsoft.Design", "CA1039")]`

유지 관리 상의 이유로 규칙 이름을 생략 하는 것은 권장 되지 않습니다.

### <a name="suppress-selective-violations-within-a-method-body"></a>메서드 본문 내에서 선택적 위반 표시 안 함

비 표시 특성은 메서드에 적용할 수 있지만 메서드 본문에 포함할 수 없습니다. 이는 메서드에 특성을 추가 하는 경우 특정 규칙의 모든 위반이 표시 되지 않음을 의미 <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> 합니다.

경우에 따라 위반의 특정 인스턴스를 표시 하지 않을 수 있습니다. 예를 들어 이후 코드가 코드 분석 규칙에서 자동으로 제외 되지 않도록 할 수 있습니다. 특정 코드 분석 규칙을 사용 하면 특성의 속성을 사용 하 여이 작업을 수행할 수 있습니다 `MessageId` <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> . 일반적으로 특정 기호 (지역 변수 또는 매개 변수)의 위반에 대 한 레거시 규칙은 속성을 준수 `MessageId` 합니다. [CA1500: VariableNamesShouldNotMatchFieldNames](../code-quality/ca1500.md) 는 이러한 규칙의 예입니다. 그러나 실행 코드 위반 (기호가 아닌)에 대 한 레거시 규칙은 속성을 고려 하지 않습니다 `MessageId` . 또한 .NET Compiler Platform ("Roslyn") 분석기는 속성을 고려 하지 않습니다 `MessageId` .

규칙의 특정 기호 위반을 억제 하려면 특성의 속성에 대 한 기호 이름을 지정 합니다 `MessageId` <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> . 다음 예제에서는 두 가지 위반 CA1500 인 코드를 보여 줍니다 [.](../code-quality/ca1500.md) &mdash; 하나는 변수에 대 한 VariableNamesShouldNotMatchFieldNames이 `name` 고 다른 하나는 변수에 대 한 것 `age` 입니다. 기호에 대 한 위반만 `age` 무시 됩니다.

```vb
Public Class Animal
    Dim age As Integer
    Dim name As String

    <CodeAnalysis.SuppressMessage("Microsoft.Maintainability", "CA1500:VariableNamesShouldNotMatchFieldNames", MessageId:="age")>
    Sub PrintInfo()
        Dim age As Integer = 5
        Dim name As String = "Charlie"

        Console.WriteLine("Age {0}, Name {1}", age, name)
    End Sub

End Class
```

```csharp
public class Animal
{
    int age;
    string name;

    [System.Diagnostics.CodeAnalysis.SuppressMessage("Microsoft.Maintainability", "CA1500:VariableNamesShouldNotMatchFieldNames", MessageId = "age")]
    private void PrintInfo()
    {
        int age = 5;
        string name = "Charlie";

        Console.WriteLine($"Age {age}, Name {name}");
    }
}
```

### <a name="global-level-suppressions"></a>전역 수준 비 표시 오류

관리 코드 분석 도구는 `SuppressMessage` 어셈블리, 모듈, 형식, 멤버 또는 매개 변수 수준에서 적용 되는 특성을 검사 합니다. 리소스와 네임 스페이스에 대 한 위반도 발생 시킵니다. 이러한 위반은 전역 수준에서 적용 해야 하며 범위 지정 및 대상 지정이 가능 합니다. 예를 들어 다음 메시지는 네임 스페이스 위반을 억제 합니다.

`[module: SuppressMessage("Microsoft.Design", "CA1020:AvoidNamespacesWithFewTypes", Scope = "namespace", Target = "MyNamespace")]`

> [!NOTE]
> 범위가 포함 된 경고를 표시 하지 `namespace` 않으면 네임 스페이스 자체에 대해 경고를 표시 하지 않습니다. 네임스페이스 내의 형식에 대한 경고를 표시하지 않습니다.

명시적 범위를 지정하여 모든 비표시(suppression)를 표현할 수 있습니다. 이러한 비제어는 전역 수준에서 유지되어야 합니다. 형식을 데코레이팅하여 멤버 수준 비제한을 지정할 수 없습니다.

전역 수준 비표시 오류(suppressions)는 명시적으로 제공된 사용자 소스에 매핑되지 않는 컴파일러 생성 코드를 참조하는 메시지를 표시하지 않는 유일한 방법입니다. 예를 들어 다음 코드는 컴파일러에서 내보낸 생성자에 대한 위반을 표시하지 않습니다.

`[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="Microsoft.Tools.FxCop.Type..ctor()")]`

> [!NOTE]
> `Target` 에는 항상 정규화된 항목 이름이 포함됩니다.

#### <a name="global-suppression-file"></a>전역 비제어 파일

전역 비표시 파일은 대상을 지정하지 않는 전역 수준 비표시 또는 비표시(suppression)인 비표시(suppression)를 유지 관리합니다. 예를 들어 어셈블리 수준 위반에 대한 비제어는 이 파일에 저장됩니다. 또한 프로젝트 수준 설정을 양식 뒤에 있는 코드에 사용할 수 없으므로 일부 ASP.NET 제거가 이 파일에 저장됩니다. 오류 **목록** 창에서 Suppress 명령의 **프로젝트 비표시 파일 옵션을** 처음 선택하면 전역 **비표시** 파일이 만들어지고 프로젝트에 추가됩니다.

#### <a name="module-suppression-scope"></a>모듈 비제어 범위

**모듈** 범위를 사용하여 전체 어셈블리에 대한 코드 품질 위반을 표시하지 않을 수 있습니다.

예를 들어 _GlobalSuppressions_ 프로젝트 파일의 다음 특성은 ASP.NET Core 프로젝트에 대한 ConfigureAwait 위반을 표시하지 않습니다.

`[assembly: System.Diagnostics.CodeAnalysis.SuppressMessage("Reliability", "CA2007:Consider calling ConfigureAwait on the awaited task", Justification = "ASP.NET Core doesn't use thread context to store request context.", Scope = "module")]`

### <a name="generated-code"></a>생성된 코드

관리 코드 컴파일러 및 일부 타사 도구는 신속한 코드 개발을 용이하게 하는 코드를 생성합니다. 소스 파일에 나타나는 컴파일러 생성 코드는 일반적으로 `GeneratedCodeAttribute` 특성으로 표시됩니다.

소스 코드 분석의 경우 파일에서 생성된 코드의 메시지를 표시하지 않을 수 `.editorconfig` 있습니다. 자세한 내용은 [생성된 코드 제외를 참조하세요.](/dotnet/fundamentals/code-analysis/configuration-options#exclude-generated-code)

레거시 코드 분석의 경우 생성된 코드에 대한 코드 분석 경고 및 오류를 표시하지 않을지 여부를 선택할 수 있습니다. 이러한 경고 및 오류를 표시 하지 않는 방법에 대 한 자세한 내용은 [방법: 생성 된 코드에 대 한 경고 표시 안 함](../code-quality/how-to-suppress-code-analysis-warnings-for-generated-code.md)을 참조 하세요.

> [!NOTE]
> 코드 분석 `GeneratedCodeAttribute` 은 전체 어셈블리나 단일 매개 변수에 적용 되는 경우를 무시 합니다.

## <a name="see-also"></a>참고 항목

- <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Scope>
- <xref:System.Diagnostics.CodeAnalysis>
- [코드 분석기 사용](../code-quality/use-roslyn-analyzers.md)
