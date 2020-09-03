---
title: 'IDebugProgramProvider2:: Getprovider프로그래밍 노드 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramProvider2::GetProviderProgramNode
helpviewer_keywords:
- IDebugProgramProvider2::GetProviderProgramNode
ms.assetid: e62e8e83-acbb-4c52-aedf-ffbd4670db29
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fd8ca7d5120ba20695caef2e9021ee25869df72f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80721799"
---
# <a name="idebugprogramprovider2getproviderprogramnode"></a>IDebugProgramProvider2::GetProviderProgramNode
특정 프로그램의 프로그램 노드를 검색 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetProviderProgramNode(
   PROVIDER_FLAGS       Flags,
   IDebugDefaultPort2*  pPort,
   AD_PROCESS_ID        processId,
   REFGUID              guidEngine,
   UINT64               programId,
   IDebugProgramNode2** ppProgramNode
);
```

```csharp
int GetProviderProgramNode(
   enum_PROVIDER_FLAGS    Flags,
   IDebugDefaultPort2     pPort,
   AD_PROCESS_ID          ProcessId,
   ref Guid               guidEngine,
   ulong                  programId,
   out IDebugProgramNode2 ppProgramNode
);
```

## <a name="parameters"></a>매개 변수
`Flags`\
진행 [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md) 열거형의 플래그 조합입니다. 이 호출에 대 한 일반적인 플래그는 다음과 같습니다.

|플래그|설명|
|----------|-----------------|
|`PFLAG_REMOTE_PORT`|호출자가 원격 컴퓨터에서 실행 되 고 있습니다.|
|`PFLAG_DEBUGGEE`|호출자가 현재 디버깅 되 고 있습니다. 각 노드에 대해 마샬링을 위한 추가 정보가 반환 됩니다.|
|`PFLAG_ATTACHED_TO_DEBUGGEE`|호출자가에 연결 되었지만 디버거에 의해 시작 되지 않았습니다.|

`pPort`\
진행 호출 프로세스가 실행 되 고 있는 포트입니다.

`processId`\
진행 문제의 프로그램을 포함 하는 프로세스의 ID를 포함 하는 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) 구조체입니다.

`guidEngine`\
진행 프로그램이 연결 된 디버그 엔진의 GUID입니다 (있는 경우).

`programId`\
진행 프로그램 노드를 가져올 프로그램의 ID입니다.

`ppProgramNode`\
제한이 요청 된 프로그램 노드를 나타내는 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) 개체입니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="see-also"></a>추가 정보
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
- [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)
- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
