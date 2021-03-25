---
description: 이 메서드는이 중단점 요청을 설명 하는 중단점 요청 정보를 가져옵니다.
title: 'IDebugBreakpointRequest3:: GetRequestInfo2 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointRequest3::GetRequestInfo2
helpviewer_keywords:
- IDebugBreakpointRequest3::GetRequestInfo2
ms.assetid: 33942e4a-0a0a-49e8-a693-004954f6d38a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 46c4984251d7546df5ea82f4c674b8ab849d27c8
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105054441"
---
# <a name="idebugbreakpointrequest3getrequestinfo2"></a>IDebugBreakpointRequest3::GetRequestInfo2
이 메서드는이 중단점 요청을 설명 하는 중단점 요청 정보를 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetRequestInfo2(
   BPREQI_FIELDS      dwFields,
   BP_REQUEST_INFO2*  bBPRequestInfo
);
```

```csharp
int GetRequestInfo2(
   enum_BPREQI_FIELDS  dwFields,
   BP_REQUEST_INFO2[]  bBPRequestInfo
);
```

## <a name="parameters"></a>매개 변수
`dwFields`\
진행 에서 채울 필드를 결정 하는 [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) 열거형의 플래그 조합입니다 `pBPRequestInfo` .

`bBPRequestInfo`\
제한이 채워질 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) 구조체입니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 이 요청에는 [Getrequestinfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md) 메서드에서 반환 된 것 보다 더 많은 정보가 있습니다.

## <a name="see-also"></a>참조
- [IDebugBreakpointRequest3](../../../extensibility/debugger/reference/idebugbreakpointrequest3.md)
- [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
- [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)
