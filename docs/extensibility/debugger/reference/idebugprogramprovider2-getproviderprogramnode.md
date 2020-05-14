---
title: IDebugProgramProvider2::GetproviderProgramNode | 마이크로 소프트 문서
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721799"
---
# <a name="idebugprogramprovider2getproviderprogramnode"></a>IDebugProgramProvider2::GetProviderProgramNode
특정 프로그램에 대한 프로그램 노드를 검색합니다.

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
【인】 [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md) 열거형의 플래그 조합입니다. 다음 플래그는 이 호출의 일반적인 플래그입니다.

|플래그|설명|
|----------|-----------------|
|`PFLAG_REMOTE_PORT`|호출기가 원격 컴퓨터에서 실행되고 있습니다.|
|`PFLAG_DEBUGGEE`|호출자는 현재 디버깅 중입니다(각 노드에 대해 마샬링에 대한 추가 정보가 반환됨).|
|`PFLAG_ATTACHED_TO_DEBUGGEE`|호출자가 연결되었지만 디버거에 의해 시작되지 않았습니다.|

`pPort`\
【인】 호출 프로세스가 실행 중인 포트입니다.

`processId`\
【인】 해당 프로그램이 포함된 프로세스의 ID를 보유한 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) 구조입니다.

`guidEngine`\
【인】 프로그램이 연결된 디버그 엔진의 GUID입니다(있는 경우).

`programId`\
【인】 프로그램 노드를 얻을 수 있는 프로그램의 ID입니다.

`ppProgramNode`\
【아웃】 요청된 프로그램 노드를 나타내는 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) 개체입니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="see-also"></a>참조
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
- [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)
- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
