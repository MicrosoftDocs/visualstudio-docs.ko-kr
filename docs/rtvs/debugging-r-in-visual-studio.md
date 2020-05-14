---
title: R 코드 디버깅
description: Visual Studio는 중단점, 연결, 호출 스택 및 검사 변수를 포함하여 R에 대한 전체 디버깅 환경을 제공합니다.
ms.date: 01/24/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 5efa0a32f51e1f5060474a0d277bfca7f1e7d548
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "73189262"
---
# <a name="debug-r-in-visual-studio"></a>Visual Studio에서 R 디버그

RTVS(Visual Studio용 R 도구)는 Visual Studio의 전체 디버깅 환경과 통합됩니다([Visual Studio의 디버깅](../debugger/debugger-feature-tour.md) 참조). 이러한 지원에는 중단점, 실행 중인 프로세스에 연결, 변수 검사 및 감시, 호출 스택 검사 등이 포함됩니다. 이 문서에서는 R 및 RTVS에 고유한 디버깅 측면을 살펴봅니다.

R 프로젝트에서 시작 R 파일에 대한 디버거를 시작하는 방법은 다른 프로젝트 형식의 경우도 동일합니다. **디버그** > **디버깅 시작**, **F5** 키 또는 디버그 도구 모음의 **소스 시작 파일**을 사용합니다.

![R에 대한 디버거 시작 단추](media/debugger-start-button.png)

시작 파일을 변경하려면 솔루션 탐색기에서 파일을 마우스 오른쪽 단추로 클릭하고 **시작 R 스크립트로 설정**을 선택합니다.

모든 경우에 디버거를 시작하면 대화형 창에서 파일이 “원본 제공”됩니다. 즉, 파일이 로드되고 대화형 창의 출력과 같이 로드된 위치에서 실행됩니다.

```output
> rtvs::debug_source("c:/proj/rproject1/rproject1/script.R")
Sourcing: c:\proj\rproject1\rproject1\script.R
Sourcing: c:\proj\rproject1\rproject1\Settings.R
```

`rtvs::debug_source` 함수를 사용하여 스크립트가 원본 제공되고 있음을 확인합니다. RTVS는 디버깅 준비 시 코드를 수정해야 하므로 이 함수가 필요합니다. RTVS 원본 제공 명령을 사용 중이며 디버거가 연결되어 있으면 Visual Studio에서 자동으로 `rtvs::debug_source`를 사용합니다.

대화형 창의 도구 모음에서 **R 도구** > **세션** > **디버거 연결** 명령, **디버그** > **R 대화형에 연결** 명령 또는 **디버거 연결** 명령을 사용하여 대화형 창에서 직접 디버거를 수동으로 연결할 수도 있습니다. 작업을 완료했으면 디버그할 파일을 원본 제공해야 합니다. 수동으로 파일을 원본 제공하려는 경우 R에서 일반적인 `rtvs::debug_source` 명령 대신 `source`를 사용해야 합니다.

디버거와 대화형 창 간의 이 연결을 통해 다양한 매개 변수 값을 사용한 함수 호출(및 디버그) 같은 작업을 더 쉽게 수행할 수 있습니다. 예를 들어 원본 제공된 파일에 다음과 같은 함수가 있다고 가정해 보겠습니다(세션으로 로드되었음을 의미함).

```R
add <- function(x, y) {
    return(x + y)
}
```

그 다음에 `return` 문에서 중단점을 설정합니다. 이제 대화형 창에서 `add(4,5)`를 입력하면 디버거가 중단점에서 중지합니다.

## <a name="environment-browser-in-the-interactive-window"></a>대화형 창의 환경 브라우저

디버거에서 중지되면 [대화형 창](interactive-repl-for-r-in-visual-studio.md)의 환경 브라우저 프롬프트에서도 중지됩니다. 프롬프트는 `Browse[n]>`으로 나타납니다. 여기서 n은 숫자입니다.

환경 브라우저에서는 다양한 특수 명령을 지원합니다.

| 명령 | Description |
| --- | --- |
| n | 다음: 코드 파일에서 다음 문을 실행합니다(단위 실행과 같음). |
| s | 한 단계씩 코드 실행: 코드 파일에서 다음 문을 실행하여 다음 문이 함수 호출인 경우 함수 범위로 한 단계씩 코드를 실행합니다. |
| f | 마침: 현재 함수 범위의 나머지를 실행하고 호출자로 돌아갑니다(단계 출력과 같음). |
| c, cont | 계속: 프로그램을 다음 중단점까지 실행합니다. |
| Q | 끝내기: 디버깅 세션을 종료합니다. |
| 라는 설치 관리자 실행 파일에 포함됩니다. 여기서 | 스택 표시: 대화형 창에 호출 스택을 표시합니다. |
| help | 도움말 표시: 대화형 창에 사용 가능한 명령을 표시합니다. |
| &lt;expr&gt; | *expr*의 식을 계산합니다. |

![대화형 창의 환경 브라우저](media/debugger-environment-browser.png)
