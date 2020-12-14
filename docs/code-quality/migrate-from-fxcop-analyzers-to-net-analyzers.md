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
ms.openlocfilehash: 5f9794c825012d682ca40dfdc5ebbfa03f0614ee
ms.sourcegitcommit: 40d758f779d42c66cb02ae7face8a62763a8662b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97398379"
---
# <a name="migrate-from-fxcop-analyzers-to-net-analyzers"></a>FxCop 분석기에서 .NET 분석기로 마이그레이션

.NET Compiler Platform ("Roslyn") 분석기의 소스 분석은 관리 코드에 대 한 [레거시 분석](code-analysis-for-managed-code-overview.md) 을 대체 합니다. 대부분의 FxCop (레거시 분석) 규칙은 이미 원본 분석기로 다시 작성 되었습니다.

Visual Studio 2019 16.8 및 .NET 5.0 이전에 이러한 분석기는 `Microsoft.CodeAnalysis.FxCopAnalyzers` [NuGet 패키지로](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers)제공 됩니다.

Visual Studio 2019 16.8 및 .NET 5.0부터 이러한 분석기는 [.NET SDK에 포함](/dotnet/fundamentals/code-analysis/overview)되어 있습니다. .NET 5 + SDK로 이동 하지 않으려는 경우 또는 NuGet 패키지 기반 모델을 선호 하는 경우 `Microsoft.CodeAnalysis.NetAnalyzers` [nuget 패키지](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers)에서도 분석기를 사용할 수 있습니다. 주문형 버전 업데이트에 대 한 패키지 기반 모델을 사용 하는 것이 좋습니다.

> [!NOTE]
> 자사 .NET 분석기는 대상 플랫폼에 독립적입니다. 즉, 프로젝트가 특정 .NET 플랫폼을 대상으로 하지 않아도 됩니다. 분석기는,, 등의 이전 .NET 버전 뿐만 아니라를 대상으로 하는 프로젝트에 대해 작동 `net5.0` `netcoreapp` `netstandard` `net472` 합니다.

## <a name="migration-steps"></a>마이그레이션 단계

버전부터 `3.3.2` `Microsoft.CodeAnalysis.FxCopAnalyzers` NuGet 패키지는 더 이상 사용 되지 않습니다. 아래 단계를 수행 하 여 프로젝트 또는 솔루션을에서 `Microsoft.CodeAnalysis.FxCopAnalyzers` .net 분석기로 마이그레이션합니다.

1. `Microsoft.CodeAnalysis.FxCopAnalyzers`NuGet 패키지 제거

2. [.Net 분석기를 사용 하도록 설정 하거나 설치](install-net-analyzers.md)합니다. 프로젝트의 대상 플랫폼을 변경할 필요는 없습니다.

3. 추가 규칙 사용: `Microsoft.CodeAnalysis.NetAnalyzers` 에 비해 훨씬 더 보수적인입니다 `Microsoft.CodeAnalysis.FxCopAnalyzers` . FxCopAnalyzers package와 달리 [빌드 경고로 기본적으로 사용](/dotnet/fundamentals/code-analysis/overview#enabled-rules)되는 몇 가지 정확성 규칙만 있습니다. [AnalysisMode](/dotnet/core/project-sdk/msbuild-props#analysismode) MSBuild 속성을 사용자 지정 하 여 [추가 규칙을 사용 하도록 설정할](/dotnet/fundamentals/code-analysis/overview#enable-additional-rules) 수 있습니다. 예를 들어 속성을로 설정 하면 `AllEnabledByDefault` 적용 가능한 모든 CA 규칙이 기본적으로 빌드 경고로 설정 됩니다.

   ```xml
   <PropertyGroup>
     <AnalysisMode>AllEnabledByDefault</AnalysisMode>
   </PropertyGroup>
   ```

## <a name="see-also"></a>참조

- [소스 코드 분석 대 레거시 분석](net-analyzers-faq.md#whats-the-difference-between-legacy-fxcop-and-net-analyzers)
- [레거시 분석에서 .NET 분석기로 마이그레이션](migrate-from-legacy-analysis-to-net-analyzers.md)
- [.NET 분석기 사용 또는 설치](install-net-analyzers.md)
- [.NET 분석기에 대 한 FAQ](net-analyzers-faq.md)
- [.NET 분석기 구성](/dotnet/fundamentals/code-analysis/code-quality-rule-options)
