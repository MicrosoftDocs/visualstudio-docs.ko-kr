---
title: 레거시 분석 (FxCop)에서 원본 분석 (FxCop 분석기)으로 마이그레이션
description: 처음으로 코드를 분석 하거나, FxCop (이진 분석)에서 소스 분석 (FxCop 분석기)을 사용 하 여 관리 코드를 분석 하는 새로운 방법으로 마이그레이션하는 방법에 대해 알아봅니다.
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
ms.openlocfilehash: 9157d47278f835232308dc497965afebb294f8fd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "78937562"
---
# <a name="migrate-from-legacy-analysis-fxcop-to-source-analysis-fxcop-analyzers"></a>레거시 분석 (FxCop)에서 원본 분석 (FxCop 분석기)으로 마이그레이션

.NET Compiler Platform ("Roslyn") 분석기의 소스 분석은 관리 코드에 대 한 [레거시 분석](../code-quality/code-analysis-for-managed-code-overview.md) 을 대체 합니다. .NET Core, .NET Standard 프로젝트 등의 최신 프로젝트 템플릿에서는 레거시 분석을 사용할 수 없습니다.

대부분의 FxCop (레거시 분석) 규칙은 Roslyn 코드 분석기 집합인 FxCop 분석기에 대해 이미 다시 작성 되었습니다. FxCop 분석기는 프로젝트 또는 솔루션에서 참조 하는 [NuGet 패키지로 설치](install-fxcop-analyzers.md#nuget-package) 합니다. 컴파일러 실행 동안 FxCop 분석기는 소스 코드 기반 분석을 실행합니다. 분석기 결과는 컴파일러 결과와 함께 보고됩니다.

레거시 분석 및 원본 분석 간의 차이점에 대 한 자세한 내용은 다음을 참조 하세요.

- [소스 코드 분석 대 레거시 분석](../code-quality/roslyn-analyzers-overview.md#source-code-analysis-versus-legacy-analysis)

- [FxCop 분석기에 대 한 FAQ](../code-quality/fxcop-analyzers-faq.md)

원본 분석으로 마이그레이션하려면 [FxCop 분석기를 설치](../code-quality/install-fxcop-analyzers.md)합니다. 레거시 분석 규칙 위반과 마찬가지로 소스 코드 분석 위반은 Visual Studio의 오류 목록 창에 표시됩니다. 소스 코드 분석 위반은 코드 편집기에도 표시되며, 위반 코드 아래에 *오류 표시선*이 나타납니다. 물결선의 색은 규칙의 [심각도 설정](../code-quality/use-roslyn-analyzers.md#rule-severity)에 따라 달라집니다. 새 FxCop 분석기로 이식 된 규칙의 상태를 확인 하려면 이식 된 [규칙 및 이식](../code-quality/fxcop-rule-port-status.md)되지 않은 규칙을 참조 하세요.

FxCop 분석기를 구성 하는 방법에 대 한 자세한 내용은 다음을 확인 하세요.

- FxCop 분석기를 구성 하려면 [fxcop 분석기 구성](../code-quality/configure-fxcop-analyzers.md)을 참조 하세요.

- EditorConfig 또는 규칙 집합 파일을 사용 하 여 미리 정의 된 규칙을 사용 하 여 분석기를 구성 하는 방법에 대해 알아보려면 [규칙 범주 사용](../code-quality/analyzer-rule-sets.md)을 참조 하세요.