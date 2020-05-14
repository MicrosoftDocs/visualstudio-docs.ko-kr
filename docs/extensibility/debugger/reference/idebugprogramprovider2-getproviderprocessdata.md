---
title: IDebugProgramProvider2::GetProviderProcessData | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramProvider2::GetProviderProcessData
helpviewer_keywords:
- IDebugProgramProvider2::GetProviderProcessData
ms.assetid: 90cf7b7f-53d2-487e-b793-94501a6e24dd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4e958900307f5f7915f58679709c88f80c2abfc9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721834"
---
# <a name="idebugprogramprovider2getproviderprocessdata"></a>IDebugProgramProvider2::GetProviderProcessData
지정된 프로세스에서 실행 중인 프로그램 목록을 검색합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetProviderProcessData(
   PROVIDER_FLAGS         Flags,
   IDebugDefaultPort2*    pPort,
   AD_PROCESS_ID          processId,
   CONST_GUID_ARRAY       EngineFilter,
   PROVIDER_PROCESS_DATA* pProcess
);
```

```csharp
int GetProviderProcessData(
   enum_PROVIDER_FLAGS     Flags,
   IDebugDefaultPort2      pPort,
   AD_PROCESS_ID           ProcessId,
   CONST_GUID_ARRAY        EngineFilter,
   PROVIDER_PROCESS_DATA[] pProcess
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
|`PFLAG_GET_PROGRAM_NODES`|호출자는 반환할 프로그램 노드 목록을 요청합니다.|

`pPort`\
【인】 호출 프로세스가 실행 중인 포트입니다.

`processId`\
【인】 해당 프로그램이 포함된 프로세스의 ID를 보유한 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) 구조입니다.

`EngineFilter`\
【인】 이 프로세스를 디버깅하기 위해 할당된 디버그 엔진에 대한 GUID 배열(제공된 엔진이 지원하는 내용에 따라 실제로 반환되는 프로그램을 필터링하는 데 사용됩니다. 엔진이 지정되지 않은 경우 모든 프로그램이 반환됩니다).

`pProcess`\
【아웃】 요청된 정보로 채워진 [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md) 구조입니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 이 메서드는 일반적으로 해당 프로세스에서 실행 중인 프로그램 목록을 가져오는 프로세스에서 호출됩니다. 반환된 정보는 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) 개체의 목록입니다.

## <a name="see-also"></a>참조
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
- [CONST_GUID_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md)
- [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)
- [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
