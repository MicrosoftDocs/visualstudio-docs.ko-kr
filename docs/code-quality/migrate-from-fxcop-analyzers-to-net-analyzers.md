---
title: FxCop 분석기에서 .NET 분석기로 마이그레이션
ms.custom: SEO-VS-2020
description: FxCop 분석기에서 .NET 분석기로 마이그레이션하는 방법에 대해 알아봅니다.
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
manager: jillfra
ms.openlocfilehash: b62f99b296c0f9624079423d850029f804e5ebe4
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96112180"
---
# <a name="migrate-from-fxcop-analyzers-to-net-analyzers"></a>FxCop 분석기에서 .NET 분석기로 마이그레이션

.NET Compiler Platform ("Roslyn") 분석기의 소스 분석은 관리 코드에 대 한 [레거시 분석](code-analysis-for-managed-code-overview.md) 을 대체 합니다. 대부분의 FxCop (레거시 분석) 규칙은 이미 원본 분석기로 다시 작성 되었습니다.

Visual Studio 2019 16.8 및 .NET 5.0 이전에 이러한 분석기는 `Microsoft.CodeAnalysis.FxCopAnalyzers` [NuGet 패키지로](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers)제공 됩니다.

Visual Studio 2019 16.8 및 .NET 5.0부터 이러한 분석기는 [.NET SDK에 포함](/dotnet/fundamentals/code-analysis/overview)되어 있습니다. `Microsoft.CodeAnalysis.NetAnalyzers` [NuGet 패키지로](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers)도 사용할 수 있습니다. `Microsoft.CodeAnalysis.FxCopAnalyzers` NuGet 패키지는 곧 사용 되지 않을 예정입니다.

## <a name="migration-steps"></a>마이그레이션 단계

아래 단계를 수행 하 여 프로젝트 또는 솔루션을에서 `Microsoft.CodeAnalysis.FxCopAnalyzers` .net 분석기로 마이그레이션합니다.

1. `Microsoft.CodeAnalysis.FxCopAnalyzers`NuGet 패키지 제거

2. [.NET 분석기 사용 또는 설치](install-net-analyzers.md)

3. 추가 규칙 사용: `Microsoft.CodeAnalysis.NetAnalyzers` 에 비해 훨씬 더 보수적인입니다 `Microsoft.CodeAnalysis.FxCopAnalyzers` . FxCopAnalyzers package와 달리 [빌드 경고로 기본적으로 사용](/dotnet/fundamentals/code-analysis/overview#enabled-rules)되는 몇 가지 정확성 규칙만 있습니다. [AnalysisMode](/dotnet/core/project-sdk/msbuild-props#analysismode) MSBuild 속성을 사용자 지정 하 여 [추가 규칙을 사용 하도록 설정할](/dotnet/fundamentals/code-analysis/overview#enable-additional-rules) 수 있습니다. 예를 들어 속성을로 설정 하면 `AllEnabledByDefault` 적용 가능한 모든 CA 규칙이 기본적으로 빌드 경고로 설정 됩니다.

   ```xml
   <PropertyGroup>
     <AnalysisMode>AllEnabledByDefault</AnalysisMode>
   </PropertyGroup>
   ```

## <a name="see-also"></a>참고 항목

- [소스 코드 분석 대 레거시 분석](net-analyzers-faq.md#whats-the-difference-between-legacy-fxcop-and-net-analyzers)
- [레거시 분석에서 .NET 분석기로 마이그레이션](migrate-from-legacy-analysis-to-net-analyzers.md)
- [.NET 분석기 사용 또는 설치](install-net-analyzers.md)
- [.NET 분석기에 대 한 FAQ](net-analyzers-faq.md)
- [.NET 분석기 구성](/dotnet/fundamentals/code-analysis/code-quality-rule-options)
