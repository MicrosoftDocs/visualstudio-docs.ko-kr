---
title: FxCop에서 소스 분석으로 마이그레이션 (.NET 분석기)
ms.custom: SEO-VS-2020
description: 처음으로 코드를 분석 하거나, FxCop (이진 분석)에서 소스 분석 (.NET 분석기)을 사용 하 여 관리 코드를 분석 하는 새로운 방법으로 마이그레이션하는 방법에 대해 알아봅니다.
ms.date: 03/06/2020
ms.topic: conceptual
f1_keywords:
- vs.projectpropertypages.codeanalysis
helpviewer_keywords:
- FxCop, migration
- legacy analysis, migration
- source code analysis, migration
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: 9a673e7467816e71b8240de9e5f68840c9188dcd
ms.sourcegitcommit: d4887ef2ca97c55e2dad9f179eec2c9631d91c95
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/06/2021
ms.locfileid: "108798234"
---
# <a name="migrate-from-legacy-analysis-fxcop-to-source-analysis-net-analyzers"></a>레거시 분석 (FxCop)에서 원본 분석 (.NET 분석기)으로 마이그레이션

.NET Compiler Platform ("Roslyn") 분석기의 소스 분석은 관리 코드에 대 한 [레거시 분석](../code-quality/code-analysis-for-managed-code-overview.md) 을 대체 합니다. .NET Core, .NET Standard 프로젝트 등의 최신 프로젝트 템플릿에서는 레거시 분석을 사용할 수 없습니다.

대부분의 FxCop (레거시 분석) 규칙은 Roslyn 코드 분석기 집합인 .NET 분석기에 대해 이미 다시 작성 되었습니다. Roslyn 분석기는 컴파일러를 실행 하는 동안 소스 코드 기반 분석을 실행 합니다. 분석기 결과는 컴파일러 결과와 함께 보고됩니다.

레거시 분석 및 원본 분석 간의 차이점에 대 한 자세한 내용은 다음을 참조 하세요.

- [소스 코드 분석 대 레거시 분석](../code-quality/net-analyzers-faq.yml#what-s-the-difference-between-legacy-fxcop-and--net-analyzers-)

- [.NET 분석기에 대 한 FAQ](../code-quality/net-analyzers-faq.yml)

## <a name="migration"></a>마이그레이션

원본 분석으로 마이그레이션하려면 [.net 분석기를 사용 하도록 설정 하거나 설치](install-net-analyzers.md)합니다. 레거시 분석 규칙 위반과 마찬가지로 소스 코드 분석 위반은 Visual Studio의 오류 목록 창에 표시됩니다. 소스 코드 분석 위반은 코드 편집기에도 표시되며, 위반 코드 아래에 *오류 표시선* 이 나타납니다. 물결선의 색은 규칙의 [심각도 설정](../code-quality/use-roslyn-analyzers.md#configure-severity-levels)에 따라 달라집니다. 새 .NET 분석기로 이식 된 규칙의 상태를 확인 하려면 이식 된 [규칙 및 이식](../code-quality/fxcop-rule-port-status.md)되지 않은 규칙을 참조 하세요.

> [!NOTE]
> Visual Studio 2019 16.8 및 .NET 5.0 이전에 이러한 분석기는 `Microsoft.CodeAnalysis.FxCopAnalyzers` [NuGet 패키지로](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers)제공 됩니다. Visual Studio 2019 16.8 및 .NET 5.0부터 이러한 분석기는 [.NET SDK에 포함](/dotnet/fundamentals/code-analysis/overview)되어 있습니다. `Microsoft.CodeAnalysis.NetAnalyzers` [NuGet 패키지로](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers)도 사용할 수 있습니다. 자세한 내용은 [FxCop 분석기에서 .net 분석기로 마이그레이션](migrate-from-fxcop-analyzers-to-net-analyzers.md)을 참조 하세요.

## <a name="configuration"></a>구성

.NET 분석기를 구성 하는 방법에 대 한 자세한 내용은 다음과 같습니다.

- .NET 분석기를 구성 하려면 [.net 분석기 구성](/dotnet/fundamentals/code-analysis/code-quality-rule-options)을 참조 하세요.

- EditorConfig 또는 규칙 집합 파일을 사용 하 여 미리 정의 된 규칙을 사용 하 여 분석기를 구성 하는 방법에 대해 알아보려면 [규칙 범주 사용](/dotnet/fundamentals/code-analysis/code-quality-rule-options)을 참조 하세요.

## <a name="see-also"></a>추가 정보

- [FxCop 분석기에서 .NET 분석기로 마이그레이션](migrate-from-fxcop-analyzers-to-net-analyzers.md)
