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
ms.openlocfilehash: 1d734ea4d87dc5d1b8f2ca7f1a1891a4cf7d512b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79508773"
---
# <a name="install-fxcop-analyzers-in-visual-studio"></a>비주얼 스튜디오에 FxCop 분석기 설치

Microsoft는 레거시 분석에서 가장 중요한 "FxCop" 규칙을 포함하는 [Microsoft.CodeAnalysis.FxCopAnalysisers라는](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers)분석기 집합을 만들었습니다. 이러한 분석기는 코드에서 보안, 성능 및 디자인 문제를 검사합니다.

이러한 FxCop 분석기를 NuGet 패키지또는 Visual Studio에 대한 VSIX 확장으로 설치할 수 있습니다. 각각의 장단점에 대해 자세히 알아보려면 [NuGet 패키지 및 VSIX 확장을 참조하십시오.](roslyn-analyzers-overview.md#nuget-package-versus-vsix-extension)

## <a name="nuget-package"></a>NuGet 패키지

::: moniker range=">=vs-2019"

Visual Studio 2019 버전 16.3 이상에서는 프로젝트의 코드 분석 속성 페이지에서 직접 [Microsoft.CodeAnalysis.FxCopAnalysisers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) NuGet 패키지를 설치할 수 있습니다.

1. **솔루션 탐색기에서**프로젝트 노드를 마우스 오른쪽 단추로 클릭하고 **속성을**선택한 다음 **코드 분석** 탭을 선택합니다.

   ![비주얼 스튜디오의 속성 페이지에서 FxCop 분석기 패키지 설치](media/install-fxcop-properties-page.png)

2. **설치**을 선택합니다.

   비주얼 스튜디오는 Microsoft.CodeAnalysis.FxCop분석기 패키지의 최신 버전을 설치합니다. 어셈블리는 **참조** > **분석기**아래의 **솔루션 탐색기에** 나타납니다.

   ![솔루션 탐색기의 분석기 노드](media/solution-explorer-analyzers-node.png)

이전 버전의 Visual Studio 2019를 사용하는 경우 [패키지 관리자 콘솔](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console) 또는 [패키지 관리자 UI를](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console)사용하여 패키지를 설치합니다.

::: moniker-end

::: moniker range="vs-2017"

1. Visual Studio 버전에 따라 설치할 [분석기 패키지](#fxcopanalyzers-package-versions) 버전을 결정합니다.

2. [패키지 관리자 콘솔](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console) 또는 패키지 [관리자 UI를](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console)사용하여 Visual Studio에 패키지를 설치합니다.

   > [!NOTE]
   > 각 분석기 패키지의 nuget.org 페이지에는 패키지 관리자 **콘솔에**붙여넣을 수 있는 명령이 표시됩니다. 클립 보드에 텍스트를 복사 하는 편리한 버튼도 있다.
   >
   > ![패키지 관리자 콘솔 명령을 보여주는 NuGet.org 페이지](media/nuget-package-manager-command.png)

   분석기 어셈블리가 설치되고 **참조** > **분석기**아래의 **솔루션 탐색기에** 나타납니다.

::: moniker-end

### <a name="custom-installation"></a>사용자 지정 설치

사용자 지정 설치의 경우 예를 들어 다른 버전의 패키지를 지정하려면 프로젝트의 코드 분석 속성 페이지에서 타원(...) 단추를 선택합니다. 이 단추는 검색 문자열로 "Microsoft.CodeAnalysis.FxCopAnalysisers"를 사용하여 NuGet 패키지 관리자를 엽니다.

![비주얼 스튜디오의 속성 페이지에서 사용자 지정 FxCop 분석기 패키지 설치](media/install-fxcop-properties-page-ellipsis.png)

> [!TIP]
> Visual Studio 버전에 따라 설치할 [분석기 패키지](#fxcopanalyzers-package-versions) 버전을 결정합니다. [패키지 관리자 UI에서](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console)패키지를 설치할 수도 있습니다.

### <a name="fxcopanalyzers-package-versions"></a>FxCop분석기 패키지 버전

다음 지침을 사용하여 Visual Studio 버전에 설치할 FxCop 분석기 패키지 버전을 결정합니다.

| Visual Studio 버전 | FxCop 분석기 패키지 버전 |
| - | - |
| 비주얼 스튜디오 2019 (모든 버전)<br />비주얼 스튜디오 2017 버전 15.8 이상 | [최신](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) |
| 비주얼 스튜디오 2017 버전 15.5 받는 것 15.7 | [2.6.3](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.6.3) |
| 비주얼 스튜디오 2017 버전 15.3 받는 것 15.4 | [2.3.0-베타1](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.3.0-beta1) |
| 비주얼 스튜디오 2017 버전 15.0 ~ 15.2 | [2.0.0-베타2](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/2.0.0-beta2) |
| 비주얼 스튜디오 2015 업데이트 2 및 3 | [1.2.0-베타2](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.2.0-beta2) |
| Visual Studio 2015 업데이트 1 | [1.1.0](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.1.0) |
| Visual Studio 2015 RTW | [1.0.1](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/1.0.1) |

## <a name="vsix"></a>VSIX

::: moniker range="vs-2017"

Visual Studio 2017 버전 15.5 이상에서는 관리되는 프로젝트에 대한 모든 FxCop 분석기를 포함하는 [Microsoft 코드 분석 2017](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017) 확장을 설치할 수 있습니다.

1. 비주얼 스튜디오에서 **도구** > **확장 및 업데이트를 선택합니다.**

   **확장명 및 업데이트** 대화 상자가 열립니다.

   > [!NOTE]
   > 또는 [Visual Studio 마켓플레이스에서](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017)직접 확장을 다운로드합니다.

2. 왼쪽 창에서 **온라인으로** 확장한 다음 **Visual Studio 마켓플레이스를**선택합니다.

3. 검색 상자에서 "코드 분석"을 입력하고 **Microsoft 코드 분석 2017** 확장을 찾습니다.

   ![마이크로소프트 코드 분석 2017 확장](media/extensions-and-updates-code-analysis.png)

::: moniker-end

::: moniker range=">=vs-2019"

[Microsoft 코드 분석 2019](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2019) 확장에는 관리되는 프로젝트에 대한 모든 FxCop 분석기가 포함되어 있습니다. 이 확장을 설치하려면 다음을 수행하십시오.

1. 시각적 스튜디오에서 **확장** > **관리 확장을 선택합니다.**

   확장 관리 대화 **상자가** 열립니다.

   > [!NOTE]
   > 또는 [Visual Studio 마켓플레이스에서](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2019)직접 확장을 다운로드합니다.

2. 왼쪽 창에서 **온라인으로** 확장한 다음 **Visual Studio 마켓플레이스를**선택합니다.

3. 검색 상자에서 "코드 분석"을 입력하고 **Microsoft 코드 분석 2019** 확장을 찾습니다.

   ![마이크로소프트 코드 분석 2019 확장](media/manage-extensions-code-analysis.png)

::: moniker-end

4. **다운로드**를 선택합니다.

   확장 프로그램이 다운로드됩니다.

5. **확인을** 선택하여 대화 상자를 닫은 다음 Visual Studio의 모든 인스턴스를 닫아 **VSIX 설치 프로그램을**시작합니다.

   **VSIX 설치 프로그램** 대화 상자가 열립니다.

   ::: moniker range="vs-2017"

   ![마이크로소프트 코드 분석을 위한 VSIX 설치 프로그램](media/vsix-installer-code-analysis.png)

   ::: moniker-end

6. 설치를 시작하려면 **수정을** 선택합니다.

   1~2분 후에 설치가 완료됩니다.

7. **닫기**를 선택한 다음 시각적 스튜디오를 다시 엽니다.

::: moniker range="vs-2017"

확장이 설치되어 있는지 확인하려면 **도구** > **확장 및 업데이트를 선택합니다.** 확장 및 업데이트 대화 상자에서 왼쪽에 **설치된** 범주를 선택한 다음 이름으로 확장을 **검색합니다.**

::: moniker-end

::: moniker range=">=vs-2019"

확장이 설치되어 있는지 확인하려면 **확장** > **관리 를 선택합니다.** 확장 관리 대화 상자에서 왼쪽에 **설치된** 범주를 선택한 다음 이름으로 확장을 **검색합니다.**

::: moniker-end

## <a name="see-also"></a>참고 항목

- [비주얼 스튜디오의 코드 분석기 개요](../code-quality/roslyn-analyzers-overview.md)
- [Visual Studio에서 코드 분석기 사용](../code-quality/use-roslyn-analyzers.md)
- [레거시 분석기에서 코드 분석기로 마이그레이션](../code-quality/migrate-from-legacy-analysis-to-fxcop-analyzers.md)
