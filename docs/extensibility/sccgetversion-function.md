---
title: SccGetVersion 기능 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetVersion
helpviewer_keywords:
- SccGetVersion function
ms.assetid: a6e786bf-744e-4272-9e21-0be44d23b1a1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a563a7d1d65dc4c6564abd4e337242eea1aa9924
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700670"
---
# <a name="sccgetversion-function"></a>SccGetVersion 함수
이 함수는 소스 제어 플러그인에서 지원하는 소스 제어 플러그인 API의 버전 번호를 가져옵니다.

## <a name="syntax"></a>구문

```cpp
LONG SccGetVersion(void);
```

#### <a name="parameters"></a>매개 변수
 없음

## <a name="return-value"></a>Return Value
 지원되는 소스 제어 플러그인 API의 버전 번호를 포함하는 `LONG` 데이터 형식:

|WORD|설명|
|----------|-----------------|
|하이워드 (오)와|주 버전|
|로워드 (주)|부 버전|

## <a name="remarks"></a>설명
 예를 들어 소스 제어 플러그인이 소스 제어 플러그인 API의 버전 1.3을 지원하는 경우 이 함수는 0x0103을 반환합니다.

## <a name="see-also"></a>참조
- [소스 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)
