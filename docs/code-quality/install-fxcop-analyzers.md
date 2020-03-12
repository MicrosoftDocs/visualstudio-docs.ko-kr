---
title: FxCop 분석기 설치
ms.date: 08/03/2018
ms.topic: conceptual
helpviewer_keywords:
- fxcop analyzers
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 78935673dbf57f75988d4c0a9e862b11e2fe855f
ms.sourcegitcommit: 514f0f7d1a61d292c7dbc80ec73a36bda960d6ce
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/09/2020
ms.locfileid: "78937524"
---
# <a name="install-fxcop-analyzers-in-visual-studio"></a>Visual Studio에서 FxCop 분석기 설치

Microsoft는 레거시 분석에서 가장 중요 한 "FxCop" 규칙을 포함 하는 [FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers)라는 분석기 집합을 만들었습니다. 이러한 분석기는 코드에서 보안, 성능 및 디자인 문제를 확인 합니다.

이러한 FxCop 분석기를 NuGet 패키지 또는 Visual Studio에 대 한 VSIX 확장으로 설치할 수 있습니다. 각의 장단점에 대 한 자세한 내용은 [NuGet 패키지 및 VSIX 확장명](roslyn-analyzers-overview.md#nuget-package-versus-vsix-extension)을 참조 하세요.

## <a name="nuget-package"></a>NuGet 패키지

::: moniker range=">=vs-2019"

Visual Studio 2019 버전 16.3 이상에서는 프로젝트의 코드 분석 속성 페이지에서 [FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) NuGet 패키지를 직접 설치할 수 있습니다.

1. **솔루션 탐색기**에서 프로젝트 노드를 마우스 오른쪽 단추로 클릭 하 고 **속성**을 선택한 다음 **코드 분석** 탭을 선택 합니다.

   ![Visual Studio의 속성 페이지에서 FxCop 분석기 패키지 설치](media/install-fxcop-properties-page.png)

2. **설치**를 선택합니다.

   Visual Studio는 최신 버전의 FxCopAnalyzers 패키지를 설치 합니다. 어셈블리는 **솔루션 탐색기** > **분석기**의 **참조** 아래에 나타납니다.

   ![솔루션 탐색기의 분석기 노드](media/solution-explorer-analyzers-node.png)

이전 버전의 Visual Studio 2019을 사용 하는 경우 패키지 [관리자 콘솔](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console) 또는 [패키지 관리자 UI](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console)를 사용 하 여 패키지를 설치 합니다.

::: moniker-end

::: moniker range="vs-2017"

1. 사용자의 Visual Studio 버전에 따라 설치할 [분석기 패키지 버전을 결정](#fxcopanalyzers-package-versions) 합니다.

2. 패키지 [관리자 콘솔](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console) 또는 [패키지 관리자 UI](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console)를 사용 하 여 Visual Studio에서 패키지를 설치 합니다.

   > [!NOTE]
   > 각 분석기 패키지의 nuget.org 페이지에는 **패키지 관리자 콘솔**에 붙여 넣을 수 있는 명령이 표시 됩니다. 텍스트를 클립보드에 복사 하는 편리한 단추도 있습니다.
   >
   > ![패키지 관리자 콘솔 명령을 표시 하는 NuGet.org 페이지](media/nuget-package-manager-command.png)

   분석기 어셈블리는 설치 되 고 > 분석기의 **참조** 아래 **솔루션 탐색기** 에 표시 **됩니다.**

::: moniker-end

### <a name="custom-installation"></a>사용자 지정 설치

사용자 지정 설치의 경우와 같이 다른 버전의 패키지를 지정 하려면 프로젝트의 코드 분석 속성 페이지에서 줄임표 (...) 단추를 선택 합니다. 이 단추를 클릭 하면 "FxCopAnalyzers"를 검색 문자열로 사용 하 여 NuGet 패키지 관리자가 열립니다.

![Visual Studio의 속성 페이지에서 사용자 지정 FxCop 분석기 패키지 설치](media/install-fxcop-properties-page-ellipsis.png)

> [!TIP]
> 사용자의 Visual Studio 버전에 따라 설치할 [분석기 패키지 버전](#fxcopanalyzers-package-versions) 을 결정 합니다. 패키지 [관리자 UI](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console)에서 패키지를 설치할 수도 있습니다.

### <a name="fxcopanalyzers-package-versions"></a>FxCopAnalyzers 패키지 버전

다음 지침에 따라 사용 중인 Visual Studio 버전에 대해 설치할 FxCop 분석기 패키지의 버전을 확인 합니다.

| Visual Studio 버전 | FxCop analyzer 패키지 버전 |
| - | - |
| Visual Studio 2019 (모든 버전)<br />Visual Studio 2017 버전 15.8 이상 | [마지막](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) |
| Visual Studio 2017 버전 15.5에서 15.7로 | [2.6.3](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.6.3) |
| Visual Studio 2017 버전 15.3에서 15.4로 | [2.3.0-beta1](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.3.0-beta1) |
| Visual Studio 2017 버전 15.0에서 15.2로 | [2.0.0-beta2](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.0.0-beta2) |
| Visual Studio 2015 업데이트 2 및 3 | [1.2.0-beta2](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.2.0-beta2) |
| Visual Studio 2015 업데이트 1 | [1.1.0](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.1.0) |
| Visual Studio 2015 RTW | [1.0.1](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.0.1) |

## <a name="vsix"></a>VSIX

::: moniker range="vs-2017"

Visual Studio 2017 버전 15.5 이상에서는 관리 되는 프로젝트에 대 한 모든 FxCop 분석기를 포함 하는 [Microsoft 코드 분석 2017](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017) 확장을 설치할 수 있습니다.

1. Visual Studio에서 **도구** > **확장 및 업데이트**를 선택 합니다.

   **확장명 및 업데이트** 대화 상자가 열립니다.

   > [!NOTE]
   > 또는 [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017)에서 직접 확장을 다운로드 합니다.

2. 왼쪽 창에서 **온라인** 을 확장 한 다음 **Visual Studio Marketplace**를 선택 합니다.

3. 검색 상자에 "코드 분석"을 입력 하 고 **Microsoft 코드 분석 2017** 확장을 찾습니다.

   ![Microsoft 코드 분석 2017 확장](media/extensions-and-updates-code-analysis.png)

::: moniker-end

::: moniker range=">=vs-2019"

[Microsoft 코드 분석 2019](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2019) 확장에는 관리 되는 프로젝트에 대 한 모든 FxCop 분석기가 포함 되어 있습니다. 이 확장을 설치 하려면:

1. Visual Studio에서 **확장 > 확장** **관리**를 선택 합니다.

   **확장 관리** 대화 상자가 열립니다.

   > [!NOTE]
   > 또는 [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2019)에서 직접 확장을 다운로드 합니다.

2. 왼쪽 창에서 **온라인** 을 확장 한 다음 **Visual Studio Marketplace**를 선택 합니다.

3. 검색 상자에 "코드 분석"을 입력 하 고 **Microsoft 코드 분석 2019** 확장을 찾습니다.

   ![Microsoft 코드 분석 2019 확장](media/manage-extensions-code-analysis.png)

::: moniker-end

4. **다운로드**를 선택합니다.

   확장이 다운로드 됩니다.

5. **확인** 을 선택 하 여 대화 상자를 닫은 다음 Visual Studio의 모든 인스턴스를 닫아 **VSIX 설치 관리자**를 시작 합니다.

   **VSIX 설치 관리자** 대화 상자가 열립니다.

   ::: moniker range="vs-2017"

   ![Microsoft Code 분석용 VSIX 설치 관리자](media/vsix-installer-code-analysis.png)

   ::: moniker-end

6. **수정을** 선택 하 여 설치를 시작 합니다.

   1 ~ 2 분 후 설치가 완료 됩니다.

7. **닫기**를 선택 하 고 Visual Studio를 다시 엽니다.

::: moniker range="vs-2017"

확장이 설치 되어 있는지 확인 하려면 **도구** > **확장 및 업데이트**를 선택 합니다. **확장 및 업데이트** 대화 상자에서 왼쪽에 있는 **설치** 된 범주를 선택 하 고 이름으로 확장을 검색 합니다.

::: moniker-end

::: moniker range=">=vs-2019"

확장이 설치 되어 있는지 확인 하려면 **확장 > 확장** 을 선택 **합니다.** **확장 관리** 대화 상자에서 왼쪽에 있는 **설치** 된 범주를 선택 하 고 이름으로 확장을 검색 합니다.

::: moniker-end

## <a name="see-also"></a>참고 항목

- [Visual Studio의 코드 분석기 개요](../code-quality/roslyn-analyzers-overview.md)
- [Visual Studio에서 코드 분석기 사용](../code-quality/use-roslyn-analyzers.md)
- [레거시 분석에서 코드 분석기로 마이그레이션](../code-quality/migrate-from-legacy-analysis-to-fxcop-analyzers.md)
