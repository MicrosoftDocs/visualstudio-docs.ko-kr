---
title: 방법 - 성능 데이터 파일 비교 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vsperf.choosediffbinaries
helpviewer_keywords:
- profiling tools, how to compare profiler result files
- profiler result files, how to compare
ms.assetid: 1905b45d-c6b3-43c8-87b1-1aee734f37f9
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 5fdb8057823732503a215fb4f2c12ebee33b34c4
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85330820"
---
# <a name="how-to-compare-performance-data-files"></a>방법: 성능 데이터 파일 비교
비교(“Diff”) 보고서 또는 뷰를 만들어 두 가지 프로파일러 데이터 파일(.*vsp* 또는 .*vsps*)의 결과를 비교할 수 있습니다. 이 비교는 프로파일링 세션 사이에 발생한 차이점, 성능 회귀 및 향상된 기능을 보여 줍니다.

 Diff 보고서는 데이터의 테이블 뷰를 제공합니다. 테이블은 델타 또는 기준선으로부터 변경을 표시합니다. 이는 이전 값, 기준 값, 새 분석의 결과 값 간의 차이를 확인하여 계산됩니다.

 프로파일러 데이터의 비교는 코드의 함수, 애플리케이션의 모듈, 줄, IP(명령 포인터) 및 형식에 따라 달라질 수 있습니다.

 노이즈를 줄이고, 지정된 크기만큼 변경되지 않은 행의 테이블 뷰에서 임의의 데이터를 필터링하도록 임계값을 설정할 수 있습니다.

### <a name="to-create-comparison-file-view-for-a-project-in-performance-explorer"></a>[성능 탐색기]에서 프로젝트에 대한 비교 파일 뷰를 만들려면

1. **성능 탐색기**의 **보고서** 아래에서 비교를 위한 기준선 값으로 사용할 .*vsp* 또는 .*vsps* 보고서 파일을 선택합니다.

2. 비교할 .*vsp* 또는 .*vsps* 보고서 파일을 선택합니다.

3. 선택한 파일을 마우스 오른쪽 단추로 클릭하고 **보고서 비교**를 클릭합니다.

### <a name="to-compare-values"></a>값을 비교하려면

1. [보고서 뷰] 창에서 **비교 보고서** 탭을 선택합니다.

2. **테이블** 드롭다운 목록에서 비교할 함수 또는 모듈을 선택합니다.

3. **열** 드롭다운 목록에서 비교할 값을 선택합니다.

4. (선택 사항) **Threshold**에 대한 값을 입력합니다.

5. **적용**을 클릭합니다.

### <a name="to-compare-report-files"></a>보고서 파일을 비교하려면

1. **분석** 메뉴에서 **성능 보고서 비교**를 선택합니다.

2. **비교할 분석 파일을 선택합니다.** 창에서 **기본 파일** 분석 파일(.*vsp* 또는 .*vsps*) 및 **비교 파일**(.*vsp* 또는 .*vsps*)을 선택합니다.

3. **확인**을 클릭합니다.
