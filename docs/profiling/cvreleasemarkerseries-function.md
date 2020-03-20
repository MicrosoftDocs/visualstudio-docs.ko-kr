---
title: CvReleaseMarkerSeries 함수 | Microsoft 문서
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkers/CvReleaseMarkerSeries
helpviewer_keywords:
- CvReleaseMarkerSeries method
ms.assetid: 3b4711ee-e534-411d-9128-f69cd7932a48
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d100b7ff37ea5a3cd224fd420f14e4cb23061903
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62974145"
---
# <a name="cvreleasemarkerseries-function"></a>CvReleaseMarkerSeries 함수
표식 계열을 해제합니다. 해제한 후에 표식 계열 개체를 사용하지 마세요. 해당 개체를 사용하는 경우 애플리케이션 작동이 중단될 수 있습니다. 표식 계열을 해제하지 못하면 메모리 누수가 발생합니다.

## <a name="syntax"></a>구문

```C
HRESULT CvReleaseMarkerSeries(
   _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries
);
```

#### <a name="parameters"></a>매개 변수
 `pMarkerSeries` 공급자 개체 변수의 주소입니다. 주소는 NULL일 수 없으며, 변수는 임의의 값을 포함할 수 있습니다.

## <a name="return-value"></a>반환 값
 표식 계열이 성공적으로 해제된 경우 S_OK이고, 오류가 발생한 경우 오류 코드입니다. SUCCEEDED/FAILED 매크로를 사용하여 오류 조건을 확인할 수 있습니다.

## <a name="requirements"></a>요구 사항
 **헤더:** *cvmarkers.h*

## <a name="see-also"></a>참조
- [C++ 라이브러리 참조](../profiling/cpp-library-reference.md)