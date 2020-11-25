---
title: .NET 분석기 사용 또는 설치
ms.date: 08/03/2018
description: .NET SDK에서 .NET 분석기를 사용 하도록 설정 하거나 이러한 분석기를 NuGet 패키지로 설치 하는 방법에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.topic: how-to
helpviewer_keywords:
- .NET analyzers
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: a14d89caba498a07c2447f9df1109e4da9f6a466
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96112172"
---
# <a name="enable-or-install-net-analyzers"></a>.NET 분석기 사용 또는 설치

## <a name="overview"></a>개요

.NET 컴파일러 플랫폼(Roslyn) 분석기는 C# 또는 Visual Basic 코드를 검사하여 코드 품질 및 코드 스타일 문제를 확인합니다. 다음 방법 중 하나를 사용 하 여 이러한 분석기를 사용 하거나 설치할 수 있습니다.

- **.NET sdk에서 사용**: Visual Studio 2019 16.8 및 .Net 5.0부터 이러한 분석기는 [.net sdk에 포함](/dotnet/fundamentals/code-analysis/overview)되어 있습니다. 분석은 기본적으로 .NET 5.0 이상을 대상으로 하는 프로젝트에 대해 사용 하도록 설정 됩니다. 속성을로 설정 하 여 이전 .NET 버전을 대상으로 하는 프로젝트에 대해 코드 분석을 사용 하도록 설정할 수 있습니다 `EnableNETAnalyzers` `true` . 을로 설정 하 여 프로젝트에 대 한 코드 분석을 사용 하지 않도록 설정할 수도 있습니다 `EnableNETAnalyzers` `false` .

- **Nuget 패키지로 설치**: 또는 `Microsoft.CodeAnalysis.NetAnalyzers` Visual Studio 2019에 [nuget 패키지](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers) 를 설치 하 여 이러한 분석기를 설치할 수 있습니다. Visual Studio 2017를 사용할 경우 최신 `2.9.x` 버전의 `Microsoft.CodeAnalysis.FxCopAnalyzers` [NuGet 패키지](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/)를 설치 합니다.

> [!NOTE]
> `Microsoft.CodeAnalysis.NetAnalyzers`가능 하면 [NuGet 패키지](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers)를 설치 하는 대신 .net SDK에서 분석기를 사용 하도록 설정 하는 것이 좋습니다. .NET SDK에서 분석기를 사용 하도록 설정 하면 SDK를 업데이트 하는 즉시 분석기 버그 수정과 새 분석기가 자동으로 다운로드 됩니다.

## <a name="see-also"></a>참고 항목

- [Visual Studio의 코드 분석기 개요](roslyn-analyzers-overview.md)
- [Visual Studio에서 코드 분석기 사용](use-roslyn-analyzers.md)
- [레거시 분석에서 .NET 분석기로 마이그레이션](migrate-from-legacy-analysis-to-net-analyzers.md)
- [FxCop 분석기에서 .NET 분석기로 마이그레이션](migrate-from-fxcop-analyzers-to-net-analyzers.md)
