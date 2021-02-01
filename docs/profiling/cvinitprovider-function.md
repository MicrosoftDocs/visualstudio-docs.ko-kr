---
title: CvInitProvider 함수 | Microsoft 문서
description: 동시성 시각화 도우미 SDK 함수인 CvInitProvider(C 라이브러리)의 참조 정보를 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkers/CvInitProvider
helpviewer_keywords:
- CvInitProvider method
ms.assetid: ba1863ad-e35f-4d34-a2f2-5e68957d1915
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0d1b41d9d62bbf5a159ec3a9d60f4e2edf5cc115
ms.sourcegitcommit: d13f7050c873b6284911d1f4acf07cfd29360183
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/22/2021
ms.locfileid: "98686508"
---
# <a name="cvinitprovider-function"></a>CvInitProvider 함수
표식 공급자를 초기화합니다. 여타의 동시성 시각화 도우미 SDK 함수 앞에 호출되어야 합니다.

## <a name="syntax"></a>구문

```C
HRESULT CvInitProvider(
   _In_ const GUID* pGuid,
   _Out_ PCV_PROVIDER* ppProvider
);
```

#### <a name="parameters"></a>매개 변수
 `pGuid` 공급자 guid입니다. NULL이 될 수 없습니다.

 `ppProvider` 공급자 컨텍스트를 저장할 출력 변수의 주소입니다. NULL이 될 수 없습니다.

## <a name="return-value"></a>반환 값
 공급자가 성공적으로 초기화된 경우 S_OK이고, 오류가 발생한 경우 오류 코드입니다. SUCCEEDED/FAILED 매크로를 사용하여 오류 조건을 확인할 수 있습니다.

## <a name="requirements"></a>요구 사항
 **헤더:** *cvmarkers.h*

## <a name="see-also"></a>추가 정보
- [C++ 라이브러리 참조](../profiling/cpp-library-reference.md)