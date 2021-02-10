---
title: CvCreateDefaultMarkerSeriesOfDefaultProvider 함수 | Microsoft 문서
description: 동시성 시각화 도우미 SDK 함수인 CvCreateDefaultMarkerSeriesOfDefaultProvider(C 라이브러리)의 참조 정보를 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkers/CvCreateDefaultMarkerSeriesOfDefaultProvider
helpviewer_keywords:
- CvCreateDefaultMarkerSeriesOfDefaultProvider method
ms.assetid: 24eb80f8-8fca-4c47-93b5-bb1eb8ffdffd
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 32d7730d36f7e99a2557e764c2adb92862515e24
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99941049"
---
# <a name="cvcreatedefaultmarkerseriesofdefaultprovider-function"></a>CvCreateDefaultMarkerSeriesOfDefaultProvider 함수
기본 공급자의 기본 표식 계열을 만듭니다.

## <a name="syntax"></a>구문

```C
HRESULT CvCreateDefaultMarkerSeriesOfDefaultProvider(
   _Out_ PCV_PROVIDER* ppProvider,
   _Out_ PCV_MARKERSERIES* ppMarkerSeries
);
```

#### <a name="parameters"></a>매개 변수
 `ppProvider` 공급자 개체 변수의 주소입니다. 주소는 NULL일 수 없으며, 변수는 임의의 값을 포함할 수 있습니다.

 `ppMarkerSeries` 표식 계열 개체 변수의 주소입니다. 주소는 NULL일 수 없으며, 변수는 임의의 값을 포함할 수 있습니다.

## <a name="return-value"></a>반환 값
 공급자와 표식 계열이 모두 성공적으로 생성된 경우 S_OK이고, 오류가 발생한 경우 오류 코드입니다. SUCCEEDED/FAILED 매크로를 사용하여 오류 조건을 확인할 수 있습니다.

## <a name="requirements"></a>요구 사항
 **헤더:** *cvmarkers.h*

## <a name="see-also"></a>추가 정보
- [C++ 라이브러리 참조](../profiling/cpp-library-reference.md)