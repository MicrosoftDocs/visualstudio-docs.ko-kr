---
title: 관리 코드에 대한 코드 분석
ms.date: 06/12/2019
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: e6515c0df7a9c3389e754d5238788d716be49e2e
ms.sourcegitcommit: a801ca3269274ce1de4f6b2c3f40b58bbaa3f460
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88800088"
---
# <a name="overview-of-code-analysis-for-managed-code-in-visual-studio"></a>Visual Studio에서 관리 코드에 대 한 코드 분석 개요

Visual Studio는 다음과 같은 두 가지 방법으로 관리 코드의 코드 분석을 수행할 수 있습니다.
- [레거시 분석](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md)을 사용 하 여 관리 되는 어셈블리에 대 한 FxCop 정적 분석이 라고도 합니다.
- 최신 [.NET Compiler Platform 기반 코드 분석기](../code-quality/roslyn-analyzers-overview.md)를 사용 합니다. 사용자가 입력 하는 동안 코드를 실시간으로 분석 하는 .NET Compiler Platform 기반 코드 분석기는 컴파일된 코드만 분석 하는 레거시 FxCop 정적 코드 분석을 대체 합니다.