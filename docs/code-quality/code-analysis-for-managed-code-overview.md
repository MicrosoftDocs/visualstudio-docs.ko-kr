---
title: 관리 코드에 대한 코드 분석
ms.date: 08/27/2020
description: Visual Studio의 .NET Compiler Platform 기반 코드 분석기에 대해 알아봅니다. 이러한 분석기가 관리 되는 어셈블리의 FxCop 정적 분석을 대체 하는 이유를 이해 합니다.
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 643e8457dbbe838d593a7bad38064537b6cbe57d
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94348530"
---
# <a name="overview-of-code-analysis-for-net-in-visual-studio"></a>Visual Studio에서 .NET에 대 한 코드 분석 개요

Visual Studio는 [레거시 분석](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md)을 사용 하 여 관리 되는 어셈블리에 대 한 FxCop 정적 분석 및 최신 [.NET Compiler Platform 기반 코드 분석기](../code-quality/roslyn-analyzers-overview.md)를 사용 하는 두 가지 방법으로 관리 코드의 코드 분석을 수행할 수 있습니다. 사용자가 입력 하는 동안 코드를 실시간으로 분석 하는 .NET Compiler Platform 기반 코드 분석기는 컴파일된 코드만 분석 하는 레거시 FxCop 정적 코드 분석을 대체 합니다.
