---
title: IDebugPort2 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80725236"
---
# <a name="idebugport2"></a>IDebugPort2
이 인터페이스는 컴퓨터의 디버그 포트를 나타냅니다.

## <a name="syntax"></a>Syntax

```
IDebugPort2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 사용자 지정 포트 공급자는이 인터페이스를 구현 하 여 컴퓨터의 디버그 포트를 나타냅니다.

 포트에서 송신 포트 이벤트를 지 원하는 경우 인터페이스를 구현 <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> 하 여 <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) 인터페이스를 제공 하는 인터페이스를 구현 해야 합니다.

## <a name="notes-for-callers"></a>호출자 참고 사항
 [Getport](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md) 또는 [addport](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) 에 대 한 호출은 요청 된 포트를 나타내는이 인터페이스를 반환 합니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는의 메서드를 보여 줍니다 `IDebugPort2` .

|메서드|설명|
|------------|-----------------|
|[GetPortName](../../../extensibility/debugger/reference/idebugport2-getportname.md)|포트 이름을 반환 합니다.|
|[GetPortId](../../../extensibility/debugger/reference/idebugport2-getportid.md)|포트 식별자를 반환 합니다.|
|[GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)|포트를 만드는 데 사용 된 요청을 반환 합니다 (사용 가능한 경우).|
|[GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md)|이 포트에 대 한 포트 공급자를 반환 합니다.|
|[GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md)|프로세스의 식별자가 지정 된 프로세스에 대 한 인터페이스를 반환 합니다.|
|[EnumProcesses](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md)|포트에서 실행 중인 모든 프로세스를 열거 합니다.|

## <a name="remarks"></a>설명
 로컬 포트는 로컬 컴퓨터에서 실행 되는 모든 프로세스와 프로그램에 대 한 액세스를 제공 합니다. 다른 포트는 Windows CE 기반 장치에 대 한 직렬 케이블 연결 또는 DCOM이 아닌 컴퓨터에 대 한 네트워크 연결을 나타낼 수 있습니다. `IDebugPort2`인터페이스는 포트의 이름과 식별자를 찾고 포트에서 실행 중인 모든 프로세스를 열거 하는 데 사용 됩니다. 포트에서 프로세스를 시작 및 종료 하는 기능이 인터페이스에서 구현 됩니다 `IDebugPortEx2` .

## <a name="requirements"></a>요구 사항
 헤더: msdbg .h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>추가 정보
- [핵심 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
