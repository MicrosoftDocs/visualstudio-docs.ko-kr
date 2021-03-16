---
description: marker_series 클래스의 새 인스턴스를 초기화합니다.
title: marker_series::marker_series 생성자 | Microsoft 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkersobj/Concurrency, diagnostic::marker_series::marker_series
helpviewer_keywords:
- Concurrency, diagnostic::marker_series constructor
ms.assetid: 042c7d23-f1d8-4e09-9e76-a21c30243790
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 88d82c78bc6126f6b3d96b77b39c729c4f452a28
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102223981"
---
# <a name="marker_seriesmarker_series-constructor"></a>marker_series::marker_series 생성자
`marker_series` 클래스의 새 인스턴스를 초기화합니다.

## <a name="syntax"></a>구문

```cpp
marker_series();
marker_series(
   _In_ LPCTSTR _SeriesName
);
marker_series(
   _In_ const GUID* _ProviderGuid
);
marker_series(
   _In_ const GUID* _ProviderGuid,
   _In_ LPCTSTR _SeriesName
);
```

#### <a name="parameters"></a>매개 변수
 `_SeriesName` 만들려는 계열의 이름입니다.

 `_ProviderGuid` 계열 공급자의 GUID입니다.

## <a name="requirements"></a>요구 사항
 **헤더:** *cvmarkersobj.h*

 **네임스페이스:** Concurrency::diagnostic

## <a name="see-also"></a>추가 정보
- [marker_series 클래스](../profiling/marker-series-class.md)
