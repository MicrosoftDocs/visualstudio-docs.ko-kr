---
title: 타사 분석기 설치
ms.date: 08/27/2020
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 9da78f4c8e76f4e5b79f4cbdb0739d34fc465330
ms.sourcegitcommit: 016bcdc7cd3e3619457beb321800e98544efb6c9
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/29/2020
ms.locfileid: "89091453"
---
# <a name="install-third-party-analyzers"></a>타사 분석기 설치

Visual Studio에는 핵심*Roslyn*(.NET Compiler Platform) 분석기가 포함 되어 있습니다. 이러한 분석기는 항상 켜져 있습니다. NuGet 패키지로 추가 분석기를 설치 하거나 *VSIX* 파일에 Visual Studio 확장으로 설치할 수 있습니다.

## <a name="to-install-nuget-analyzer-packages"></a>NuGet 분석기 패키지를 설치 하려면

1. Www.nuget.org에 설치 하려는 분석기 패키지를 찾습니다.

   예를 들어 [StyleCop](https://www.nuget.org/packages/stylecop.analyzers/) 를 설치 하 여 코드 베이스에서 스타일 문제를 찾을 수 있습니다.

2. 패키지 [관리자 콘솔](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console) 또는 [패키지 관리자 UI](/nuget/quickstart/install-and-use-a-package-in-visual-studio#package-manager-console)를 사용 하 여 Visual Studio에서 패키지를 설치 합니다.

   > [!NOTE]
   > 각 분석기 패키지의 www.nuget.org 페이지에는 **패키지 관리자 콘솔**에 붙여 넣을 수 있는 명령이 표시 됩니다. 텍스트를 클립보드에 복사 하는 편리한 단추도 있습니다.

   분석기 어셈블리는 설치 되 고 **참조**분석기 아래 **솔루션 탐색기** 에 표시 됩니다  >  **Analyzers**.

## <a name="to-install-vsix-analyzers"></a>VSIX 분석기를 설치 하려면

::: moniker range="vs-2017"

1. Visual Studio에서 **도구** > **확장 및 업데이트**를 선택 합니다.

   **확장명 및 업데이트** 대화 상자가 열립니다.

   > [!NOTE]
   > 또는 [Visual Studio Marketplace](https://marketplace.visualstudio.com)에서 직접 분석기 확장을 찾아서 다운로드할 수 있습니다.

::: moniker-end

::: moniker range=">=vs-2019"

1. Visual Studio에서 **확장** > **확장 관리**를 선택 합니다.

   **확장 관리** 대화 상자가 열립니다.

   > [!NOTE]
   > 또는 [Visual Studio Marketplace](https://marketplace.visualstudio.com)에서 직접 분석기 확장을 찾아서 다운로드할 수 있습니다.

::: moniker-end

2. 왼쪽 창에서 **온라인** 을 확장 한 다음 **Visual Studio Marketplace**를 선택 합니다.

3. 검색 상자에 설치 하려는 분석기 확장의 이름을 입력 합니다. 예를 들어 [Microsoft FxCop 분석기를 설치](install-fxcop-analyzers.md#vsix) 하 여 코드에서 보안 및 성능 문제를 확인 하는 것이 좋습니다.

4. **다운로드**를 선택합니다.

   확장이 다운로드 됩니다.

5. **확인** 을 선택 하 여 대화 상자를 닫은 다음 Visual Studio의 모든 인스턴스를 닫아 **VSIX 설치 관리자**를 시작 합니다.

   **VSIX 설치 관리자** 대화 상자가 열립니다.

   ![Microsoft Code 분석용 VSIX 설치 관리자](media/vsix-installer-code-analysis.png)

6. **수정을** 선택 하 여 설치를 시작 합니다.

7. 1 ~ 2 분 후 설치가 완료 됩니다. **닫기**를 선택합니다.

8. Visual Studio를 다시 엽니다.

::: moniker range="vs-2017"

확장이 설치 되어 있는지 여부를 확인 하려면 **도구**  >  **확장 및 업데이트**를 선택 합니다. **확장 및 업데이트** 대화 상자에서 왼쪽에 있는 **설치** 된 범주를 선택 하 고 이름으로 확장을 검색 합니다.

::: moniker-end

::: moniker range=">=vs-2019"

확장이 설치 되어 있는지 여부를 확인 **하려면 확장 확장**  >  **관리**를 선택 합니다. **확장 관리** 대화 상자에서 왼쪽에 있는 **설치** 된 범주를 선택 하 고 이름으로 확장을 검색 합니다.

::: moniker-end

## <a name="next-steps"></a>다음 단계

> [!div class="nextstepaction"]
> [Visual Studio에서 코드 분석기 사용](../code-quality/use-roslyn-analyzers.md)

## <a name="see-also"></a>참고 항목

- [Visual Studio의 코드 분석기 개요](../code-quality/roslyn-analyzers-overview.md)
- [FxCop 분석기 설치](../code-quality/install-fxcop-analyzers.md)
