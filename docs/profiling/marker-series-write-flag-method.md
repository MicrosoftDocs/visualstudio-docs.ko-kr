---
title: marker_series::write_flag 메서드 | Microsoft 문서
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkersojb/Concurrency::diagnostic::marker_series::write_flag
helpviewer_keywords:
- Concurrency::diagnostic::marker_series::write_flag method
ms.assetid: ca07f388-e5d5-46fd-b991-fe6e9029a68f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f09cca9bd1e3babccb0debc369881a0efa00fa0b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62830813"
---
# <a name="marker_serieswrite_flag-method"></a>marker_series::write_flag 메서드
동시성 시각화 도우미 추적 파일에 플래그를 씁니다.

## <a name="syntax"></a>구문

```cpp
void write_flag(
   _In_ LPCTSTR _Format,
   ...
);
void write_flag(
   marker_importance _Importance,
   _In_ LPCTSTR _Format,
   ...
);
void write_flag(
   int _Category,
   _In_ LPCTSTR _Format,
   ...
);
void write_flag(
   marker_importance _Importance,
   int _Category,
   _In_ LPCTSTR _Format,
   ...
);
```

#### <a name="parameters"></a>매개 변수
 `_Format` 인수 목록의 개체에 해당하는 0개 이상의 서식 항목과 결합된 텍스트를 포함하는 합성 서식 문자열입니다.

 `_Importance` 중요도 수준.

 `_Category` 범주.

## <a name="requirements"></a>요구 사항
 **헤더:** *cvmarkersobj.h*

 **네임스페이스:** Concurrency::diagnostic

## <a name="see-also"></a>참조
- [marker_series 클래스](../profiling/marker-series-class.md)