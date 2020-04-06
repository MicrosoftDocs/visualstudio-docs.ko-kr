---
title: 아이디버그프로그램2::겟엔진정보 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetEngineInfo
helpviewer_keywords:
- IDebugProgram2::GetEngineInfo
ms.assetid: 3a4f2dc0-e082-4d8d-aeaf-463ab09d279b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 53f16a3ef6bd1328d73c8a6c71c666968d5564d4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722822"
---
# <a name="idebugprogram2getengineinfo"></a>IDebugProgram2::GetEngineInfo
이 프로그램을 실행하는 디버그 엔진(DE)의 이름과 GUID를 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetEngineInfo( 
   BSTR* pbstrEngine,
   GUID* pguidEngine
);
```

```csharp
int GetEngineInfo( 
   out string pbstrEngine,
   out GUID   pguidEngine
);
```

## <a name="parameters"></a>매개 변수
`pbstrEngine`\
【아웃】 이 프로그램을 실행하는 DE의 이름을 반환합니다.

`pguidEngine`\
【아웃】 이 프로그램을 실행하는 DE의 GUID를 반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 각 DE는 식별을 위해 자체 GUID를 정의합니다.

## <a name="see-also"></a>참조
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
