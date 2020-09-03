---
title: 'IDebugProgramProvider2:: GetProviderProcessData | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramProvider2::GetProviderProcessData
helpviewer_keywords:
- IDebugProgramProvider2::GetProviderProcessData
ms.assetid: 90cf7b7f-53d2-487e-b793-94501a6e24dd
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a50faf4531a098dde544adcffe535ed26e9c5cd8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148510"
---
# <a name="idebugprogramprovider2getproviderprocessdata"></a>IDebugProgramProvider2::GetProviderProcessData
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

지정 된 프로세스에서 실행 중인 프로그램의 목록을 검색 합니다.  
  
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
  
#### <a name="parameters"></a>매개 변수  
 `Flags`  
 진행 [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md) 열거형의 플래그 조합입니다. 이 호출에 대 한 일반적인 플래그는 다음과 같습니다.  
  
|플래그|설명|  
|----------|-----------------|  
|`PFLAG_REMOTE_PORT`|호출자가 원격 컴퓨터에서 실행 되 고 있습니다.|  
|`PFLAG_DEBUGGEE`|호출자가 현재 디버깅 되 고 있습니다. 각 노드에 대해 마샬링을 위한 추가 정보가 반환 됩니다.|  
|`PFLAG_ATTACHED_TO_DEBUGGEE`|호출자가에 연결 되었지만 디버거에 의해 시작 되지 않았습니다.|  
|`PFLAG_GET_PROGRAM_NODES`|호출자가 반환할 프로그램 노드 목록을 요청 하 고 있습니다.|  
  
 `pPort`  
 진행 호출 프로세스가 실행 되 고 있는 포트입니다.  
  
 `processId`  
 진행 문제의 프로그램을 포함 하는 프로세스의 ID를 포함 하는 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) 구조체입니다.  
  
 `EngineFilter`  
 진행 이 프로세스를 디버그 하기 위해 할당 된 디버그 엔진의 Guid 배열입니다 .이는 제공 된 엔진이 지 원하는 항목에 따라 실제로 반환 되는 프로그램을 필터링 하는 데 사용 됩니다. 엔진을 지정 하지 않으면 모든 프로그램이 반환 됩니다.  
  
 `pProcess`  
 제한이 요청 된 정보를 사용 하 여 채워지는 [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md) 구조입니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.  
  
## <a name="remarks"></a>설명  
 이 메서드는 일반적으로 해당 프로세스에서 실행 되는 프로그램 목록을 가져오는 프로세스에 의해 호출 됩니다. 반환 된 정보는 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) 개체의 목록입니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)   
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)   
 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)   
 [CONST_GUID_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md)   
 [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)   
 [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
