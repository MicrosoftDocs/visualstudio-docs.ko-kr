---
title: 코드 메트릭 창
ms.date: 12/12/2017
ms.topic: reference
f1_keywords:
- vs.codemetrics.output
helpviewer_keywords:
- code metrics results
- code metrics results window
- results window, code metrics
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6d62baf32685832072266438de003b523399137f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75587084"
---
# <a name="use-the-code-metrics-results-window"></a>코드 메트릭 결과 창 사용

**코드 메트릭 결과** 창에는 코드 메트릭 분석에 의해 생성 된 데이터가 표시 됩니다. 코드 메트릭 데이터 값에 대 한 자세한 내용은 [코드 메트릭 값](../code-quality/code-metrics-values.md)을 참조 하세요.

## <a name="display-code-metrics-results"></a>코드 메트릭 결과 표시

코드 **메트릭 결과 창은 코드** 메트릭 결과를 생성할 때 자동으로 표시 됩니다. 언제 든 지 창을 표시할 수도 있습니다.

다음 메뉴 시퀀스 중 하나를 사용 하 여 코드 메트릭 결과 창을 표시할 수 있습니다.

- **분석** 메뉴에서 **Windows**  >  **코드 메트릭 결과**를 선택 합니다.

- **보기** 메뉴에서 **기타 Windows**  >  **코드 메트릭 결과**를 선택 합니다.

결과를 포함 하지 않는 경우에도 **코드 메트릭 결과** 창이 열립니다.

### <a name="to-view-code-metrics-details"></a>코드 메트릭 세부 정보를 보려면

코드 메트릭 결과가 생성 된 경우 **계층** 열에서 트리를 확장 합니다.

## <a name="filter-code-metrics-results"></a>코드 메트릭 결과 필터링

위쪽의 도구 모음을 사용 하 여 **코드 메트릭 결과** 창에 표시 되는 결과를 필터링 할 수 있습니다. 예를 들어 유지 관리 인덱스가 65 미만인 결과만 표시 하려는 경우가 있습니다.

**필터** 드롭다운 상자에는 결과 열의 이름이 포함 됩니다. 필터가 정의 되 면 들여쓰기를 사용 하 여 목록의 맨 아래에 추가 됩니다. 이 목록에는 정의 된 마지막 10 개의 필터가 포함 될 수 있습니다.

### <a name="to-filter-the-code-metrics-results"></a>코드 메트릭 결과를 필터링 하려면

1. **필터** 목록에서 열 이름을 선택 합니다.

2. **최소값**에 표시 되는 최소값을 입력 합니다.

3. **최대**값에 표시 될 최대값을 입력 합니다.

4. **필터 적용** 단추를 클릭 합니다.

5. 결과 세부 정보를 보려면 계층 트리를 확장 합니다.

## <a name="add-remove-and-rearrange-data-columns"></a>데이터 열 추가, 제거 및 다시 정렬

**코드 메트릭 결과** 창에서 결과 열을 추가 하거나 제거할 수 있습니다. 또한 결과 열을 원하는 순서로 표시 되도록 다시 정렬할 수 있습니다.

### <a name="add-or-remove-a-column"></a>열 추가 또는 제거

1. **열 추가/제거** 단추를 클릭 하거나 열 머리글을 마우스 오른쪽 단추로 클릭 한 다음 **열 추가/제거**를 클릭 합니다.

1. **열 추가/제거** 대화 상자에서 추가 또는 제거할 열의 확인란을 선택 하거나 선택 취소 한 다음 **확인**을 선택 합니다.

### <a name="rearrange-columns"></a>열 다시 정렬

1. **열 추가/제거** 단추를 클릭 합니다.

1. **열 추가/제거** 대화 상자에서 이동할 열을 선택 하 고 위쪽 화살표 또는 아래쪽 화살표를 선택 합니다.

1. 원하는 위치에 열을 배치 하는 경우 **확인**을 선택 합니다.

## <a name="copy-data-to-the-clipboard-or-excel"></a>데이터를 클립보드 또는 Excel로 복사

선택한 코드 메트릭 데이터 행을 선택 하 고 각 데이터 열의 이름 및 값에 대 한 한 줄이 포함 된 텍스트 문자열로 클립보드에 복사할 수 있습니다. **Microsoft excel에서 선택 영역 열기** 를 클릭 하 여 모든 코드 메트릭 결과를 Excel 스프레드시트로 내보낼 수도 있습니다.

## <a name="create-a-work-item-based-on-code-metric-results"></a>코드 메트릭 결과를 기준으로 작업 항목 만들기

**코드 메트릭 결과** 창에서 결과를 기반으로 하는 [Azure Boards](/azure/devops/boards/index?view=vsts) 작업 항목을 만들 수 있습니다. 작업 항목을 만들 때 Visual Studio는 자동으로 **제목** 필드에 제목을 입력 하 고 **기록** 탭에 코드 메트릭 데이터를 입력 합니다.

작업 항목을 Azure Boards 하는 방법에 대 한 자세한 내용은 [작업 항목](/azure/devops/boards/work-items/index?view=vsts)을 참조 하세요.

### <a name="to-create-a-work-item-based-on-a-result"></a>결과를 기준으로 작업 항목을 만들려면

1. 결과를 마우스 오른쪽 단추로 클릭 합니다.

2. **작업 항목 만들기**를 가리킨 다음 만들려는 작업 항목의 형식 (**버그**, **작업**등)을 클릭 합니다.

3. 모든 필수 필드를 입력 하 여 작업 항목 폼을 완료 합니다.

4. **파일** 메뉴에서 **모두 저장** 을 클릭 하 여 작업 항목을 저장 합니다.

### <a name="to-create-a-bug-based-on-a-result"></a>결과를 기반으로 버그를 만들려면

1. 결과를 클릭 하 여 선택 합니다.

2. **작업 항목 만들기** 단추를 클릭 합니다.

3. 모든 필수 필드를 입력 하 여 작업 항목 폼을 완료 합니다.

4. **파일** 메뉴에서 **모두 저장** 을 클릭 하 여 작업 항목을 저장 합니다.

## <a name="see-also"></a>추가 정보

- [코드 메트릭 값](../code-quality/code-metrics-values.md)
- [방법: 코드 메트릭 데이터 생성](../code-quality/how-to-generate-code-metrics-data.md)
