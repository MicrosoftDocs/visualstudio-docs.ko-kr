---
title: R에 대한 도움말 창
description: R에 대한 도움말은 ? 선택합니다.
ms.date: 01/24/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: af6c6156b1d88c1d015f7700fc7bed061bbe9a76
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62950558"
---
# <a name="help-in-r-tools-for-visual-studio"></a>Visual Studio용 R 도구의 도움말

R에 대한 도움말은 Visual Studio의 대화형 창에 직접 통합됩니다. `?` 등의 `?mtcars` 명령을 사용할 때마다 R 설명서의 도움말이 Visual Studio 창에 나타납니다.

![Visual Studio의 도움말 창](media/help-window.png)

> [!Tip]
> Visual Studio의 모든 다른 항목처럼 [도움말] 창을 원하는 대로 정렬 및 고정할 수 있습니다. [Visual Studio에서 창 레이아웃 사용자 지정](../ide/customizing-window-layouts-in-visual-studio.md)을 참조하세요.
>
> 브라우저에서 도움말 결과를 열려면 **R 도구** > **옵션** 메뉴를 선택하고 **R 도움말 브라우저** 속성을 `External`로 설정합니다. [옵션](options-for-r-tools-in-visual-studio.md)을 참조하세요.

도움말을 검색하려면 `??` 명령과 검색어를 차례로 사용합니다. 검색에 공백이 있으면 따옴표를 사용합니다.

```R
??"Motor Trend"
```

![도움말 검색 결과](media/help-search1.png)

[도움말] 창에는 R 설명서에서 직접 추가 검색을 수행하는 데 사용되는 검색 입력 필드도 있습니다.

![입력 필드를 사용한 도움말 검색 결과](media/help-search2.png)

## <a name="integrated-help-lookup"></a>통합 도움말 조회

개발자는 종종 R 설명서에서 함수 이름, 데이터 세트 및 기타 요소에 대한 도움말을 검색합니다. RTVS(Visual Studio용 R 도구)에서는 도움말 조회를 편집기 및 대화형 창에 직접 통합하여 프로세스를 간소화합니다.

- 자동 완성 작업 중에 **F1** 키를 누르면 부분 문자열과 일치하는 도움말 결과 목록이 생성됩니다.
- 검색어(예: 함수)를 마우스 오른쪽 단추로 클릭하고 **도움말** 명령을 선택하면 해당 함수에 대한 도움말이 열립니다. 선택에 대한 **도움말**을 호출할 수도 있습니다.

    ![마우스 오른쪽 단추 클릭 상황에 맞는 메뉴를 통해 도움말 호출](media/help-right-click.png)

> [!Tip]
> 통합 도움말을 브라우저에서 열려면 **R 도구** > **옵션**을 선택하고 **F1 웹 브라우저**를 `External`로 설정합니다. [옵션](options-for-r-tools-in-visual-studio.md)을 참조하세요.

## <a name="integrated-stackoverflow-search"></a>통합 StackOverflow 검색

R 설명서를 검색할 뿐 아니라 개발자는 코드를 작성하는 동안 종종 StackOverflow를 검색합니다. RTVS에서는 이 프로세스도 간소화합니다. 용어나 선택 항목을 마우스 오른쪽 단추로 클릭하고 **웹 검색** 명령(**Ctrl**+**F1**)을 선택하면 Visual Studio에서 StackOverflow로 범위가 지정된 검색 결과가 표시된 창이 열립니다.

![Visual Studio의 웹 검색 결과](media/help-web-search-results.png)

추가된 범위 지정 문자열 `R site:stackoverflow`는 **R 도구** > **옵션** > **F1 웹 검색 문자열** 옵션을 통해 변경할 수 있습니다.

![F1 웹 검색 문자열 옵션 변경](media/options-dialog.png)

브라우저에서 결과를 표시하려는 경우 **옵션**에 설명된 대로 [F1 웹 브라우저](options-for-r-tools-in-visual-studio.md) 옵션을 변경합니다.