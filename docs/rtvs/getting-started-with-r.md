---
title: R 시작 자습서
description: 프로젝트 만들기, 대화형 창, 코드 편집 및 디버깅을 포함하여 Visual Studio에서 R을 사용하는 연습입니다.
ms.date: 06/29/2017
ms.topic: tutorial
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: be0ba7b32af5247bb0dccccb68d900cb6797cc13
ms.sourcegitcommit: a801ca3269274ce1de4f6b2c3f40b58bbaa3f460
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88801180"
---
# <a name="get-started-with-r-tools-for-visual-studio"></a>Visual Studio용 R 도구 시작

RTVS(Visual Studio용 R 도구)를 설치한 후([설치](installing-r-tools-for-visual-studio.md) 참조) 해당 도구가 제공하는 환경을 빠르게 경험할 수 있습니다.

## <a name="create-an-r-project"></a>R 프로젝트 만들기

1. Visual Studio를 엽니다.
1. **파일** > **새로 만들기** > **프로젝트**(**Ctrl**+**Shift**+**N**) 선택
1. **템플릿** > **R** 아래에서 “R 프로젝트”를 선택하고, 프로젝트의 이름과 위치를 입력한 후 **확인**을 선택합니다.

   ![Visual Studio의 R(VS2017의 RTVS)에 대한 새 프로젝트 대화 상자](media/getting-started-01-new-project.png)

1. 프로젝트가 생성되면 다음 창이 표시됩니다.

    - 오른쪽에 있는 Visual Studio 솔루션 탐색기에서는 포함 *솔루션* 내에서 프로젝트를 확인할 수 있습니다. 솔루션에는 다양한 형식의 프로젝트가 개수 제한 없이 포함될 수 있습니다. 자세한 내용은 [프로젝트](r-projects-in-visual-studio.md)를 참조하세요.
    - 왼쪽 위에 있는 새 R 파일(`script.R`)에서는 모든 Visual Studio 편집 기능을 사용하여 소스 코드를 편집할 수 있습니다.
    - 왼쪽 아래에 있는 **R 대화형** 창에서는 대화형으로 코드를 개발 및 테스트할 수 있습니다.

> [!Note]
> 프로젝트를 열 필요 없이 다른 프로젝트 형식이 로드된 경우에도 **R 대화형** 창을 사용할 수 있습니다. 언제든지 **R 도구** > **창** > **R 대화형**을 선택하면 됩니다.

## <a name="explore-the-interactive-window-and-intellisense"></a>대화형 창 및 IntelliSense 살펴보기

1. `3 + 4`를 입력하여 대화형 창이 작동하는지 테스트한 다음, **Enter**를 눌러 결과를 확인합니다.

    ![Visual Studio 2017(VS2017)의 R 대화형 창](media/getting-started-02-interactive1.png)

1. 약간 더 복잡한 `ds <- c(1.5, 6.7, 8.9) * 1:12`를 입력하고 `ds`를 입력하여 결과를 확인합니다.

    ![Visual Studio의 R에 대한 추가 대화형 예제](media/getting-started-03-interactive2.png)

1. `mean(ds)`을 입력하지만 `m` 또는 `me`를 입력하자마자 Visual Studio IntelliSense에서 자동 완성 옵션을 제공합니다. 목록에서 원하는 완성이 선택되면 **Tab**을 눌러 완성을 삽입합니다. 화살표 키 또는 마우스를 사용하여 선택을 변경할 수 있습니다.

    ![코드를 입력할 때 나타나는 IntelliSense](media/getting-started-04-intellisense1.png)

1. `mean`을 완성한 후 여는 괄호(`(`)를 입력하고 IntelliSense가 함수에 대한 인라인 도움말을 제공하는 방식을 확인합니다.

    ![함수에 대한 도움말을 표시하는 IntelliSense](media/getting-started-05-intellisense2.png)

1. `mean(ds)` 줄을 완성하고 Enter 키를 눌러 결과(`[1] 39.51667`)를 확인합니다.

1. 대화형 창은 도움말과 통합되어 있으므로, `?mean`을 입력하면 Visual Studio의 **R 도움말** 창에 해당 함수에 대한 도움말이 표시됩니다. 자세한 내용은 [Visual Studio용 R 도구의 도움말](getting-started-help.md)을 참조하세요.

    ![Visual Studio의 R 도움말 창](media/getting-started-06-help.png)

1. `plot(1:100)` 등의 일부 명령은 대화형 창에 직접 출력을 표시할 수 없는 경우 Visual Studio에서 새 창을 엽니다.

    ![Visual Studio의 플롯 표시](media/getting-started-07-plot-window.png)

대화형 창에서는 기록을 검토하고, 작업 영역을 로드 및 저장하고, 디버거에 연결하고, 복사-붙여넣기를 사용하는 대신 소스 코드 파일을 조작할 수도 있습니다. 자세한 내용은 [R 대화형 창 사용](interactive-repl-for-r-in-visual-studio.md)을 참조하세요.

## <a name="experience-code-editing-features"></a>코드 기능 편집 경험

대화형 창에서 잠시 작업하면 코드 편집기에서도 작동하는 IntelliSense 등의 기본 편집 기능을 확인할 수 있습니다. 이전과 같은 코드를 입력하면 동일한 자동 완성 및 IntelliSense 프롬프트가 표시되지만 출력은 표시되지 않습니다.

*.R* 파일에 코드를 작성하면 모든 코드를 한 번에 확인할 수 있고, 사소한 변경을 수행한 다음, 대화형 창에서 코드를 실행하여 결과를 빠르게 확인하기가 더 쉽습니다. 프로젝트에 원하는 개수만큼 파일을 포함할 수도 있습니다. 코드가 파일에 있으면 디버거에서 코드를 단계별로 실행할 수도 있습니다(이 문서의 뒷부분에서 설명). 이러한 기능은 계산 알고리즘을 개발하고 코드를 작성하여 하나 이상의 데이터 세트를 조작할 경우, 특히 모든 중간 결과를 조사하려는 경우에 유용합니다.

예제와 같이 다음 단계에서는 간단한 코드를 만들어 [중심 극한 정리](https://en.wikipedia.org/wiki/Central_limit_theorem)(Wikipedia)를 살펴봅니다. 이 예제는 Paul Teetor에 의해 *R Cookbook*에서 변형되었습니다.

1. `script.R` 편집기에서 다음 코드를 입력합니다.

    ```R
    mu <- 50
    stddev <- 1
    N <- 10000
    pop <- rnorm(N, mean = mu, sd = stddev)
    plot(density(pop), main = "Population Density", xlab = "X", ylab = "")
    ```

1. 결과를 빠르게 확인하려면 모든 코드를 선택(**Ctrl**+**A**)한 다음, **Ctrl**+**Enter**를 누르거나 마우스 오른쪽 단추를 클릭하고 **대화형으로 실행**을 선택합니다. 선택한 모든 코드가 직접 입력한 것처럼 대화형 창에서 실행되고 결과가 플롯 창에 표시됩니다.

    ![Visual Studio의 플롯 표시](media/getting-started-08-plot1.png)

1. 한 줄의 경우 언제든지 **Ctrl**+**Enter**만 누르면 대화형 창에서 해당 줄이 실행됩니다.

> [!Tip]
> 편집하고 **Ctrl**+**Enter**를 눌러(또는 **Ctrl**+**A**로 모든 내용을 선택한 다음, **Ctrl**+**Enter**를 누름) 코드를 빠르게 실행하는 패턴을 알아봅니다. 이 방법은 같은 작업에 마우스를 사용하는 것보다 훨씬 더 효율적입니다.
>
> 또한 Visual Studio 프레임에서 플롯 창을 끌어서 놓고 디스플레이에서 필요할 때마다 다른 곳에 배치할 수 있습니다. 그런 다음 플롯 창을 원하는 크기로 조정하고 이미지 또는 PDF 파일에 저장할 수 있습니다.

1. 몇 줄의 코드를 더 추가하여 두 번째 플롯을 포함합니다.

    ```R
    n <- 30
    samp.means <- rnorm(N, mean = mu, sd = stddev / sqrt(n))
    lines(density(samp.means))
    ```

1. **Ctrl**+**A** 및 **Ctrl**+**Enter**를 다시 눌러 코드를 실행하고 다음 결과를 생성합니다.

    ![Visual Studio의 업데이트된 이중 플롯](media/getting-started-09-plot2.png)

1. 문제는 첫 번째 플롯이 세로 배율을 결정하므로 두 번째 플롯(`lines` 포함)이 맞지 않는다는 것입니다. 이 문제를 해결하려면 `plot` 호출에서 `ylim` 매개 변수를 설정해야 하지만, 이 작업을 제대로 수행하려면 최대 세로 값을 계산하는 코드를 추가해야 합니다. `plot`을 호출하기 전에 `samp.means`를 사용하려면 코드를 다시 정렬해야 하므로 대화형 창에서 이 코드를 한 줄씩 실행하는 것은 불편합니다. 하지만 코드 파일에서는 손쉽게 제대로 편집할 수 있습니다.

    ```R
    mu <- 50
    stddev <- 1
    N <- 10000
    pop <- rnorm(N, mean = mu, sd = stddev)

    n <- 30
    samp.means <- rnorm(N, mean = mu, sd = stddev / sqrt(n))
    max.samp.means <- max(density(samp.means)$y)

    plot(density(pop), main = "Population Density",
        ylim = c(0, max.samp.means),
        xlab = "X", ylab = "")
    lines(density(samp.means))
    ```

1. **Ctrl**+**A** 및 **Ctrl**+**Enter**를 다시 누르면 결과가 표시됩니다.

    ![제대로 크기 조정된 Visual Studio의 업데이트된 이중 플롯](media/getting-started-10-plot3.png)

편집기에서 더 많은 작업을 수행할 수 있습니다. 자세한 내용은 [편집 R 코드](editing-r-code-in-visual-studio.md), [IntelliSense](r-intellisense.md) 및 [코드 조각](code-snippets-for-r.md)을 참조하세요.

## <a name="debug-your-code"></a>코드 디버그

Visual Studio의 키 수준 중 하나는 디버깅 UI입니다. RTVS는 이 강력한 기초 위에 빌드되고 [변수 탐색기](variable-explorer.md)와 같은 혁신적인 UI를 추가합니다. 여기서 디버깅의 개요를 살펴보겠습니다.

1. 시작하려면 **R 도구** > **세션** > **다시 설정** 메뉴 명령을 통해 현재 작업 영역을 다시 설정하여 지금까지 수행한 모든 작업을 지웁니다. 기본적으로 대화형 창에서 수행한 모든 작업은 현재 세션에서 생성된 후 디버거에서 사용됩니다. 세션을 다시 설정하면 디버깅 세션이 기존 데이터 없이 시작됩니다. 그러나 **다시 설정** 명령은 *script.R* 원본 파일에 영향을 주지 않습니다. 소스 파일이 작업 영역 외부에서 관리 및 저장되기 때문입니다.

1. 이전 섹션에서 생성된 *script.R* 파일을 사용하여 `pop <-`로 시작하는 줄에 캐럿을 배치한 다음, **F9**를 누르거나 **디버그** > **중단점 설정/해제** 메뉴 명령을 선택하여 해당 줄에서 중단점을 설정합니다. 또는 빨간색 중단점이 나타나는 줄의 왼쪽 여백을 클릭합니다.

    ![편집기에서 중단점 설정](media/getting-started-11-debug1.png)

1. 도구 모음에서 **소스 시작 파일** 단추를 선택하거나, **디버그** > **소스 시작 파일** 메뉴 항목을 선택하거나, **F5**를 눌러 *script.R*의 코드를 사용하여 디버거를 시작합니다. Visual Studio가 디버깅 모드로 전환되고 코드 실행이 시작됩니다. 하지만 코드는 중단점을 설정한 줄에서 중지합니다.

    ![Visual Studio 디비거의 중단점에서 중지](media/getting-started-12-debug2.png)

1. 디버깅하는 동안 Visual Studio는 한 줄씩 코드를 단계별로 실행하는 기능을 제공합니다. 함수에 대해 한 단계씩 코드 실행, 프로시저 단위 실행 또는 호출 컨텍스트로 프로시저 나가기를 수행할 수 있습니다. 이러한 기능은 다른 기능과 함께 **디버그** 메뉴, 편집기의 마우스 오른쪽 단추 클릭 상황에 맞는 메뉴 및 디버그 도구 모음에서 찾을 수 있습니다.

    ![Visual Studio의 디버그 도구 모음](media/getting-started-13-debug3.png)

1. 중단점에서 중지한 경우 변수 값을 검사할 수 있습니다. Visual Studio에서 **자동** 창을 찾고 아래쪽 가장자리에 있는 **로컬**이라는 탭을 선택합니다. **로컬** 창에는 프로그램의 현재 지점에 있는 로컬 변수가 표시됩니다. 이전에 설정한 중단점에서 중지된 경우 `pop` 변수가 아직 정의되지 않은 것으로 표시됩니다. 이제 **디버그** > **프로시저 단위 실행** 명령(**F10**)을 사용하면 `pop`의 값이 나타납니다.

    ![Visual Studio의 로컬 창](media/getting-started-14-debug4.png)

1. 전역 범위 및 패키지 범위를 포함하여 다른 범위의 변수를 검사하려면 [변수 탐색기](variable-explorer.md)를 사용합니다. 변수 탐색기에서는 정렬 가능한 열이 있는 테이블 형식 뷰로 전환하고 데이터를 CSV 파일로 내보내는 기능을 제공합니다.

    ![변수 탐색기의 확장된 보기](media/variable-explorer-expanded-results.png)

1. 계속해서 프로그램을 한 줄씩 단계별로 실행하거나 **계속**(**F5**)을 선택하여 완료될 때까지(또는 다음 중단점까지) 실행할 수 있습니다.

자세한 내용은 [디버깅](debugging-r-in-visual-studio.md) 및 [변수 탐색기](variable-explorer.md)를 참조하세요.

## <a name="next-steps"></a>다음 단계

이 연습에서는 Visual Studio의 대화형 창, 코드 편집 및 디버깅을 사용하여 R 프로젝트의 기본 사항을 알아보았습니다. 계속해서 더 많은 기능을 살펴보려면 목차에 표시된 문서와 다음 문서를 참조하세요.

- [샘플 프로젝트](getting-started-samples.md)
- [코드 편집](editing-r-code-in-visual-studio.md)
- [디버깅](debugging-r-in-visual-studio.md)
- [작업 영역](r-workspaces-in-visual-studio.md)
- [코드 시각화](visualizing-data-with-r-in-visual-studio.md)
