---
title: CvIsEnabled 함수 | Microsoft 문서
description: 동시성 시각화 도우미 SDK 함수인 CvIsEnabled(C 라이브러리)의 참조 정보를 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkers/CvIsEnabledEx
- cvmarkers/CvIsEnabled
helpviewer_keywords:
- CvIsEnabled method
- CvIsEnabledEx method
ms.assetid: 2e4fea6d-758d-4150-8744-6102a1d58c1c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 57f1bb96480fe054c729b11a3fabd311407fa858
ms.sourcegitcommit: d13f7050c873b6284911d1f4acf07cfd29360183
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/22/2021
ms.locfileid: "98686482"
---
# <a name="cvisenabled-function"></a>CvIsEnabled 함수
세션에서 지정된 ETW 공급자를 사용하도록 설정했는지 확인합니다.

## <a name="syntax"></a>구문

```C
HRESULT CvIsEnabled(
   _In_ PCV_PROVIDER pProvider
);
HRESULT CvIsEnabledEx(
   _In_ PCV_PROVIDER pProvider,
   _In_ CV_IMPORTANCE level,
   _In_ int category
);
```

#### <a name="parameters"></a>매개 변수
 `category` 범주.

 `level` 중요도 수준.

 `pProvider` 올바른 공급자 개체. NULL이 될 수 없습니다.

## <a name="return-value"></a>반환 값
 현재 공급자를 사용할 수 있는 경우 S_OK입니다. 현재 공급자를 사용할 수 없는 경우 S_FALSE입니다. 오류가 발생한 경우 오류 코드입니다. FAILED 매크로를 사용하여 오류 조건을 확인한 후 S_OK/S_FALSE를 확인할 수 있습니다.

## <a name="requirements"></a>요구 사항
 **헤더:** *cvmarkers.h*

## <a name="see-also"></a>추가 정보
- [C++ 라이브러리 참조](../profiling/cpp-library-reference.md)