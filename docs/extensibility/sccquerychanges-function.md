---
title: SccQueryChanges 함수 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80700491"
---
# <a name="sccquerychanges-function"></a>SccQueryChanges 함수
이 함수는 지정 된 파일 목록을 열거 하 고 콜백 함수를 통해 각 파일의 이름 변경에 대 한 정보를 제공 합니다.

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

진행 소스 제어 플러그 인 컨텍스트 포인터입니다.

 n

진행 배열에 있는 파일 수 `lpFileNames` 입니다.

 lpFileNames 이름

진행 정보를 가져올 파일 이름 배열입니다.

 pfnCallback

진행 목록에서 각 파일 이름에 대해 호출할 콜백 함수입니다 (자세한 내용은 [querydetails func](../extensibility/querychangesfunc.md) 참조).

 pvCallerData

진행 변경 되지 않은 상태로 콜백 함수로 전달 되는 값입니다.

## <a name="return-value"></a>반환 값
 이 함수의 소스 제어 플러그 인 구현은 다음 값 중 하나를 반환 해야 합니다.

|값|설명|
|-----------|-----------------|
|SCC_OK|쿼리 프로세스가 완료 되었습니다.|
|SCC_E_PROJNOTOPEN|프로젝트가 소스 제어에서 열려 있지 않습니다.|
|SCC_E_ACCESSFAILURE|네트워크 또는 경합 문제로 인해 원본 제어 시스템에 액세스 하는 동안 문제가 발생 했습니다.|
|SCC_E_NONSPECIFICERROR|지정 되지 않았거나 일반 오류가 발생 했습니다.|

## <a name="remarks"></a>설명
 에 대해 쿼리 하는 변경 내용은 네임 스페이스에 있습니다. 특히 파일 이름 바꾸기, 추가 및 제거를 수행 합니다.

## <a name="see-also"></a>추가 정보
- [소스 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)
- [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)
- [오류 코드](../extensibility/error-codes.md)
