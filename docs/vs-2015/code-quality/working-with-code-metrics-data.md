---
title: 코드 메트릭 데이터 작업 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codemetrics.output
helpviewer_keywords:
- code metrics results
- code metrics results window
- results window, code metrics
ms.assetid: 988193ec-b4a3-4e11-b5a1-7334979807d5
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3c2460b4e8b9e0b9043178989fcf8825815471be
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72645700"
---
# <a name="working-with-code-metrics-data"></a>코드 메트릭 데이터 작업
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**코드 메트릭 결과** 창에는 코드 메트릭 분석에 의해 생성 된 데이터가 표시 됩니다. 코드 메트릭 데이터 값에 대 한 자세한 내용은 [코드 메트릭 값](../code-quality/code-metrics-values.md)을 참조 하세요.

 이 항목에는 다음과 같은 섹션이 포함되어 있습니다.

- [코드 메트릭 결과 창](../code-quality/working-with-code-metrics-data.md#BKMK_CodeMetricsResultsWindow)

- [코드 메트릭 결과 표시](../code-quality/working-with-code-metrics-data.md#BKMK_DisplayingCodeMetricsResults)

- [코드 메트릭 결과 필터링](../code-quality/working-with-code-metrics-data.md#BKMK_FilteringCodeMetricsResults)

- [데이터 열 추가, 제거 및 다시 정렬](../code-quality/working-with-code-metrics-data.md#BKMK_AddingRemovingandRearrangingDataColumns)

- [클립보드 또는 Excel로 데이터 복사](../code-quality/working-with-code-metrics-data.md#BKMK_Copying_Data_to_the_Clipboard_or_Excel)

- [코드 메트릭 결과를 기준으로 작업 항목 만들기](../code-quality/working-with-code-metrics-data.md#BKMK_Creating_a_Work_Item_Based_on_Code_Metric_Results)

## <a name="code-metrics-results-window"></a><a name="BKMK_CodeMetricsResultsWindow"></a> Code Metrics Results Window
 **코드 메트릭 결과** 창에는 계산 된 결과를 표시할 위쪽 및 열에 도구 모음이 있습니다.

|열|설명|
|------------|-----------------|
|**계층**|**계층 구조** 열에는 확장 하거나 축소 하 여 원하는 세부 수준을 볼 수 있는 코드 계층 구조에 대 한 트리 뷰가 포함 되어 있습니다. 나머지 열에는 계산 된 결과가 표시 됩니다. 원하는 대로 결과 열을 숨기 거 나 정렬할 수 있습니다.|
|**유지 관리**|**유지 관리** 열에는 숫자 결과와 함께 아이콘이 포함 되어 있습니다. 녹색 아이콘은 상대적으로 높은 유지 관리 수준을 나타냅니다. 노란색 아이콘은 유지 관리 용이성 수준을 나타냅니다. 빨간색 아이콘은 낮은 유지 관리와 잠재적인 문제를 나타냅니다. 이러한 색 표시기는 FxCop 규칙 AvoidUnmaintainableCode에서 사용 하는 심각도 범주에 해당 합니다. 이 규칙은 유지 관리 인덱스가 10 보다 낮으면 오류가 발생 하 고 인덱스가 10에서 20 사이인 경우에는 경고를 발생 하 고 인덱스가 20 보다 크면 오류나 경고를 발생 하지 않습니다. 유지 관리 인덱스는 순환 복잡성, 코드 줄 및 계산 복잡성의 세 가지 메트릭을 합성 한 것입니다. 해당 값은 단위로 표현 되지 않습니다.|

## <a name="displaying-code-metrics-results"></a><a name="BKMK_DisplayingCodeMetricsResults"></a> 코드 메트릭 결과 표시
 코드 메트릭 결과 창은 코드 메트릭 결과를 생성할 때 자동으로 표시 됩니다. 언제 든 지 창을 표시할 수도 있습니다.

#### <a name="to-display-the-code-metrics-results-window"></a>코드 메트릭 결과 창을 표시 하려면

- **분석** 메뉴에서 **창** 을 클릭 한 다음 **코드 메트릭 결과**를 클릭 합니다.

     \- 또는 -

- **보기** 메뉴에서 **다른 창** 을 가리킨 다음 **코드 메트릭 결과**를 클릭 합니다.

     코드 메트릭 결과 창은 결과가 포함 되지 않은 경우에도 표시 됩니다.

#### <a name="to-view-code-metrics-details"></a>코드 메트릭 세부 정보를 보려면

- 코드 메트릭 결과가 생성 된 경우 **계층** 열에서 트리를 확장 합니다.

## <a name="filtering-code-metrics-results"></a><a name="BKMK_FilteringCodeMetricsResults"></a> 코드 메트릭 결과 필터링
 위쪽의 도구 모음을 사용 하 여 **코드 메트릭 결과** 창에 표시 되는 결과를 필터링 할 수 있습니다. 예를 들어 유지 관리 인덱스가 65 미만인 결과만 표시 하려는 경우가 있습니다.

 **필터** 드롭다운 상자에는 결과 열의 이름이 포함 됩니다. 필터가 정의 되 면 들여쓰기를 사용 하 여 목록의 맨 아래에 추가 됩니다. 이 목록에는 정의 된 마지막 필터 10 개가 포함 될 수 있습니다.

#### <a name="to-filter-the-code-metrics-results"></a>코드 메트릭 결과를 필터링 하려면

1. **필터** 목록에서 열 이름을 선택 합니다.

2. **최소값**에 표시 되는 최소값을 입력 합니다.

3. **최대**값에 표시 될 최대값을 입력 합니다.

4. **필터 적용** 단추를 클릭 합니다.

5. 결과 세부 정보를 보려면 계층 트리를 확장 합니다.

## <a name="adding-removing-and-rearranging-data-columns"></a><a name="BKMK_AddingRemovingandRearrangingDataColumns"></a> 데이터 열 추가, 제거 및 다시 정렬
 **코드 메트릭 결과** 창에서 결과 열을 추가 하거나 제거할 수 있습니다. 또한 결과 열을 원하는 순서로 표시 되도록 다시 정렬할 수 있습니다.

#### <a name="to-remove-a-column"></a>열을 제거 하려면

1. **열 추가/제거** 단추를 클릭 합니다.

     \- 또는 -

     열 머리글을 마우스 오른쪽 단추로 클릭 한 다음 **열 추가/제거**를 클릭 합니다.

2. **열 추가/제거** 대화 상자에서 제거 하려는 열에 대 한 확인란의 선택을 취소 한 다음 **확인**을 클릭 합니다.

#### <a name="to-add-a-previously-removed-column"></a>이전에 제거한 열을 추가 하려면

1. **열 추가/제거** 단추를 클릭 합니다.

     \- 또는 -

     열 머리글을 마우스 오른쪽 단추로 클릭 한 다음 **열 추가/제거**를 클릭 합니다.

2. **열 추가/제거** 대화 상자에서 추가 하려는 열의 확인란을 선택한 다음 **확인**을 클릭 합니다.

#### <a name="to-rearrange-columns"></a>열을 다시 정렬 하려면

1. **열 추가/제거** 단추를 클릭 합니다.

     \- 또는 -

     열 머리글을 마우스 오른쪽 단추로 클릭 한 다음 **열 추가/제거**를 클릭 합니다.

2. **열 추가/제거** 대화 상자에서 이동할 열을 선택 하 고 위쪽 화살표 또는 아래쪽 화살표를 클릭 합니다.

3. 원하는 위치에 열을 배치 하려면 **확인**을 클릭 합니다.

## <a name="copying-data-to-the-clipboard-or-excel"></a><a name="BKMK_Copying_Data_to_the_Clipboard_or_Excel"></a> 클립보드 또는 Excel로 데이터 복사
 선택한 코드 메트릭 데이터 행을 선택 하 고 각 데이터 열의 이름 및 값에 대 한 한 줄이 포함 된 텍스트 문자열로 클립보드에 복사할 수 있습니다. **Microsoft excel에서 목록 열기** 를 클릭 하 여 모든 코드 메트릭 결과를 Excel 스프레드시트로 내보낼 수도 있습니다.

## <a name="creating-a-work-item-based-on-code-metric-results"></a><a name="BKMK_Creating_a_Work_Item_Based_on_Code_Metric_Results"></a> 코드 메트릭 결과를 기준으로 작업 항목 만들기
 [!INCLUDE[esprfound](../includes/esprfound-md.md)] **코드 메트릭 결과** 창에서 결과를 기반으로 작업 항목을 만들 수 있습니다. 작업 항목을 만들면에서 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 자동으로 제목 필드에 제목을 입력 하 **Title** 고 **기록** 탭에 코드 메트릭 데이터를 입력 합니다.

 작업 항목을 만드는 방법에 대 한 자세한 내용은 [리디렉션된&#93;작업 항목 &#91;만들기 ](https://msdn.microsoft.com/24b2e064-16ac-4bf0-8de4-98a1f48b8c4b)를 참조 하세요.

#### <a name="to-create-a-work-item-based-on-a-result"></a>결과를 기준으로 작업 항목을 만들려면

1. 결과를 마우스 오른쪽 단추로 클릭 합니다.

2. **작업 항목 만들기**를 가리킨 다음 만들려는 작업 항목의 형식 (**버그**, **작업**등)을 클릭 합니다.

3. 모든 필수 필드를 입력 하 여 작업 항목 폼을 완료 합니다.

4. **파일** 메뉴에서 **모두 저장** 을 클릭 하 여 작업 항목을 저장 합니다.

#### <a name="to-create-a-bug-based-on-a-result"></a>결과를 기반으로 버그를 만들려면

1. 결과를 클릭 하 여 선택 합니다.

2. **작업 항목 만들기** 단추를 클릭 합니다.

3. 모든 필수 필드를 입력 하 여 작업 항목 폼을 완료 합니다.

4. **파일** 메뉴에서 **모두 저장** 을 클릭 하 여 작업 항목을 저장 합니다.

## <a name="see-also"></a>관련 항목
 [관리 코드의 복잡성 및 유지 관리 용이성 측정](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md) [방법: 코드 메트릭 데이터 생성](../code-quality/how-to-generate-code-metrics-data.md)
