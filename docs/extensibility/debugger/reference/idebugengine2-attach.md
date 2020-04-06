---
title: IDebugEngine2::연결 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::Attach
helpviewer_keywords:
- IDebugEngine2::Attach
ms.assetid: 173dcbda-5019-4c5e-bca9-a071838b5739
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 93890885dbbdfd3cc26984590955681487977200
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731210"
---
# <a name="idebugengine2attach"></a>IDebugEngine2::Attach
디버그 엔진(DE)을 프로그램 또는 프로그램에 연결합니다. DE가 SDM에 프로세스 중 실행 중일 때 세션 디버그 관리자(SDM)에서 호출됩니다.

## <a name="syntax"></a>구문

```cpp
HRESULT Attach( 
   IDebugProgram2**      pProgram,
   IDebugProgramNode2**  rgpProgramNodes,
   DWORD                 celtPrograms,
   IDebugEventCallback2* pCallback,
   ATTACH_REASON         dwReason
);
```

```csharp
int Attach( 
   IDebugProgram2[]     pProgram,
   IDebugProgramNode2[] rgpProgramNodes,
   uint                 celtPrograms,
   IDebugEventCallback2 pCallback,
   Enum_ATTACH_REASON   dwReason
);
```

## <a name="parameters"></a>매개 변수
`pProgram`\
【인】 연결할 프로그램을 나타내는 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 개체의 배열입니다. 포트 프로그램입니다.

`rgpProgramNodes`\
【인】 프로그램 노드를 나타내는 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) 개체의 배열입니다. 이 배열의 프로그램 노드는 에서와 `pProgram`동일한 프로그램을 나타냅니다. DE가 연결할 프로그램을 식별할 수 있도록 프로그램 노드가 제공됩니다.

`celtPrograms`\
【인】 `pProgram` 및 `rgpProgramNodes` 배열의 프로그램 및/또는 프로그램 노드 수입니다.

`pCallback`\
【인】 디버그 이벤트를 SDM에 보내는 데 사용할 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 개체입니다.

`dwReason`\
【인】 이러한 프로그램을 연결하는 이유를 지정하는 [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) 열거형의 값입니다. 자세한 내용은 주의 섹션을 참조하세요.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 다음과 같이 프로그램에 연결하는 데는 세 가지 이유가 있습니다.

- `ATTACH_REASON_LAUNCH`은 사용자가 DE를 포함하는 프로세스를 시작했기 때문에 DE가 프로그램에 연결되고 있음을 나타냅니다.

- `ATTACH_REASON_USER`은 사용자가 DE를 프로그램(또는 프로그램이 포함된 프로세스)에 연결하도록 명시적으로 요청했음을 나타냅니다.

- `ATTACH_REASON_AUTO`은 DE가 특정 프로세스의 다른 프로그램을 이미 디버깅하고 있기 때문에 특정 프로그램에 연결되고 있음을 나타냅니다. 이를 자동 연결이라고도 합니다.

  이 메서드가 호출되면 DE는 다음 이벤트를 순서대로 보내야 합니다.

1. [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) (디버그 엔진의 특정 인스턴스에 대해 아직 전송되지 않은 경우)

2. [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)

3. [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)

   또한 연결 `ATTACH_REASON_LAUNCH`이유가 있는 경우 DE는 [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) 이벤트를 보내야 합니다.

   DE가 디버깅 되는 프로그램에 해당하는 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) 개체를 받으면 모든 개인 인터페이스에 대해 쿼리할 수 있습니다.

   또는 에 `pProgram` `rgpProgramNodes`의해 주어진 배열에서 프로그램 노드의 메서드를 호출하기 전에 , 필요한 `IDebugProgram2` 경우, 프로그램 노드를 나타내는 인터페이스에서 활성화해야합니다. 그러나 일반적으로 이 단계는 필요하지 않습니다. 자세한 내용은 [보안 문제를](../../../extensibility/debugger/security-issues.md)참조하십시오.

## <a name="see-also"></a>참조
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md)
- [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)
- [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)
- [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)
- [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)
