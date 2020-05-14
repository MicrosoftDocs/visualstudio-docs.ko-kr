---
title: '방법: 명령 프롬프트에서 프로파일러 비교 보고서 만들기 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 00548d16-eb5b-46f7-8a65-862f98a43831
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: d0328e04067770f8837d10d532abb67d16c65e50
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74776429"
---
# <a name="how-to-create-a-profiler-comparison-report-from-a-command-prompt"></a>방법: 명령 프롬프트에서 프로파일러 비교 보고서 만들기
두 가지 프로파일링 데이터(.*vsp* /또는 .*vsps*) 파일의 성능 데이터를 비교하는 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 프로파일링 도구 보고서를 생성할 수 있습니다. 보고서는 프로파일링 세션 사이에 발생한 차이점, 성능 회귀 및 향상된 기능을 보여 줍니다. 보고서의 값은 지정하는 첫 번째 파일의 기준에서 델타 또는 변경 내용을 제공합니다. 이 델타는 이전 값, 기준 값, 새 분석의 결과 값 간의 차이를 확인하여 계산됩니다. 프로파일러 데이터의 비교는 코드의 함수, 애플리케이션의 모듈, 줄, IP(명령 포인터) 및 형식에 따라 달라질 수 있습니다.

 비교 범주 및 필드의 식별자를 나열하려면 다음 명령줄을 입력합니다.

 **VSPerfReport /querydifftables**  *VspFileName1* *VspFileName2*

 다음 구문을 사용하여 비교 보고서를 만듭니다.

 **VSPerfReport /diff**  `VspFileName1` *VspFileName2* [ **/** `Options`]

 다음 표에서 **VSPerfReport /diff** 명령줄에 옵션을 추가할 수 있습니다.

|옵션|설명|
|------------|-----------------|
|**DiffThreshold:** [*Value*]|이 백분율 임계값보다 낮으면 차이를 무시합니다. 또한 이 임계값보다 낮은 값을 갖는 새 데이터는 표시되지 않습니다.|
|**DiffTable:** *TableName*|이 테이블을 사용하여 파일을 비교합니다. 기본적으로 함수 테이블이 사용됩니다. **VSPerfReport /querydifftables**에 나열된 식별자를 지정합니다.|
|**DiffColumn:** *ColumnName*|이 열을 사용하여 값을 비교합니다. 기본적으로 전용 샘플 백분율 열이 사용됩니다. **VSPerfReport /querydifftables**에 나열된 식별자를 지정합니다.|
