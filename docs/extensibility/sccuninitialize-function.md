---
title: SccUninitialize 기능 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccUninitialize
helpviewer_keywords:
- SccUninitialize function
ms.assetid: 17cf5337-d251-4422-bc96-93fe7d48f2ae
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c4706ddf28949af4fe1bba01c32b2c64c9156d51
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700238"
---
# <a name="sccuninitialize-function"></a>SccUninitialize 함수
이 함수는 소스 제어 플러그인을 종료하기 위해 [SccInitialize에](../extensibility/sccinitialize-function.md) 대한 이전 호출에서 만든 모든 할당 또는 열린 연결을 정리합니다.

## <a name="syntax"></a>구문

```cpp
SCCRTN SccUninitialize (
   LPVOID pvContext
);
```

#### <a name="parameters"></a>매개 변수
 pvContext

【인】 [SccInitialize에서](../extensibility/sccinitialize-function.md)만든 소스 제어 플러그인 컨텍스트 구조에 대한 포인터입니다.

## <a name="return-value"></a>Return Value
 이 함수의 소스 제어 플러그인 구현은 다음 값 중 하나를 반환해야 합니다.

|값|Description|
|-----------|-----------------|
|SCC_OK|정리가 성공적으로 완료되었습니다.|

## <a name="remarks"></a>설명
 소스 제어 플러그인은 종료할 준비를 하고 플러그인이 컨텍스트 구조에 할당한 메모리를 확보하는 것을 담당합니다. 이 함수는 플러그인의 각 지정된 인스턴스에 대해 한 번 호출됩니다. 이 호출 앞에 [SccInitialize에](../extensibility/sccinitialize-function.md) 대한 호출이 옵니다. 을 호출할 때 에도 열려 있는 `SccUninitialize`프로젝트는 없습니다.

## <a name="see-also"></a>참조
- [소스 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)
