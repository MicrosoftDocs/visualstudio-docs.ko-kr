---
title: FxCop 분석기에서 .NET 분석기로 마이그레이션
ms.custom: SEO-VS-2020
description: FxCop 분석기에서 .NET 분석기로 마이그레이션하는 방법 알아보기
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
ms.openlocfilehash: d6f9c36b1b64abe648c3aa9014c633e4e4949b1a
ms.sourcegitcommit: d4887ef2ca97c55e2dad9f179eec2c9631d91c95
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/06/2021
ms.locfileid: "108798260"
---
# <a name="migrate-from-fxcop-analyzers-to-net-analyzers"></a>FxCop 분석기에서 .NET 분석기로 마이그레이션

.NET Compiler Platform("Roslyn") 분석기별 원본 분석은 관리 코드에 대한 [레거시 분석을 대체합니다.](code-analysis-for-managed-code-overview.md) 많은 레거시 분석(FxCop) 규칙은 이미 원본 분석기로 다시 작성되었습니다.

2019 16.8 및 .NET 5.0을 Visual Studio 전에 이러한 분석기는 `Microsoft.CodeAnalysis.FxCopAnalyzers` [NuGet 패키지](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers)로 제공되었습니다.

Visual Studio 2019 16.8 및 .NET 5.0부터 이러한 분석기는 [.NET SDK 에 포함됩니다.](/dotnet/fundamentals/code-analysis/overview) .NET 5+ SDK로 이동하지 않거나 NuGet 패키지 기반 모델을 선호하는 경우 `Microsoft.CodeAnalysis.NetAnalyzers` [NuGet 패키지](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers)에서도 분석기를 사용할 수 있습니다. 주문형 버전 업데이트에는 패키지 기반 모델을 사용하는 것이 좋습니다.

> [!NOTE]
> 타사 .NET 분석기는 대상 플랫폼에 구애받지 않습니다. 즉, 프로젝트에서 특정 .NET 플랫폼을 대상으로 지정할 필요가 없습니다. 분석기는 `net5.0` 이전 .NET 버전(예: , 및 )을 대상으로 하는 프로젝트에서 작동합니다. `netcoreapp` `netstandard` `net472`

## <a name="migration-steps"></a>마이그레이션 단계

버전부터 `3.3.2` `Microsoft.CodeAnalysis.FxCopAnalyzers` NuGet 패키지는 더 이상 사용되지 않습니다. 프로젝트 또는 솔루션을 에서 .NET 분석기로 마이그레이션하려면 아래 단계를 따르세요. `Microsoft.CodeAnalysis.FxCopAnalyzers`

1. `Microsoft.CodeAnalysis.FxCopAnalyzers`NuGet 패키지 제거

2. [.NET 분석기 를 사용하거나 설치합니다.](install-net-analyzers.md) 프로젝트의 대상 플랫폼을 변경할 필요가 없습니다.

3. 추가 규칙 사용: `Microsoft.CodeAnalysis.NetAnalyzers` 는 에 비해 훨씬 더보수적입니다. `Microsoft.CodeAnalysis.FxCopAnalyzers` FxCopAnalyzers 패키지와 달리 기본적으로 [빌드 경고로 사용하도록 설정되는](/dotnet/fundamentals/code-analysis/overview#enabled-rules)몇 가지 정확성 규칙만 있습니다. [AnalysisMode](/dotnet/core/project-sdk/msbuild-props#analysismode) MSBuild 속성을 사용자 지정하여 [추가 규칙을 사용하도록 설정할](/dotnet/fundamentals/code-analysis/overview#enable-additional-rules) 수 있습니다. 예를 들어 속성을 로 `AllEnabledByDefault` 설정하면 적용 가능한 모든 CA 규칙이 기본적으로 빌드 경고로 사용됩니다.

   ```xml
   <PropertyGroup>
     <AnalysisMode>AllEnabledByDefault</AnalysisMode>
   </PropertyGroup>
   ```

## <a name="see-also"></a>추가 정보

- [소스 코드 분석 대 레거시 분석](net-analyzers-faq.yml#what-s-the-difference-between-legacy-fxcop-and--net-analyzers-)
- [레거시 분석에서 .NET 분석기로 마이그레이션](migrate-from-legacy-analysis-to-net-analyzers.md)
- [.NET 분석기 사용 또는 설치](install-net-analyzers.md)
- [.NET 분석기 FAQ](net-analyzers-faq.yml)
- [.NET 분석기 구성](/dotnet/fundamentals/code-analysis/code-quality-rule-options)
