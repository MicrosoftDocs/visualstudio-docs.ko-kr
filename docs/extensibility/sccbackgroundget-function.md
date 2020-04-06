---
title: SccBackgroundGet 기능 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccBackgroundGet
helpviewer_keywords:
- SccBackgroundGet function
ms.assetid: 69817e52-b9ac-4f4d-820b-2cc9c384f0dc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b1c07076b6e257bd5519d19f841797fbc652f0c1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701238"
---
# <a name="sccbackgroundget-function"></a>SccBackgroundGet 함수
이 함수는 사용자 상호 작용 없이 지정된 각 파일을 소스 제어에서 검색합니다.

## <a name="syntax"></a>구문

```cpp
SCCRTN SccBackgroundGet(
   LPVOID  pContext,
   LONG    nFiles,
   LPCSTR* lpFileNames,
   LONG    dwFlags,
   LONG    dwBackgroundOperationID
);
```

### <a name="parameters"></a>매개 변수
 pContext

【인】 소스 제어 플러그인 컨텍스트 포인터입니다.

 n파일

【인】 배열에 지정된 파일 `lpFileNames` 수입니다.

 lpFile 이름

【인, 아웃】 검색할 파일 의 이름 배열입니다.

> [!NOTE]
> 이름은 정규화된 로컬 파일 이름이어야 합니다.

 dwFlags

【인】 명령 플래그`SCC_GET_ALL` `SCC_GET_RECURSIVE`(, ).

 dw배경작업ID

【인】 이 작업과 관련된 고유 값입니다.

## <a name="return-value"></a>반환 값
 이 함수의 소스 제어 플러그인 구현은 다음 값 중 하나를 반환해야 합니다.

|값|Description|
|-----------|-----------------|
|SCC_OK|작업이 완료되었습니다.|
|SCC_E_BACKGROUNDGETINPROGRESS|백그라운드 검색이 이미 진행 중입니다(원본 제어 플러그인은 동시 일괄 처리 작업을 지원하지 않는 경우에만 이 것을 반환해야 합니다).|
|SCC_I_OPERATIONCANCELED|작업이 완료되기 전에 취소되었습니다.|

## <a name="remarks"></a>설명
 이 함수는 항상 소스 제어 플러그인을 로드한 스레드와 다른 스레드에서 호출됩니다. 이 함수는 완료될 때까지 반환되지 않습니다. 그러나 여러 파일 목록과 동시에 여러 번 호출할 수 있습니다.

 인수의 `dwFlags` 사용은 [SccGet](../extensibility/sccget-function.md).

## <a name="see-also"></a>참조
- [소스 제어 플러그인 API 기능](../extensibility/source-control-plug-in-api-functions.md)
- [SccGet](../extensibility/sccget-function.md)
