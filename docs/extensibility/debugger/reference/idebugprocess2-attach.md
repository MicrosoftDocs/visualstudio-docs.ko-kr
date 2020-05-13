---
title: IDebugProcess2::연결 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::Attach
helpviewer_keywords:
- IDebugProcess2::Attach
ms.assetid: 40d78417-fde2-45c3-96c9-16e06bd9008d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fb6ea896285c784021402400597ba168f6ccf716
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724187"
---
# <a name="idebugprocess2attach"></a>IDebugProcess2::Attach
세션 디버그 관리자(SDM)를 프로세스에 연결합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT Attach( 
   IDebugEventCallback2* pCallback,
   GUID*                 rgguidSpecificEngines,
   DWORD                 celtSpecificEngines,
   HRESULT*              rghrEngineAttach
);
```

```csharp
int Attach( 
   IDebugEventCallback2 pCallback,
   Guid[]               rgguidSpecificEngines,
   uint                 celtSpecificEngines,
   int[]                rghrEngineAttach
);
```

## <a name="parameters"></a>매개 변수
`pCallback`\
【인】 디버그 이벤트 알림에 사용되는 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 개체입니다.

`rgguidSpecificEngines`\
【인】 프로세스에서 실행 중인 프로그램을 디버깅하는 데 사용할 디버그 엔진의 GUID 배열입니다. 이 매개 변수는 null 값이 될 수 있습니다. 자세한 내용은 비고를 참조하십시오.

`celtSpecificEngines`\
【인】 `rgguidSpecificEngines` 배열의 디버그 엔진 수와 `rghrEngineAttach` 배열의 크기입니다.

`rghrEngineAttach`\
【인, 아웃】 디버그 엔진에서 반환되는 HRESULT 코드 의 배열입니다. 이 배열의 크기는 매개 `celtSpecificEngines` 변수에 지정됩니다. 각 코드는 `S_OK` 일반적으로 `S_ATTACH_DEFERRED`또는 . 후자는 DE가 현재 프로그램에 연결되어 있지 않음을 나타냅니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다. 다음 표에서는 다른 가능한 값을 보여 주며 있습니다.

|값|Description|
|-----------|-----------------|
|`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`|지정된 프로세스가 디버거에 이미 연결되어 있습니다.|
|`E_ATTACH_DEBUGGEE_PROCESS_SECURITY_VIOLATION`|연결 절차 중에 보안 위반이 발생했습니다.|
|`E_ATTACH_CANNOT_ATTACH_TO_DESKTOP`|데스크톱 프로세스를 디버거에 연결할 수 없습니다.|

## <a name="remarks"></a>설명
 프로세스에 연결하면 배열에 지정된 DE(디버그 엔진)에서 디버깅할 수 있는 해당 프로세스에서 실행중인 모든 프로그램에 SDM이 `rgguidSpecificEngines` 연결됩니다. 매개 `rgguidSpecificEngines` 변수를 null 값으로 `GUID_NULL` 설정하거나 프로세스의 모든 프로그램에 연결할 배열에 포함합니다.

 프로세스에서 발생하는 모든 디버그 이벤트는 지정된 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 개체로 전송됩니다. 이 `IDebugEventCallback2` 개체는 SDM에서 이 메서드를 호출할 때 제공됩니다.

## <a name="see-also"></a>참조
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
