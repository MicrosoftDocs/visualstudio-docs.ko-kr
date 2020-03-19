---
title: R에 대한 변수 탐색기
description: Visual Studio의 변수 탐색기는 현재 R 세션에서 지정된 범위에 있는 모든 변수를 표시합니다.
ms.date: 01/24/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 799b7f2789898e0d02d9588f9a3ad7d1e8098a00
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62809872"
---
# <a name="variable-explorer"></a>변수 탐색기

**R 도구** > **Windows** > **변수 탐색기**(또는 **R 도구** > **데이터 과학 설정**을 사용한 경우 **Ctrl**+**8**)를 사용하여 연 **변수 탐색기** 창에는 현재 R 세션에서 제공된 범위의 모든 변수가 표시됩니다. 예를 들어 **변수 탐색기**를 열고 [대화형 창](interactive-repl-for-r-in-visual-studio.md)에 다음 줄을 입력할 경우:

```R
x <- 42
y <- 43
n <- c(1,2,3,5,8,13)
```

**변수 탐색기** 창이 다음과 같이 표시됩니다.

![Visual Studio의 변수 탐색기 창](media/variable-explorer-window.png)

세션에 정의된 더 복잡한 R 데이터 프레임이 있는 경우 데이터로 이동할 수 있습니다. 예를 들어 `cars <- mtcars`를 실행한 후 **변수 탐색기**에서 다른 노드를 확장하여 데이터 세트를 탐색할 수 있습니다.

![변수 탐색기의 확장된 보기](media/variable-explorer-expanded-results.png)

변수를 삭제하려면 마우스 오른쪽 단추를 클릭하고 **삭제**를 선택하거나, 변수를 선택하고 **Delete** 키를 누릅니다.

증분 검색을 사용하여 데이터 프레임에서 관찰을 검색할 수도 있습니다. 먼저 검색할 데이터 프레임에서 노드를 확장하고 검색 상자에 검색어를 입력합니다.

## <a name="details-table-view"></a>세부 정보(테이블) 보기

데이터는 테이블 형식으로 제공되는 경우가 많으므로 돋보기 아이콘을 선택하거나 마우스 오른쪽 단추를 클릭하고 **자세한 정보 표시**를 선택하여 복잡한 데이터 형식을 개별 테이블로 볼 수 있습니다.

![변수 탐색기 테이블 뷰](media/variable-explorer-table-view.png)

열 제목을 클릭하면 데이터가 열을 기준으로 정렬됩니다(오름차순 및 내림차순 간 전환). **Shift** 키를 누른 채 추가 열을 클릭하면 해당 열도 정렬에 추가됩니다. **Shift** 키 없이 열을 클릭하면 단일 열 정렬로 돌아갑니다.

열 제목을 클릭한 순서에 따라 정렬 수행 순서가 결정됩니다. 예를 들어 **Shift**+키를 누른 채 **cyl** 열을 **클릭**한 다음, **Shift**+ 키를 누른 채 **mpg** 열을 두 번 **클릭**하면 목록에서 실린더가 오름차순으로, 연료 소비량이 내림차순으로 정렬됩니다.

![두 개의 열 기준으로 정렬하는 데이터의 테이블 뷰.](media/variable-explorer-table-view-sorting.png)

**변수 탐색기** 및 테이블 뷰는 개별 Visual Studio 창에 있으므로 사용자가 단계별 작업을 선호하는 경우 정렬할 수 있습니다. 일반적인 지침은 [Visual Studio에서 창 레이아웃 사용자 지정](../ide/customizing-window-layouts-in-visual-studio.md)을 참조하세요.

## <a name="open-in-excel-or-other-csv-capable-application"></a>Excel(또는 기타 CSV 지원 애플리케이션)에서 열기

추가 조작 및 분석을 위해 일반적으로 세션 변수를 CSV로 내보내는 것이 좋습니다. **변수 탐색기**에서 각 노드 옆에 있는 작은 Excel 아이콘(![Excel 내보내기 아이콘](media/variable-explorer-excel-icon.png))을 사용하거나 항목을 마우스 오른쪽 단추로 클릭하고 **CSV 앱에서 열기**를 선택하여 내보내기를 수행합니다. 아이콘을 선택하면 데이터가 *%userprofile%\Documents\RTVS_CSV_Exports* 폴더의 새 CSV 파일에 기록되고 해당 파일이 시작됩니다. 파일은 *.csv* 확장과 연결된 애플리케이션에서 열립니다.

## <a name="scopes"></a>범위

기본적으로 **변수 탐색기**는 전역 범위에 대해 열립니다. 패키지 범위로 전환하려면 창 맨 위의 드롭다운에서 패키지를 선택합니다.

![패키지 범위가 표시된 변수 탐색기](media/variable-explorer-package-scopes.png)

디버거의 중단점에서 멈춘 경우 함수 범위로 전환할 수도 있습니다. **변수 탐색기**가 디버그되는 코드의 함수 범위로 자동으로 전환되지는 않습니다.

![디버그 중인 데이터 프레임이 표시된 변수 탐색기](media/variable-explorer-as-locals-window.png)

**변수 탐색기**에서는 디버거에서 함수의 로컬 변수 표시와 같이 코드를 단계별로 진행함에 따라 자동으로 함수 범위를 변경합니다.

## <a name="import-data-into-variable-explorer"></a>변수 탐색기로 데이터 가져오기

**변수 탐색기** 도구 모음의 다음 두 가지 명령(**R 도구** > **데이터** 메뉴를 통해 사용할 수도 있음)은 외부 CSV 데이터 세트를 R 세션으로 가져옵니다.  **웹 URL에서 R 세션으로 데이터 세트 가져오기** 및 **텍스트 파일에서 R 세션으로 데이터 세트 가져오기**

가져올 CSV 파일을 확정하고 나면 Visual Studio에서 **데이터 세트 가져오기** 대화 상자를 표시합니다. 여기에는 해당 데이터 파일을 구문 분석하는 방법(필드 구분 기호 및 따옴표 처리 방법 선택)을 제어하는 옵션이 있습니다. 가져온 데이터 프레임 및 원본 데이터 파일의 미리 보기를 확인할 수도 있습니다.

![데이터 세트 가져오기 대화 상자](media/variable-explorer-import-dataset-dialog.png)
