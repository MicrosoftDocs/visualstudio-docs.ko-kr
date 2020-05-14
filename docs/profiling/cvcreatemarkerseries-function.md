---
title: CvCreateMarkerSeries 함수 | Microsoft 문서
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkers/CvCreateMarkerSeriesA
- cvmarkers/CvCreateMarkerSeriesW
helpviewer_keywords:
- CvCreateMarkerSeriesA method
- CvCreateMarkerSeriesW method
ms.assetid: e280530b-137a-43a7-8643-aa514ab86ed7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eb3ef4d928aaac57f39a48e5be212c1148ef58eb
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62552683"
---
# <a name="cvcreatemarkerseries-function"></a>CvCreateMarkerSeries 함수
지정된 공급자에 대한 표식 계열을 만듭니다.

## <a name="syntax"></a>구문

```C
_Check_return_ HRESULT CvCreateMarkerSeriesW(
    _In_ PCV_PROVIDER  pProvider,
    _In_ LPCWSTR pSeriesName,
    _Out_ PCV_MARKERSERIES* ppMarkerSeries);

_Check_return_ HRESULT CvCreateMarkerSeriesA(
    _In_ PCV_PROVIDER  pProvider,
    _In_ LPCSTR pSeriesName,
    _Out_ PCV_MARKERSERIES* ppMarkerSeries);
```

#### <a name="parameters"></a>매개 변수
 `pProvider` 이전에 CvInitProvider에서 초기화한 공급자 개체입니다. NULL일 수 없습니다.

 `pSeriesName` 표식 계열 이름입니다. NULL일 수 없지만 빈 문자열을 사용할 수 있습니다.

 `ppMarkerSeries` 표식 계열 컨텍스트를 저장할 출력 변수의 주소입니다. NULL일 수 없습니다.

## <a name="return-value"></a>반환 값
 표식 계열이 성공적으로 생성된 경우 S_OK이고, 오류가 발생한 경우 오류 코드입니다. SUCCEEDED/FAILED 매크로를 사용하여 오류 조건을 확인할 수 있습니다.

## <a name="requirements"></a>요구 사항
 **헤더:** *cvmarkers.h*

 **유니코드:** CvCreateMarkerSeriesW

 **ANSI:** CvCreateMarkerSeriesA

## <a name="see-also"></a>참조
- [C++ 라이브러리 참조](../profiling/cpp-library-reference.md)