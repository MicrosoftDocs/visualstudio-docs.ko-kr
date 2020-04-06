---
title: 아이디버그프로그램노드2 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2
helpviewer_keywords:
- IDebugProgramNode2 interface
ms.assetid: 80e511d8-9b40-4a85-aa5d-952fa5ee6ae7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2e6eac7c97b9d375f32e36a372d6f31175c79098
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721921"
---
# <a name="idebugprogramnode2"></a>IDebugProgramNode2
이 인터페이스는 디버깅할 수 있는 프로그램을 나타냅니다.

## <a name="syntax"></a>구문

```
IDebugProgramNode2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 디버그 엔진(DE) 또는 사용자 지정 포트 공급자는 디버깅할 수 있는 프로그램을 나타내기 위해 이 인터페이스를 구현합니다. 이 인터페이스는 일반적으로 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 인터페이스를 구현하는 동일한 개체에서 구현됩니다. 이 인터페이스는 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)를 호출하여 등록됩니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 [GetProviderProgramNode를](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md) 호출하여 이 인터페이스를 반환합니다. 사용자 지정 포트 공급자는 [AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)에 대한 호출을 통해 이 인터페이스를 수신합니다. DE는 [연결](../../../extensibility/debugger/reference/idebugengine2-attach.md)에 대한 호출을 통해 이 인터페이스를 수신합니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는 의 `IDebugProgramNode2`메서드를 보여 주며 의 메서드를 보여 주면 됩니다.

|방법|설명|
|------------|-----------------|
|[GetProgramName](../../../extensibility/debugger/reference/idebugprogramnode2-getprogramname.md)|프로그램의 이름을 가져옵니다.|
|[GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)|프로그램을 호스팅하는 프로세스의 이름을 가져옵니다.|
|[GetHostPid](../../../extensibility/debugger/reference/idebugprogramnode2-gethostpid.md)|프로그램을 호스팅하는 프로세스에 대한 시스템 프로세스 식별자를 가져옵니다.|
|[GetHostMachineName_V7](../../../extensibility/debugger/reference/idebugprogramnode2-gethostmachinename-v7.md)|되지 않는. 사용하지 마십시오.|
|[Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)|되지 않는. 사용하지 마십시오. 다른 방법은 [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md) 인터페이스를 참조하십시오.|
|[GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)|이 프로그램을 실행하는 DE의 이름과 식별자를 가져옵니다.|
|[DetachDebugger_V7](../../../extensibility/debugger/reference/idebugprogramnode2-detachdebugger-v7.md)|되지 않는. 사용하지 마십시오.|

## <a name="remarks"></a>설명
 세션 디버그 관리자(SDM)는 일반적으로 [GetProviderProgramNode를](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md) 호출하여 이 인터페이스를 가져옵니다.

## <a name="requirements"></a>요구 사항
 헤더: Msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
- [RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)
- [연결](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)
- [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)
