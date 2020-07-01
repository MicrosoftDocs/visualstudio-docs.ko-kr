---
title: CvInitProvider 함수 | Microsoft 문서
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
ms.openlocfilehash: b06190568454977bfcb54d65db9011fc979f7591
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85329570"
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
 `pGuid` 공급자 guid입니다. NULL일 수 없습니다.

 `ppProvider` 공급자 컨텍스트를 저장할 출력 변수의 주소입니다. NULL일 수 없습니다.

## <a name="return-value"></a>반환 값
 공급자가 성공적으로 초기화된 경우 S_OK이고, 오류가 발생한 경우 오류 코드입니다. SUCCEEDED/FAILED 매크로를 사용하여 오류 조건을 확인할 수 있습니다.

## <a name="requirements"></a>요구 사항
 **헤더:** *cvmarkers.h*

## <a name="see-also"></a>참조
- [C++ 라이브러리 참조](../profiling/cpp-library-reference.md)