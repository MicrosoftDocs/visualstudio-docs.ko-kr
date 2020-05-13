---
title: SccQuery변경 기능 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccQueryChanges
helpviewer_keywords:
- SccQueryChanges function
ms.assetid: 4cd58eb3-6952-49b1-9620-8682e3eaa604
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ec335d808c287decb75bf759d5a3795d98962579
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700491"
---
# <a name="sccquerychanges-function"></a>SccQueryChanges 함수
이 함수는 지정된 파일 목록을 열거하여 콜백 함수를 통해 각 파일의 이름 변경에 대한 정보를 제공합니다.

## <a name="syntax"></a>구문

```cpp
SCCRTN SccQueryChanges(
   LPVOID           pContext,
   LONG             nFiles,
   LPCSTR*          lpFileNames,
   QUERYCHANGESFUNC pfnCallback,
   LPVOID           pvCallerData
);
```

#### <a name="parameters"></a>매개 변수
 pContext

【인】 소스 제어 플러그인 컨텍스트 포인터입니다.

 n파일

【인】 `lpFileNames` 배열의 파일 수입니다.

 lpFile 이름

【인】 에 대한 정보를 얻을 수있는 파일 이름의 배열.

 pfnCallback

【인】 콜백 함수는 목록의 각 파일 이름을 호출합니다(자세한 내용은 [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md) 참조).

 pvCallerData

【인】 콜백 함수에 변경되지 않고 전달되는 값입니다.

## <a name="return-value"></a>Return Value
 이 함수의 소스 제어 플러그인 구현은 다음 값 중 하나를 반환해야 합니다.

|값|Description|
|-----------|-----------------|
|SCC_OK|쿼리 프로세스가 성공적으로 완료되었습니다.|
|SCC_E_PROJNOTOPEN|소스 제어에서 프로젝트가 열리지 않았습니다.|
|SCC_E_ACCESSFAILURE|네트워크 또는 경합 문제로 인해 소스 제어 시스템에 액세스하는 데 문제가 있었습니다.|
|SCC_E_NONSPECIFICERROR|지정되지 않았거나 일반적인 오류가 발생했습니다.|

## <a name="remarks"></a>설명
 쿼리되는 변경 사항은 네임스페이스, 특히 파일 이름 바꾸기, 추가 및 제거입니다.

## <a name="see-also"></a>참조
- [소스 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)
- [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)
- [오류 코드](../extensibility/error-codes.md)
