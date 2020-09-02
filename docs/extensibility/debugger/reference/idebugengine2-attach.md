---
title: 'IDebugEngine2:: Attach | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80731210"
---
# <a name="idebugengine2attach"></a>IDebugEngine2::Attach
프로그램 또는 프로그램에 디버그 엔진 (DE)을 연결 합니다. DE-DE가 in-process로 실행 중인 경우 세션 디버그 관리자 (SDM)에 의해 호출 됩니다.

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
진행 연결할 프로그램을 나타내는 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 개체의 배열입니다. 이러한 프로그램은 포트 프로그램입니다.

`rgpProgramNodes`\
진행 각 프로그램에 대해 하나씩, 프로그램 노드를 나타내는 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) 개체의 배열입니다. 이 배열의 프로그램 노드는와 같은 프로그램을 나타냅니다 `pProgram` . 프로그램 노드가 제공 되므로 DE가 연결할 프로그램을 식별할 수 있습니다.

`celtPrograms`\
진행 및 배열의 프로그램 및/또는 프로그램 노드 수 `pProgram` `rgpProgramNodes` 입니다.

`pCallback`\
진행 SDM에 디버그 이벤트를 보내는 데 사용 되는 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) 개체입니다.

`dwReason`\
진행 이러한 프로그램을 연결 하는 이유를 지정 하는 [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) 열거형의 값입니다. 자세한 내용은 설명 섹션을 참조하세요.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 프로그램에 연결 하는 데는 다음과 같은 세 가지 이유가 있습니다.

- `ATTACH_REASON_LAUNCH` 사용자가이를 포함 하는 프로세스를 시작 했기 때문에 DE가 프로그램에 연결 됨을 나타냅니다.

- `ATTACH_REASON_USER` 사용자가 프로그램 (또는 프로그램을 포함 하는 프로세스)에 연결 하기 위해 명시적으로 DE를 요청 했음을 나타냅니다.

- `ATTACH_REASON_AUTO` 특정 프로세스에서 다른 프로그램을 이미 디버깅 하 고 있으므로 DE가 특정 프로그램에 연결 되어 있음을 나타냅니다. 이를 자동 연결이 라고도 합니다.

  이 메서드가 호출 되 면 DE는 이러한 이벤트를 순서 대로 전송 해야 합니다.

1. [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) (디버그 엔진의 특정 인스턴스에 대해 아직 전송 되지 않은 경우)

2. [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)

3. [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)

   또한 연결에 대 한 이유가 인 경우 `ATTACH_REASON_LAUNCH` DE는 [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) 이벤트를 전송 해야 합니다.

   디버그 중인 프로그램에 해당 하는 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) 개체를 제거 하면 전용 인터페이스에 대해 쿼리할 수 있습니다.

   또는에 지정 된 배열에서 프로그램 노드의 메서드를 호출 하기 전에 `pProgram` , `rgpProgramNodes` 필요한 경우 가장을 사용 하도록 설정 해야 합니다 `IDebugProgram2` . 그러나 일반적으로이 단계는 필요 하지 않습니다. 자세한 내용은 [보안 문제](../../../extensibility/debugger/security-issues.md)를 참조 하세요.

## <a name="see-also"></a>추가 정보
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md)
- [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)
- [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)
- [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)
- [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)
