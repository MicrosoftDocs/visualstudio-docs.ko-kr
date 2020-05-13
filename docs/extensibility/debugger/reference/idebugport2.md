---
title: 아이디버그포트2 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPort2
helpviewer_keywords:
- IDebugPort2 interface
ms.assetid: 8fd87f05-a950-4d14-b925-98be29d4facc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 62912be9fdfecc98a264a58c9713cc12ccaf28f2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725236"
---
# <a name="idebugport2"></a>IDebugPort2
이 인터페이스는 컴퓨터의 디버그 포트를 나타냅니다.

## <a name="syntax"></a>구문

```
IDebugPort2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 사용자 지정 포트 공급자는 이 인터페이스를 구현하여 컴퓨터에서 디버그 포트를 나타냅니다.

 포트가 포트 이벤트 전송을 지원하는 경우 <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) 인터페이스를 제공하는 인터페이스를 지원하는 인터페이스도 구현해야 합니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 [GetPort](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md) 또는 [AddPort에](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) 대한 호출은 요청된 포트를 나타내는 이 인터페이스를 반환합니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는 의 `IDebugPort2`메서드를 보여 주며 의 메서드를 보여 주면 됩니다.

|방법|설명|
|------------|-----------------|
|[GetPortName](../../../extensibility/debugger/reference/idebugport2-getportname.md)|포트 이름을 반환합니다.|
|[GetPortId](../../../extensibility/debugger/reference/idebugport2-getportid.md)|포트 식별자를 반환합니다.|
|[GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)|포트를 만드는 데 사용된 요청을 반환합니다(사용 가능한 경우).|
|[GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md)|이 포트에 대한 포트 공급자를 반환합니다.|
|[GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md)|프로세스의 식별자가 지정된 프로세스에 인터페이스를 반환합니다.|
|[EnumProcesses](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md)|포트에서 실행되는 모든 프로세스를 모두 연수합니다.|

## <a name="remarks"></a>설명
 로컬 포트는 로컬 컴퓨터에서 실행되는 모든 프로세스 및 프로그램에 대한 액세스를 제공합니다. 다른 포트는 Windows CE 기반 장치에 대한 직렬 케이블 연결 또는 DCOM이 아닌 컴퓨터에 대한 네트워크 연결을 나타낼 수 있습니다. 인터페이스는 `IDebugPort2` 포트의 이름과 식별자를 찾고 포트에서 실행되는 모든 프로세스를 등록하는 데 사용됩니다. 포트에서 프로세스를 시작하고 종료하기 위한 시설은 인터페이스에서 `IDebugPortEx2` 구현됩니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
