---
title: 코드 분석 해제
ms.date: 10/03/2019
ms.topic: how-to
helpviewer_keywords:
- code analysis, disable
- disable code analysis
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d2cac7ad0502d82309aa664b8e8fe6bdd0301815
ms.sourcegitcommit: a801ca3269274ce1de4f6b2c3f40b58bbaa3f460
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88800700"
---
# <a name="how-to-disable-source-code-analysis-for-managed-code"></a>관리 코드에 대 한 소스 코드 분석을 사용 하지 않도록 설정 하는 방법

::: moniker range=">=vs-2019"

이 페이지는 Visual Studio에서 코드 분석을 사용 하지 않도록 설정 하는 데 도움이 됩니다. 비활성화할 수 있는 항목에 대 한 제한 사항이 있으며, 코드 분석을 해제 하는 절차는 다음과 같은 몇 가지 요인에 따라 다릅니다.

- 프로젝트 형식 (.NET Core/Standard 대 .NET Framework)

  .NET Core 및 .NET Standard 프로젝트에는 NuGet 패키지로 설치 된 분석기에서 코드 분석을 해제할 수 있는 코드 분석 속성 페이지에 대 한 옵션이 있습니다. 자세한 내용은 [.Net Core 및 .NET Standard 프로젝트](#net-core-and-net-standard-projects)를 참조 하세요. .NET Framework 프로젝트에 대 한 소스 코드 분석을 해제 하려면 [.NET Framework 프로젝트](#net-framework-projects)를 참조 하세요.

- 원본 분석 및 레거시 분석

  이 항목은 레거시 (이진) 분석에는 적용 되지 않고 소스 코드 분석에 적용 됩니다. 레거시 분석을 사용 하지 않도록 설정 하 [는 방법은 방법: 레거시 코드 분석 사용 및 사용 안 함](how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)을 참조 하세요.

## <a name="net-core-and-net-standard-projects"></a>.NET Core 및 .NET Standard 프로젝트

Visual Studio 2019 버전 16.3부터 코드 분석 속성 페이지에서 사용할 수 있는 두 가지 확인란을 사용할 수 있습니다 .이를 통해 코드 분석 속성 페이지에서 분석기가 빌드 시간 및 디자인 타임에 실행 되는지 여부를 제어할 수 있습니다. 이러한 옵션은 프로젝트별로 지정 됩니다.

![Visual Studio에서 라이브 코드 분석 또는 빌드에 대 한 사용 또는 사용 안 함](media/run-on-build-run-live-analysis.png)

이 페이지를 열려면 **솔루션 탐색기** 에서 프로젝트 노드를 마우스 오른쪽 단추로 클릭 하 고 **속성**을 선택 합니다. **코드 분석** 탭을 선택 합니다.

- 빌드 시 소스 분석을 사용 하지 않도록 설정 하려면 **빌드 시 실행** 옵션을 선택 취소 합니다.
- 라이브 소스 분석을 사용 하지 않도록 설정 하려면 **라이브 분석에서 실행** 옵션을 선택 취소 합니다.

> [!NOTE]
> Visual Studio 2019 버전 16.5부터 주문형 코드 분석 실행 워크플로를 선호 하는 경우 라이브 분석 및/또는 빌드 중에 분석기 실행을 사용 하지 않도록 설정 하 고 요청 시 프로젝트 또는 솔루션에서 코드 분석을 수동으로 트리거할 수 있습니다. 수동으로 코드 분석을 실행 하는 방법에 대 한 자세한 내용은 [방법: 관리 코드에 대해 수동으로 코드 분석 실행](how-to-run-code-analysis-manually-for-managed-code.md)을 참조 하세요.

## <a name="net-framework-projects"></a>.NET Framework 프로젝트

분석기에 대 한 소스 코드 분석을 해제 하려면 다음 MSBuild 속성 중 하나 이상을 [프로젝트 파일](../ide/solutions-and-projects-in-visual-studio.md#project-file)에 추가 합니다.

| MSBuild 속성 | 설명 | 기본값 |
| - | - | - |
| `RunAnalyzersDuringBuild` | 빌드 시 분석기가 실행 되는지 여부를 제어 합니다. | `true` |
| `RunAnalyzersDuringLiveAnalysis` | 분석기가 디자인 타임에 코드를 실시간으로 분석할 지 여부를 제어 합니다. | `true` |
| `RunAnalyzers` | 빌드 및 디자인 타임에 분석기를 사용 하지 않도록 설정 합니다. 이 속성은 및 보다 우선적으로 적용 `RunAnalyzersDuringBuild` `RunAnalyzersDuringLiveAnalysis` 됩니다. | `true` |

예제:

```xml
<RunAnalyzersDuringBuild>false</RunAnalyzersDuringBuild>
<RunAnalyzersDuringLiveAnalysis>false</RunAnalyzersDuringLiveAnalysis>
<RunAnalyzers>false</RunAnalyzers>
```

::: moniker-end

::: moniker range="vs-2017"

## <a name="source-analysis"></a>소스 분석

Visual Studio 2017에서 [소스 분석](roslyn-analyzers-overview.md) 을 해제할 수 없습니다. **오류 목록**에서 분석기 오류를 지우려면 **Analyze**  >  메뉴 모음에서 분석**실행 코드 분석 및 활성 문제 표시 안 함** 을 선택 하 여 현재 위반을 모두 표시 하지 않을 수 있습니다. 자세한 내용은 [위반 표시 안 함](use-roslyn-analyzers.md#suppress-violations)을 참조 하세요.

Visual Studio 2019 버전 16.3부터 소스 코드 분석을 해제 하거나 요청 시 실행할 수 있습니다. Visual Studio 2019로 업그레이드 하는 것이 좋습니다.

## <a name="legacy-analysis"></a>레거시 분석

**코드 분석** 속성 페이지에서 레거시, 빌드 시간 분석을 사용 하지 않도록 설정할 수 있습니다. 자세한 내용은 [방법: 레거시 코드 분석 사용 및 사용 안 함](how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)을 참조 하세요.

::: moniker-end

## <a name="see-also"></a>참고 항목

- [위반 표시 안 함](use-roslyn-analyzers.md#suppress-violations)
- [방법: 레거시 코드 분석 사용 및 사용 안 함](how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)
