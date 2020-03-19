---
title: R 도구 옵션
description: R 언어 및 관련 기능에 대한 Visual Studio의 옵션 참조입니다.
ms.date: 12/04/2017
ms.topic: reference
f1_keywords:
- vs.toolsoptionspages.text_editor.r.advanced
- vs.toolsoptionspages.r_tools
- vs.toolsoptionspages.r_tools.advanced
- vs.toolsoptionspages.r_tools.#150
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: c7c2cb57dc96d7bb0df09248eb7a877820e50521
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79307066"
---
# <a name="r-tools-for-visual-studio-options"></a>Visual Studio용 R 도구 옵션

설정은 **R 도구** > **옵션** 메뉴를 통해 액세스하거나 **도구** > **옵션**을 통해 **R 도구**로 스크롤하여 액세스합니다.

  ![R 도구의 [옵션] 대화 상자](media/options-dialog.png)

아래 방법을 사용하여 R에 관련된 옵션 및 설정에 액세스합니다. 이러한 섹션을 모두 표시하려면 **옵션** 대화 상자의 맨 아래에 있는 **모든 설정 표시** 상자를 선택해야 합니다.

- 코드 서식 지정 옵션([편집기 옵션](editing-r-code-in-visual-studio.md#editor-options) 참조: **도구** > **옵션** 메뉴에서 **텍스트 편집기** > **R** > **서식 지정**을 선택합니다.
- Linter 옵션([Linting](linting-r-code.md) 참조): **도구** > **옵션** 메뉴에서 **텍스트 편집기** > **R** > **Lint**를 선택합니다.
- 고급 편집기 옵션([이 문서에 설명됨](#text-editor--r--advanced-options)): **도구** > **옵션** 메뉴에서 **텍스트 편집기** > **R** > **고급**을 선택합니다.
- 동작 옵션([이 문서에 설명됨](#r-tools--advanced-options)): **R 도구** > **옵션** 메뉴 또는 **도구** > **옵션**에서 **R 도구**까지 스크롤합니다.

**R 도구** > **데이터 과학 설정** 명령은 전체 Visual Studio에서 다양한 다른 설정에도 영향을 미칩니다. 이 명령에 대해서는 다음 섹션에서 설명합니다.

<a name="data-scientist-layout"></a>

## <a name="r-tools--data-science-settings"></a>R 도구 > 데이터 과학 설정

**R 도구 > 데이터 과학 설정** 메뉴 항목은 데이터 과학자의 필요에 맞게 최적화된 레이아웃으로 Visual Studio IDE를 구성합니다. 특히 이 옵션을 선택하면 [대화형](interactive-repl-for-r-in-visual-studio.md), [변수 탐색기](variable-explorer.md) 및 [작업 영역](r-workspaces-in-visual-studio.md) 창이 열립니다.

![Visual Studio의 데이터 과학자 창 레이아웃](media/installation-data-scientist-layout-result.png)

나중에 다른 Visual Studio 설정으로 되돌리려면 먼저 **도구** > **설정 가져오기 및 내보내기** 명령을 사용하여 **선택한 환경 설정 내보내기**를 선택하고 파일 이름을 지정합니다. 이러한 설정을 복원하려면 동일한 명령을 사용하고 **선택한 환경 설정 가져오기**를 선택합니다. 데이터 과학자 레이아웃을 변경한 후 나중에 다시 해당 레이아웃으로 돌아가려는 경우에도 **데이터 과학 설정** 명령을 직접 사용하는 대신 같은 명령을 사용할 수 있습니다.

## <a name="text-editor--r--advanced-options"></a>텍스트 편집기 > R > 고급 옵션

이러한 옵션은 R에 대한 서식 지정, IntelliSense, 개요, 들여쓰기 및 구문 검사 동작을 제어합니다.

![R 텍스트 편집기 고급 옵션의 옵션 대화 상자](media/options-dialog-advanced-text-editor.png)

각 옵션은 설정 또는 해제로 설정되어 문제가 된 동작을 제어합니다. 각 옵션이 주는 영향에 대한 자세한 내용은 대화 상자의 맨 아래에 있는 도움말 창을 확인합니다. 창을 크게 만들기 위해 해당 도움말 창의 상단으로 끌어올 수 있습니다.

![R 텍스트 편집기 고급 옵션 대화 상자의 확장 도움말 창](media/options-dialog-advanced-text-editor2.png)

## <a name="r-tools--advanced-options"></a>R 도구 > 고급 옵션

**R 도구** > **옵션** 메뉴 명령 창은 R 옵션에 대한 **옵션** 대화 상자를 엽니다.

  ![R 도구의 [옵션] 대화 상자](media/options-dialog.png)

다음 섹션에서는 이 페이지에서 제공되는 다양한 옵션을 설명합니다.

### <a name="debugging"></a>디버깅

이러한 옵션은 [변수 탐색기](variable-explorer.md) 및 조사식 및 지역 같은 디버거 창에서 값을 처리하는 방법을 제어합니다([R 코드 디버그](debugging-r-in-visual-studio.md) 참조).

| 옵션 | 기본값 | Description |
| --- | --- | --- |
| 활성 바인딩 평가 | `True` | `True`인 경우 변수 및 속성을 검사할 때 항상 최신 값이 표시되도록 합니다. 식을 평가하면 구현 방법에 따라 부작용이 발생할 수 있습니다. |
| 점 접두사가 있는 변수 표시 | `False` | `.` 접두사가 있는 변수를 표시할지 지정합니다. |

### <a name="grid-view"></a>그리드 보기

| 옵션 | 기본값 | Description |
| --- | --- | --- |
| 동적 평가 | `False` | 기본적으로는 `View(<expression>)` 함수는 데이터의 스냅샷을 데이터 프레임으로 만듭니다. 여기서는 큰 데이터 세트을 포함한 많은 메모리를 사용할 수 있습니다. 이 옵션을 `True`로 설정하면 표시되는 해당 데이터를 가져오기 위해 표를 새로 고칠 때 식이 계산됩니다. 그러나 식이 변경되면 데이터도 변경됩니다. 그러면 dplyr pip 식에 적합하지 않을 수 있습니다. |

### <a name="help"></a>도움말

| 옵션 | 기본값 | Description |
| --- | --- | --- |
| F1 웹 브라우저 | `Internal` | **Ctrl**+**F1**을 사용하여 용어를 검색하는 동안 도움말이 표시되는 방식을 제어합니다. `Internal`로 설정되면 Visual Studio의 도구 창 내에서 도움말이 렌더링됩니다. `External`로 설정되면 기본 웹 브라우저에서 도움말이 나타납니다. |
| F1 웹 검색 문자열 | `R site:stackoverflow.com` | 편집기의 용어에서 **Ctrl**+**F1**을 누를 때 검색어가 검색 엔진에 전달되는 방식을 제어합니다. 기본적으로 문자열은 `R site:stackoverflow.com`입니다. 이 문자열은 `R`를 검색어에 추가합니다. `site:stackoverflow.com`은 `stackoverflow.com` 도메인 내의 페이지로 검색 범위를 지정하도록 알리는 검색 엔진에 대한 지시문입니다. |
| R 도움말 브라우저 | `Automatic` | **F1**, **?** 또는 **??** 를 사용하여 R 문서를 검색하는 동안 도움말이 표시되는 방식을 제어합니다. `Automatic`으로 설정되면 해당하는 창에서 도움말이 렌더링됩니다. 예를 들어 HTML 도움말은 Visual Studio 도구 창 내에 표시되지만 PDF는 기본 PDF 프로그램에 나타납니다. `External`로 설정되면 기본 웹 브라우저에서 도움말이 렌더링됩니다. |

### <a name="history"></a>기록

| 옵션 | 기본값 | Description |
| --- | --- | --- |
| 항상 기록 저장 | `True` | RTVS가 프로젝트가 닫힐 때마다 작업 디렉터리의 *.RHistory* 파일에 명령 기록을 쓸지 제어합니다. 종료하기 전에 프로젝트를 저장하지 않은 경우에도 기록 저장이 수행됩니다. |
| 검색 필터 다시 설정 | `True` | [기록] 창에서 부분 문자열이 [R 기록] 대화 상자의 필터 용어와 일치하는 명령만 표시하도록 명령 기록을 필터링할 수 있는지 결정합니다. 이 설정에 따라 새 명령을 실행할 때마다 또는 새 프로젝트로 전환하여 다른 *.RHistory* 파일의 로드를 트리거할 때마다 기록 검색 필터를 다시 설정할지가 결정됩니다. 기본 설정 `True`는 필터 집합 관련 명령을 실행할 때 문제를 최소화하며 사용자는 방금 실행한 명령이 기록에 표시되지 않은 이유를 궁금해합니다. |
| 여러 줄 선택 사용 | `True` | 한 번 클릭으로 기록에서 여러 줄 문을 선택할 수 있는지 지정합니다. 또한 줄이 아닌 문별로 대화형 창에서 위쪽/아래쪽 화살표 탐색을 사용하도록 설정합니다. |

### <a name="html"></a>HTML

| 옵션 | 기본값 | Description |
| --- | --- | --- |
| HTML 페이지 브라우저 | `External` | `ggvis` 플롯 등의 콘텐츠나 `shiny` 애플리케이션이 렌더링되는 위치를 결정합니다. `Internal`은 Visual Studio의 도구 창 내에 HTML 출력을 표시합니다. `External`은 기본 브라우저에 HTML 출력을 표시합니다. |

### <a name="logging"></a>로깅

| 옵션 | 기본값 | Description |
| --- | --- | --- |
| 로그 이벤트 | `Normal` | RTVS 진단에 사용되는 로깅의 자세한 정도를 제어합니다. `Normal`의 기본 설정은 `TEMP` 디렉터리에서 로그 파일을 만듭니다. `Traffic`으로 설정되면 RTVS는 해당 세션의 모든 명령과 응답을 기록합니다. 이러한 로그 파일은 컴퓨터에서 유지되며 RTVS에서 문제를 진단하는 데 도움이 될 수 있습니다. |

### <a name="markdown"></a>Markdown

| 옵션 | 기본값 | Description |
| --- | --- | --- |
| Markdown 미리 보기 단추 | `External` | RMarkdown HTML 출력을 표시할지 결정합니다. `Internal`은 Visual Studio의 도구 창 내에 RMarkdown HTML 문서를 표시합니다. `External`은 기본 브라우저에 RMarkdown HTML을 표시합니다. |

### <a name="r-engine"></a>R 엔진

| 옵션 | 기본값 | Description |
| --- | --- | --- |
| 코드 페이지 | `(OS Default)` | R에 대한 코드 페이지(로캘)를 설정합니다. 기본적으로 운영 체제의 기본 로캘을 사용합니다. |
| CRAN 미러 | `(Use .Rprofile)` | 패키지 설치에 대한 기본 CRAN 미러를 설정합니다. `Use .Rprofile`의 기본 설정은 CRAN Mirror 설정을 *.RProfile* 파일에 보존합니다. |

### <a name="workspace"></a>작업 영역

| 옵션 | 기본값 | Description |
| --- | --- | --- |
| 프로젝트가 열리면 작업 영역 로드 | `No` | `Yes`로 설정하면 프로젝트가 열릴 때 *.RData* 파일에서 전역 환경으로 세션 데이터를 로드할 수 있습니다. |
| 다시 설정할 때 작업 영역 저장 메시지 표시 | `Yes` | `No`로 설정하면 대화형 창에서 [다시 설정] 단추를 클릭할 때 작업 영역을 저장할지 묻는 메시지가 표시되지 않습니다. |
| 프로젝트가 닫히면 작업 영역 저장 | `No` | `Yes`로 설정하면 프로젝트가 닫힐 때 전역 환경을 *.RData* 파일에 저장할 수 있습니다. |
| 작업 영역을 전환하기 전에 확인 대화 상자를 표시합니다. | `Yes` | `No`로 설정하면 작업 영역 간에 전환할 때 사용자에게 확인 메시지가 표시되지 않습니다. [작업 영역 간 전환](r-workspaces-in-visual-studio.md#switch-between-workspaces) 참조 |
| 컴퓨터 부하 표시기 표시 | `False` | 상태 표시줄에 있는 CPU/메모리/네트워크 부하 표시기의 표시 유형을 제어합니다. 표시기에서 네트워크 트래픽이 발생하기 때문에 원격 요금 시나리오를 `False`로 설정하는 것이 유용합니다. 이 옵션을 변경하면 Visual Studio를 다시 시작해야 합니다. |
