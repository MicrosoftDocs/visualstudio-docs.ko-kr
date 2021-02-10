---
title: CvReleaseProvider 함수 | Microsoft 문서
description: 동시성 시각화 도우미 SDK 함수인 CvReleaseProvider(C 라이브러리)의 참조 정보를 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkers/CvReleaseProvider
helpviewer_keywords:
- CvReleaseProvider method
ms.assetid: 8d74379e-295d-452b-bd5f-0769df387d4f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ae363f1909f169d2d5dc4004a79cfe3c2919bdf3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948233"
---
# <a name="cvreleaseprovider-function"></a>CvReleaseProvider 함수
표식 공급자를 해제합니다. 표식 공급자 해제가 이 공급자의 이전에 만든 표식 계열에 영향을 주지 않습니다. 표식 계열은 CvReleaseMarkerSeries 호출을 통해 별도로 해제해야 합니다. 공급자를 해제하지 못하면 메모리 누수가 발생합니다.

## <a name="syntax"></a>구문

```C
HRESULT CvReleaseProvider(
   _In_ PCV_PROVIDER pProvider
);
```

#### <a name="parameters"></a>매개 변수
 `pProvider` 공급자 컨텍스트입니다. NULL이 될 수 없습니다.

## <a name="return-value"></a>반환 값
 공급자가 성공적으로 해제된 경우 S_OK이고, 오류가 발생한 경우 오류 코드입니다. SUCCEEDED/FAILED 매크로를 사용하여 오류 조건을 확인할 수 있습니다.

## <a name="requirements"></a>요구 사항
 **헤더:** *cvmarkers.h*

## <a name="see-also"></a>추가 정보
- [C++ 라이브러리 참조](../profiling/cpp-library-reference.md)