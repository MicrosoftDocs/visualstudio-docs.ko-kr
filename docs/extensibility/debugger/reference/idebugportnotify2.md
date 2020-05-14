---
title: 아이디버그포트알림2 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortNotify2
helpviewer_keywords:
- IDebugPortNotify2 interface
ms.assetid: 43278b79-bf16-4c08-bcf1-6f7f7a17feab
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 49d3d1161d488ed4a9e12b7af6b70bf336c9f286
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724922"
---
# <a name="idebugportnotify2"></a>IDebugPortNotify2
이 인터페이스는 실행 중인 포트로 디버깅할 수 있는 프로그램을 등록하거나 등록 취소합니다.

## <a name="syntax"></a>구문

```
IDebugPortNotify2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 사용자 지정 포트 공급자는 이 인터페이스를 구현하여 포트에서 프로그램 추가 및 제거를 지원합니다. 일반적으로 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) 인터페이스를 구현하는 동일한 개체에서 구현됩니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 인터페이스에서 [QueryInterface를](/cpp/atl/queryinterface) `IDebugPort2` 호출하면 이 인터페이스가 반환됩니다. 또한 [GetPortNotify에](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md) 대한 호출은 이 인터페이스를 반환합니다. 디버그 엔진은 이 인터페이스를 [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md).

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는 의 `IDebugPortNotify2`메서드를 보여 주며 의 메서드를 보여 주면 됩니다.

|방법|설명|
|------------|-----------------|
|[AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)|실행 중인 포트로 디버깅할 수 있는 프로그램을 등록합니다.|
|[RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)|실행 중인 포트에서 디버깅할 수 있는 프로그램을 등록 취소합니다.|

## <a name="remarks"></a>설명
 디버그 포트에 프로그램이 로드되거나 언로드되는 시기를 알 수 있는 방법이 없다면 사용자 지정 포트 공급자는 이 인터페이스를 구현해야 합니다. 특정 포트를 통해 디버깅하기 위해 로드된 모든 프로그램은 이 인터페이스를 사용하여 추적됩니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
