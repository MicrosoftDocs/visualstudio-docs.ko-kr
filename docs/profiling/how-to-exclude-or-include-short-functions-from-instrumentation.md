---
title: 계측에서 간단한 함수 제외 또는 포함
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- profiling tools, instrument events
- profiling tools, include short functions
- profiling tools, exclude short functions
ms.assetid: eaeead79-aafe-4490-86ff-6ed4cad9c15f
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 4aaae07987f1d3364b064465aa6edff9a4748301
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85329793"
---
# <a name="how-to-exclude-or-include-short-functions-from-instrumentation"></a>방법: 계측에서 간단한 함수 제외 또는 포함
기본적으로 프로파일링 도구는 *작은 함수*를 구현에서 제외합니다. 작은 함수는 함수를 호출하지 않는 간단한 함수입니다. 이러한 작은 함수를 제외하면 계측 오버헤드가 감소하므로 계측 속도가 향상됩니다. 또한 성능 프로파일링 데이터 파일(.*vsp*) 크기가 감소하고 분석에 필요한 시간이 단축됩니다. 작은 함수가 제외되면 작은 함수에 사용되는 시간이 부모 함수의 전용 및 포괄 시간에 포함됩니다. 다음 절차에 설명된 대로 작은 함수를 계측에서 제외하거나 포함할 수 있습니다.

### <a name="to-exclude-or-include-short-functions-from-instrumentation"></a>계측에서 간단한 함수를 제외하거나 포함하려면

1. **성능 탐색기**에서 **성능 세션**을 선택한 다음 마우스 오른쪽 단추를 클릭하고 **속성**을 클릭합니다.

     **속성 페이지** 대화 상자가 표시됩니다.

2. **속성 페이지**에서 **계측** 속성을 클릭합니다.

3. 계측에서 간단한 함수를 제외하려면 **계측에서 간단한 함수 제외**를 선택합니다. 이 값은 기본 설정입니다.

     또는

     계측에 간단한 함수를 포함하려면 **계측에서 간단한 함수 제외**의 선택을 취소합니다.

4. **확인**을 클릭합니다.

## <a name="see-also"></a>참고 항목
- [데이터 수집 제어](../profiling/controlling-data-collection.md)
- [성능 세션 속성](../profiling/performance-session-properties.md)
