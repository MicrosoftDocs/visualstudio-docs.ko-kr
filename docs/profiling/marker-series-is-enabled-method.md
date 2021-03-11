---
description: 모든 세션에서 공급자를 사용하도록 설정했는지 확인합니다.
title: marker_series::is_enabled 메서드 | Microsoft 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkersobj/Concurrency, diagnostic::marker_series::is_enabled
helpviewer_keywords:
- Concurrency, diagnostic::marker_series::is_enabled method
ms.assetid: 8ce4dd50-ca29-4c72-98d6-582693f7d501
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0ce01d71b3fac63062a3f823f1862fd199fa39be
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102223578"
---
# <a name="marker_seriesis_enabled-method"></a>marker_series::is_enabled 메서드
모든 세션에서 공급자를 사용하도록 설정했는지 확인합니다.

## <a name="syntax"></a>구문

```cpp
bool is_enabled();
bool is_enabled(
   marker_importance _Importance,
   int _Category
);
```

#### <a name="parameters"></a>매개 변수
 `_Importance` 중요도 수준.

 `_Category` 범주.

## <a name="return-value"></a>반환 값

## <a name="requirements"></a>요구 사항
 **헤더:** *cvmarkersobj.h*

 **네임스페이스:** Concurrency::diagnostic

## <a name="see-also"></a>추가 정보
- [marker_series 클래스](../profiling/marker-series-class.md)
