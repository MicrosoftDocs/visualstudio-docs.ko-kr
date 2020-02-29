---
title: 코드 분석 경고 표시 안 함
ms.date: 12/01/2018
ms.topic: conceptual
helpviewer_keywords:
- source suppression, code analysis
- code analysis, source suppression
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.openlocfilehash: 71d2fe83690e55d49bb23bffb09de91c8f7534b6
ms.sourcegitcommit: 1efb6b219ade7c35068b79fbdc573a8771ac608d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78167626"
---
# <a name="suppress-code-analysis-warnings"></a>코드 분석 경고 표시 안 함

경고가 적용 되지 않는 것을 나타내는 것이 유용한 경우가 많습니다. 이는 팀 멤버에 게 코드를 검토 하 고 경고를 표시 하지 않을 수 있음을 나타냅니다. ISS (원본 내 비 표시)는 <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> 특성을 사용 하 여 경고를 표시 하지 않습니다. 특성은 경고를 생성 한 코드 세그먼트 가까이에 배치할 수 있습니다. <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> 특성을에 입력 하 여 소스 파일에 추가 하거나 **오류 목록** 경고에 대 한 바로 가기 메뉴를 사용 하 여 자동으로 추가할 수 있습니다.

<xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> 특성은 CODE_ANALYSIS 컴파일 기호가 컴파일 타임에 정의 된 경우에만 관리 코드 어셈블리의 IL 메타 데이터에 포함 되는 조건부 특성입니다.

/Cli C++에서 매크로 CA를 사용 하 여 헤더 파일에서 전역\_SUPPRESS_MESSAGE\_\_메시지 또는 CA를 표시 하지\_특성을 추가 합니다.

> [!NOTE]
> 소스 없는 비 표시 메타 데이터를 실수로 전달 하지 않도록 릴리스 빌드에서 소스 비 표시 오류를 사용 하면 안 됩니다. 또한 소스 비 표시 제거의 처리 비용으로 인해 응용 프로그램 성능이 저하 될 수 있습니다.

::: moniker range="vs-2017"

> [!NOTE]
> 프로젝트를 Visual Studio 2017로 마이그레이션하는 경우 많은 수의 코드 분석 경고가 발생 했을 수 있습니다. 경고를 수정할 준비가 되지 않은 경우 > **분석** 을 선택 하 여 **코드 분석을 실행 하 고 활성 문제를 표시**하지 않도록 하 여 모든 경고를 표시 하지 않을 수 있습니다.
>
> ![Visual Studio에서 코드 분석을 실행 하 고 문제를 표시 하지 않습니다.](media/suppress-active-issues.png)

::: moniker-end

::: moniker range=">=vs-2019"

> [!NOTE]
> 프로젝트를 Visual Studio 2019로 마이그레이션하는 경우 많은 수의 코드 분석 경고가 발생 했을 수 있습니다. 경고를 해결할 준비가 되지 않은 경우 > **분석** 을 선택 하 **고 활성 문제를 표시 하지 않도록**설정 하 여 모든 경고를 표시 하지 않을 수 있습니다.

::: moniker-end

## <a name="suppressmessage-attribute"></a>SuppressMessage 특성

**오류 목록**에서 코드 분석 경고의 상황에 맞는 메뉴 또는 오른쪽 클릭 메뉴에서 **표시 안 함** 을 선택 하면 코드 또는 프로젝트의 전역 비 표시 해제 파일에 <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> 특성이 추가 됩니다.

<xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> 특성의 형식은 다음과 같습니다.

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

- **범주** -규칙이 정의 된 범주입니다. 코드 분석 규칙 범주에 대 한 자세한 내용은 [관리 코드 경고](../code-quality/code-analysis-for-managed-code-warnings.md)를 참조 하세요.

- **CheckId** -규칙의 식별자입니다. 지원에는 규칙 식별자에 대 한 짧은 이름과 긴 이름이 모두 포함 됩니다. 약식 이름은 CAXXXX입니다. 긴 이름은 CAXXXX: FriendlyTypeName입니다.

- **근거** -메시지를 표시 하지 않는 이유를 문서화 하는 데 사용 되는 텍스트입니다.

- **MessageId** -각 메시지의 문제에 대 한 고유 식별자입니다.

- **범위** -경고가 표시 되지 않는 대상입니다. 대상이 지정 되지 않은 경우 특성의 대상으로 설정 됩니다. 지원 되는 [범위](xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Scope) 는 다음과 같습니다.

  - [`module`](#module-suppression-scope) -이 범위는 어셈블리에 대 한 경고를 표시 하지 않습니다. 전체 프로젝트에 적용 되는 전역 비 표시 제거입니다.

  - `resource`-([레거시 FxCop](../code-quality/static-code-analysis-for-managed-code-overview.md) 만 해당)이 범위는 모듈 (어셈블리)의 일부인 리소스 파일에 기록 된 진단 정보의 경고를 표시 하지 않습니다. 이 범위는 원본 파일만 분석 하는 C#Roslyn analyzer 진단에 대 한/vb 컴파일러에서 읽고 적용 되지 않습니다.

  - `type`-이 범위는 형식에 대 한 경고를 표시 하지 않습니다.

  - `member`-이 범위는 멤버에 대 한 경고를 표시 하지 않습니다.

  - `namespace`-이 범위는 네임 스페이스 자체에 대 한 경고를 표시 하지 않습니다. 네임 스페이스 내의 형식에 대 한 경고는 표시 하지 않습니다.

  - `namespaceanddescendants`-(컴파일러 버전 3(sp3) 이상 및 Visual Studio 2019 필요)이 범위는 네임 스페이스 및 모든 하위 기호에서 경고를 표시 하지 않습니다. `namespaceanddescendants` 값은 레거시 분석에서 무시 됩니다.

- **대상** -경고를 표시 하지 않을 대상을 지정 하는 데 사용 되는 식별자입니다. 정규화 된 항목 이름을 포함 해야 합니다.

## <a name="suppressmessage-usage"></a>SuppressMessage 사용

코드 분석 경고는 <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> 특성이 적용 되는 수준에서 표시 되지 않습니다. 예를 들어, 특성을 어셈블리, 모듈, 형식, 멤버 또는 매개 변수 수준에서 적용할 수 있습니다. 이는 위반이 발생 하는 코드에 비 표시 정보를 긴밀 하 게 두는 것입니다.

일반 표시 형식에는 규칙 범주 및 규칙 식별자 (사람이 읽을 수 있는 규칙 이름)가 포함 되어 있습니다. 예를 들어 다음과 같은 가치를 제공해야 합니다.

`[SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`

원본 비 표시 메타 데이터를 최소화 하는 엄격한 성능상의 이유가 있는 경우 규칙 이름을 생략할 수 있습니다. 규칙 범주와 해당 규칙 ID는 모두 충분히 고유한 규칙 식별자를 구성 합니다. 예를 들어 다음과 같은 가치를 제공해야 합니다.

`[SuppressMessage("Microsoft.Design", "CA1039")]`

유지 관리 상의 이유로 규칙 이름을 생략 하는 것은 권장 되지 않습니다.

## <a name="suppress-selective-violations-within-a-method-body"></a>메서드 본문 내에서 선택적 위반 표시 안 함

비 표시 특성은 메서드에 적용할 수 있지만 메서드 본문에 포함할 수 없습니다. 이는 <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> 특성을 메서드에 추가 하는 경우 특정 규칙의 모든 위반이 표시 되지 않음을 의미 합니다.

경우에 따라 위반의 특정 인스턴스를 표시 하지 않을 수 있습니다. 예를 들어 이후 코드가 코드 분석 규칙에서 자동으로 제외 되지 않도록 할 수 있습니다. 특정 코드 분석 규칙을 사용 하면 <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> 특성의 `MessageId` 속성을 사용 하 여이 작업을 수행할 수 있습니다. 일반적으로 특정 기호 (지역 변수 또는 매개 변수)의 위반에 대 한 레거시 규칙은 `MessageId` 속성을 준수 합니다. [CA1500: VariableNamesShouldNotMatchFieldNames](../code-quality/ca1500.md) 는 이러한 규칙의 예입니다. 그러나 실행 코드 위반 (기호가 아닌)에 대 한 레거시 규칙은 `MessageId` 속성을 고려 하지 않습니다. 또한 .NET Compiler Platform ("Roslyn") 분석기는 `MessageId` 속성을 고려 하지 않습니다.

규칙의 특정 기호 위반을 억제 하려면 <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> 특성의 `MessageId` 속성에 대 한 기호 이름을 지정 합니다. 다음 예제에서는 [CA1500:VariableNamesShouldNotMatchFieldNames](../code-quality/ca1500.md)&mdash;`name` 변수 및 `age` 변수에 대 한 두 가지 위반 의 코드를 보여 줍니다. `age` 기호에 대 한 위반만 무시 됩니다.

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

## <a name="generated-code"></a>생성 된 코드

관리 코드 컴파일러와 일부 타사 도구는 코드를 신속 하 게 개발 하는 코드를 생성 합니다. 소스 파일에 표시 되는 컴파일러 생성 코드는 일반적으로 `GeneratedCodeAttribute` 특성으로 표시 됩니다.

생성 된 코드에 대 한 코드 분석 경고 및 오류를 표시 하지 않을 지 여부를 선택할 수 있습니다. 이러한 경고 및 오류를 표시 하지 않는 방법에 대 한 자세한 내용은 [How to: ](../code-quality/how-to-suppress-code-analysis-warnings-for-generated-code.md)생성 된 코드에 대 한 경고를 표시 하지 않습니다.

> [!NOTE]
> 코드 분석은 전체 어셈블리나 단일 매개 변수에 적용 될 때 `GeneratedCodeAttribute`를 무시 합니다.

## <a name="global-level-suppressions"></a>전역 수준 비 표시 오류

관리 코드 분석 도구는 어셈블리, 모듈, 형식, 멤버 또는 매개 변수 수준에서 적용 되는 `SuppressMessage` 특성을 검사 합니다. 리소스와 네임 스페이스에 대 한 위반도 발생 시킵니다. 이러한 위반은 전역 수준에서 적용 해야 하며 범위 지정 및 대상 지정이 가능 합니다. 예를 들어 다음 메시지는 네임 스페이스 위반을 억제 합니다.

`[module: SuppressMessage("Microsoft.Design", "CA1020:AvoidNamespacesWithFewTypes", Scope = "namespace", Target = "MyNamespace")]`

> [!NOTE]
> `namespace` 범위를 사용 하 여 경고를 표시 하지 않으면 네임 스페이스 자체에 대해 경고를 표시 하지 않습니다. 네임 스페이스 내의 형식에 대해 경고를 표시 하지 않습니다.

명시적 범위를 지정 하 여 모든 억제를 표현할 수 있습니다. 이러한 비 표시 오류는 전역 수준에서 지속 되어야 합니다. 형식을 데코레이팅하 면 멤버 수준 제거를 지정할 수 없습니다.

전역 수준 비 표시 오류는 명시적으로 제공 된 사용자 소스에 매핑되지 않는 컴파일러 생성 코드를 참조 하는 메시지를 표시 하지 않는 유일한 방법입니다. 예를 들어 다음 코드는 컴파일러에서 내보낸 생성자에 대 한 위반을 억제 합니다.

`[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="Microsoft.Tools.FxCop.Type..ctor()")]`

> [!NOTE]
> `Target`에는 항상 정규화 된 항목 이름이 포함 됩니다.

### <a name="global-suppression-file"></a>전역 비 표시 파일

전역 비 표시 오류 (suppression) 파일은 대상을 지정 하지 않는 전역 수준 비 표시 오류 (suppression) 또는 비 표시 오류 (suppression)를 유지 합니다. 예를 들어 어셈블리 수준 위반에 대 한 비 표시 오류는이 파일에 저장 됩니다. 또한 일부 ASP.NET 비 표시 오류는이 파일에 저장 됩니다 .이 파일은 폼의 코드에 대해 프로젝트 수준 설정을 사용할 수 없기 때문입니다. **오류 목록** 창에 있는 **표시 안 함** 명령의 **Project 비 표시 오류 (suppression) 파일** 옵션을 처음으로 선택 하면 전역 비 표시 오류 (suppression) 파일이 생성 되어 프로젝트에 추가 됩니다.

### <a name="module-suppression-scope"></a>모듈 비 표시 범위

**모듈** 범위를 사용 하 여 전체 어셈블리에 대 한 코드 품질 위반을 억제할 수 있습니다.

예를 들어 _Globalsuppressions_ 표시 프로젝트 파일의 다음 특성은 ASP.NET Core 프로젝트에 대 한 system.threading.tasks.task.configureawait 위반을 표시 하지 않습니다.

`[assembly: System.Diagnostics.CodeAnalysis.SuppressMessage("Reliability", "CA2007:Consider calling ConfigureAwait on the awaited task", Justification = "ASP.NET Core doesn't use thread context to store request context.", Scope = "module")]`

## <a name="see-also"></a>참고 항목

- <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Scope>
- <xref:System.Diagnostics.CodeAnalysis>
- [코드 분석기 사용](../code-quality/use-roslyn-analyzers.md)
