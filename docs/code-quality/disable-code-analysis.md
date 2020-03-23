---
title: 코드 분석 끄기
ms.date: 10/03/2019
ms.topic: conceptual
helpviewer_keywords:
- code analysis, disable
- disable code analysis
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8db6ad7bed4b1526d87112f33d3586728728d7f5
ms.sourcegitcommit: 92361aac3665a934faa081e1d1ea89a067b01c5b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79431399"
---
# <a name="how-to-disable-source-code-analysis-for-managed-code"></a>관리 코드에 대 한 소스 코드 분석을 사용 하지 않도록 설정 하는 방법

::: moniker range=">=vs-2019"

이 페이지에서는 Visual Studio에서 코드 분석을 사용하지 않도록 설정하는 데 도움이 됩니다. 비활성화할 수 있는 항목에는 제한이 있으며 코드 분석을 해제하는 절차는 몇 가지 요인에 따라 다릅니다.

- 프로젝트 유형(.NET 코어/표준 대 .NET 프레임워크)

  .NET Core 및 .NET 표준 프로젝트에는 NuGet 패키지로 설치된 분석기에서 코드 분석을 끌 수 있는 코드 분석 속성 페이지에 옵션이 있습니다. 자세한 내용은 [.NET 코어 및 .NET 표준 프로젝트를](#net-core-and-net-standard-projects)참조하십시오. .NET Framework 프로젝트에 대한 소스 코드 분석을 해제하려면 [.NET Framework 프로젝트를](#net-framework-projects)참조하십시오.

- 소스 분석 과 레거시 분석

  이 항목은 레거시(바이너리) 분석이 아닌 소스 코드 분석에 적용됩니다. 레거시 분석 사용 중지에 대한 자세한 내용은 [사용 및 사용 설정 및 레거시 코드 분석을 사용하지 않도록 설정하는 방법을](how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)참조하십시오.

## <a name="net-core-and-net-standard-projects"></a>.NET 코어 및 .NET 표준 프로젝트

Visual Studio 2019 버전 16.3부터 코드 분석 속성 페이지에는 분석기의 빌드 시간 및 설계 시간에 실행 여부를 제어할 수 있는 두 개의 확인란이 있습니다. 이러한 옵션은 프로젝트별 옵션입니다.

![Visual Studio에서 라이브 코드 분석 또는 빌드 시 사용 또는 비활성화](media/run-on-build-run-live-analysis.png)

이 페이지를 열려면 **솔루션 탐색기에서** 프로젝트 노드를 마우스 오른쪽 단추로 클릭하고 **속성을**선택합니다. 코드 **분석** 탭을 선택합니다.

- 빌드 시 소스 분석을 사용하지 않으려면 **빌드 시 실행** 옵션을 선택 취소합니다.
- 라이브 소스 분석을 사용하지 않으려면 라이브 분석에서 실행 옵션을 선택 **취소합니다.**

> [!NOTE]
> Visual Studio 2019 버전 16.5부터 온디맨드 코드 분석 실행 워크플로우를 선호하는 경우 라이브 분석 중에 분석기 실행을 비활성화하거나 프로젝트 또는 주문형 솔루션에 대해 코드 분석을 한 번 빌드하고 수동으로 트리거할 수 있습니다. 코드 분석을 수동으로 실행하는 방법에 대한 자세한 내용은 [관리 코드에 대해 코드 분석을 수동으로 실행하는 방법을](how-to-run-code-analysis-manually-for-managed-code.md)참조하십시오.  

## <a name="net-framework-projects"></a>.NET 프레임워크 프로젝트

분석기의 소스 코드 분석을 끄려면 다음 MSBuild 속성 중 하나 이상을 [프로젝트 파일에](../ide/solutions-and-projects-in-visual-studio.md#project-file)추가합니다.

| MSBuild 속성 | Description | 기본값 |
| - | - | - |
| `RunAnalyzersDuringBuild` | 분석기빌드 시 실행 여부를 제어합니다. | `true` |
| `RunAnalyzersDuringLiveAnalysis` | 분석기는 설계 시점에 실시간으로 코드를 분석할지 여부를 제어합니다. | `true` |
| `RunAnalyzers` | 빌드 및 디자인 시간 모두에서 분석기를 사용하지 않도록 설정합니다. 이 속성은 우선 `RunAnalyzersDuringBuild` `RunAnalyzersDuringLiveAnalysis`순위를 차지합니다. | `true` |

예제:

```xml
<RunAnalyzersDuringBuild>false</RunAnalyzersDuringBuild>
<RunAnalyzersDuringLiveAnalysis>false</RunAnalyzersDuringLiveAnalysis>
<RunAnalyzers>false</RunAnalyzers>
```

::: moniker-end

::: moniker range="vs-2017"

## <a name="source-analysis"></a>소스 분석

Visual Studio 2017에서는 [소스 분석을](roslyn-analyzers-overview.md) 끌 수 없습니다. 오류 목록에서 분석기 오류를 지우려면 메뉴 모음에서 실행 코드 분석 **분석** > **및 활성 문제 억제를** 선택하여 현재 모든 위반을 억제할 수 있습니다. 자세한 내용은 [위반 억제](use-roslyn-analyzers.md#suppress-violations)를 참조하십시오.

Visual Studio 2019 버전 16.3부터 소스 코드 분석을 끄거나 필요에 따라 실행할 수 있습니다. 비주얼 스튜디오 2019로 업그레이드하는 것이 좋습니다.

## <a name="legacy-analysis"></a>레거시 분석

**코드 분석** 속성 페이지에서 레거시 빌드 시간 분석을 사용하지 않도록 설정할 수 있습니다. 자세한 내용은 [레거시 코드 분석을 활성화 및 사용하지 않도록 설정하는 방법을](how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)참조하십시오.

::: moniker-end

## <a name="see-also"></a>참고 항목

- [위반 억제](use-roslyn-analyzers.md#suppress-violations)
- [방법: 레거시 코드 분석 사용 및 비활성화](how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)
