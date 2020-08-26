---
title: R Markdown
description: Visual Studio에서 R Markdown 문서를 만들어 고품질 보고서, 프레젠테이션 및 대시보드를 생성하는 방법입니다.
ms.date: 11/16/2017
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 2cfad81c44822e59abb704e5e830357bfd32067d
ms.sourcegitcommit: a801ca3269274ce1de4f6b2c3f40b58bbaa3f460
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88801557"
---
# <a name="create-r-markdown-documents"></a>R Markdown 문서 만들기

[R Markdown](https://rmarkdown.rstudio.com/)은 R의 분석을 고품질 문서, 보고서, 프레젠테이션 및 대시보드로 전환하는 문서 형식입니다.

RTVS(Visual Studio용 R 도구)는 R Markdown 항목 템플릿, 편집기 지원(편집기 내에 R 코드용 IntelliSense 포함), 파일 생성 기능 및 실시간 미리 보기를 제공합니다.

## <a name="using-r-markdown"></a>R Markdown 사용

1. Visual Studio를 닫습니다.
1. (한 번만 실행) [pandoc.org](https://pandoc.org/installing.html)에서 `pandoc`를 설치합니다.
1. Visual Studio를 다시 시작합니다(pandoc 설치를 선택해야 함).
1. `knitr` 및 `rmarkdown` 패키지를 설치합니다([대화형 창](interactive-repl-for-r-in-visual-studio.md)에서 수행할 수 있음).

    ```R
    install.packages("knitr")
    install.packages("rmarkdown")

    ```

1. **파일** > **새로 만들기** > **파일** 메뉴 명령을 사용하고 목록에서 **R** > **R Markdown**을 선택하여 새로운 R Markdown 파일을 만듭니다. 프로젝트의 컨텍스트에서 솔루션 탐색기의 프로젝트를 마우스 오른쪽 단추로 클릭하고 **R Markdown 추가**를 선택(또는 **추가** > **새 항목**을 선택하고 목록에서 **R Markdown**을 선택)합니다.

1. 새 파일의 기본 콘텐츠는 다음과 같습니다.

    <!-- markdownlint-disable MD048 -->
    ~~~markdown
    ---
    title: "Untitled"
    output: html_document
    ---

    This is an R Markdown document. Markdown is a simple formatting syntax for authoring HTML, PDF, and Microsoft Word documents. For more details on using R Markdown see <http://rmarkdown.rstudio.com>.

    When you select the **R Tools | Publish | Preview** button, a document will be generated that includes both content as well as the output of any embedded R code chunks within the document. You can embed an R code chunk like this:

    ```{r}
    summary(cars)
    ```

    You can also embed plots, for example:

    ```{r, echo=FALSE}
    plot(cars)
    ```

    Note that the `echo = FALSE` parameter was added to the code chunk to prevent printing of the R code that generated the plot.

    ~~~
    <!-- markdownlint-disable MD048 -->

## <a name="previews"></a>미리 보기

Visual Studio 2017 버전 15.5 이상은 R Markdown에 대한 실시간 미리 보기를 자동으로 제공합니다. 편집기와 미리 보기 간에 자동 동기화를 설정하려면 **R 도구** > **Markdown** > **자동 동기화**(**Ctrl**+**Shift**+**Y**)를 선택합니다. 자동 동기화를 사용하지 않는 경우 **R 도구** > **Markdown** > **R Markdown 미리 보기 다시 로드**를 사용하여 미리 보기를 새로 고칠 수 있습니다.

편집기에서 마우스 오른쪽 단추로 클릭하고 **미리 보기** 명령 중 하나를 선택하여 HTML, PDF 및 Microsoft Word 형식의 파일을 미리 볼 수 있습니다. 동일한 명령을 **R 도구** > **Markdown** 메뉴에서 사용할 수 있습니다. (이전 버전의 Visual Studio인 경우 이러한 명령은 **R 도구** > **게시** 메뉴에 있습니다.)

![R Markdown 실시간 미리 보기 및 기타 미리 보기 메뉴 명령](media/rmarkdown-live-preview.png)
