---
title: 관리 코드에 대 한 레거시 분석
ms.date: 06/12/2019
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 18c4ebf61e7136d908ad1e444616b0af7ac59a48
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "88238376"
---
# <a name="overview-of-legacy-analysis-for-managed-code-in-visual-studio"></a>Visual Studio에서 관리 코드에 대 한 레거시 분석 개요

Visual Studio는 [레거시 분석](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md)을 사용 하 여 관리 되는 어셈블리에 대 한 FxCop 정적 분석 및 최신 .NET Compiler Platform 기반 [코드 분석기](../code-quality/roslyn-analyzers-overview.md)를 사용 하는 두 가지 방법으로 관리 코드의 코드 분석을 수행할 수 있습니다. 이 항목에서는 레거시 분석에 대해 설명 합니다. .NET Compiler Platform 기반 코드 분석에 대해 자세히 알아보려면 [.NET Compiler Platform 기반 분석기 개요](../code-quality/roslyn-analyzers-overview.md)를 참조 하세요.

관리 코드에 대 한 코드 분석은 관리 되는 어셈블리를 분석 하 고 [.Net 디자인 지침](/dotnet/standard/design-guidelines/)에 명시 된 프로그래밍 및 디자인 규칙의 위반과 같은 어셈블리 관련 정보를 보고 합니다.

분석 도구는 분석하는 동안 수행하는 검사를 경고 메시지로 나타냅니다. 경고 메시지는 관련 프로그래밍 및 디자인 문제를 식별하며 가능한 경우 문제 해결 방법에 대한 정보를 제공합니다.

> [!NOTE]
> Visual Studio에서 .NET Core 및 .NET Standard 프로젝트에 대 한 레거시 분석 (정적 코드 분석)은 지원 되지 않습니다. Msbuild의 일부로 .NET Core 또는 .NET Standard 프로젝트에 대해 코드 분석을 실행 하는 경우 다음과 유사한 오류가 표시 됩니다. **CA0055:에 대 한 \<your.dll> 플랫폼을 식별할 수 **없습니다. .NET Core 또는 .NET Standard 프로젝트에서 코드를 분석 하려면 대신 [코드 분석기](../code-quality/roslyn-analyzers-overview.md) 를 사용 합니다.

## <a name="ide-integrated-development-environment-integration"></a>IDE (통합 개발 환경) 통합

프로젝트에서 수동으로 또는 자동으로 코드 분석을 실행할 수 있습니다.

프로젝트를 빌드할 때마다 코드 분석을 실행 하려면 프로젝트의 **코드 분석** 속성 페이지에서 옵션을 선택 합니다. 자세한 내용은 [방법: 자동 코드 분석 사용 및 사용 안 함](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)을 참조 하세요.

프로젝트에서 수동으로 코드 분석을 실행 하려면 메뉴 모음에서 **분석**  >  **실행 코드 분석**실행  >  **코드 분석 \<project> 실행 **을 선택 합니다.

## <a name="rule-sets"></a>규칙 집합

관리 코드에 대한 코드 분석 규칙은 [규칙 집합](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)으로 그룹화됩니다. Microsoft 표준 규칙 집합 중 하나를 사용 하거나 특정 요구를 충족 하는 [사용자 지정 규칙 집합을 만들](../code-quality/how-to-create-a-custom-rule-set.md) 수 있습니다.

## <a name="suppress-warnings"></a>경고 표시 안 함

경고가 적용되지 않는 것으로 표시하면 유용한 경우가 많습니다. 이렇게 하면 경고를 조사한 다음 이를 표시하지 않거나 무시하도록 설정했다는 것을 개발자와 나중에 이 코드를 검토할 수 있는 다른 사람에게 알릴 수 있습니다.

경고의 소스 내 제거는 사용자 지정 특성을 통해 구현 됩니다. 경고를 표시하지 않으려면 다음 예제와 같이 소스 코드에 `SuppressMessage` 특성을 추가합니다.

```csharp
[System.Diagnostics.CodeAnalysis.SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]
Public class MyClass
{
   // code
}
```

자세한 내용은 [경고 표시 안 함](../code-quality/in-source-suppression-overview.md)을 참조 하세요.

::: moniker range="vs-2017"

> [!NOTE]
> 프로젝트를 Visual Studio 2017로 마이그레이션하는 경우 많은 수의 코드 분석 경고가 발생 했을 수 있습니다. 경고를 수정할 준비가 되지 않은 경우 **분석**  >  **실행 코드 분석을 선택 하 고 활성 문제를 표시**하지 않도록 설정 하 여 모든 경고를 표시 하지 않을 수 있습니다.
>
> ![Visual Studio에서 코드 분석을 실행 하 고 문제를 표시 하지 않습니다.](media/suppress-active-issues.png)

::: moniker-end

::: moniker range=">=vs-2019"

> [!NOTE]
> 프로젝트를 Visual Studio 2019로 마이그레이션하는 경우 많은 수의 코드 분석 경고가 발생 했을 수 있습니다. 경고를 수정할 준비가 되지 않은 경우 빌드 **분석**  >  **및 활성 문제 표시 안**함을 선택 하 여 모든 경고를 표시 하지 않을 수 있습니다.

::: moniker-end

## <a name="run-code-analysis-as-part-of-check-in-policy"></a>체크 인 정책의 일부로 코드 분석 실행

조직에서 반드시 특정 정책에 따라 체크 인을 수행하려는 경우 특히 다음 정책을 따르는지 확인할 수 있습니다.

- 체크 인 된 코드에 빌드 오류가 없습니다.

- 코드 분석은 최신 빌드의 일부로 실행 됩니다.

체크 인 정책을 지정하여 위 사항을 확인할 수 있습니다. 자세한 내용은 [프로젝트 체크 인 정책을 사용 하 여 코드 품질 향상](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md)을 참조 하세요.

## <a name="team-build-integration"></a>팀 빌드 통합

빌드 시스템의 통합된 기능을 사용하여 빌드 프로세스의 일부로 분석 도구를 실행할 수 있습니다. 자세한 내용은 [Azure Pipelines](/azure/devops/pipelines/index?view=vsts)를 참조하세요.

## <a name="see-also"></a>추가 정보

- [.NET Compiler Platform 기반 분석기 개요](../code-quality/roslyn-analyzers-overview.md)
- [규칙 집합을 사용하여 코드 분석 규칙 그룹화](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
- [방법: 자동 코드 분석 사용 설정 및 해제](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)
