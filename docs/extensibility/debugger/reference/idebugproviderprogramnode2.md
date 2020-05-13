---
title: 아이디버그프로바이더프로그램노드2 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProviderProgramNode2
helpviewer_keywords:
- IDebugProviderProgramNode2
ms.assetid: f0bca1cc-afbe-44cf-b5aa-d078aa685d24
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 815a945f6fb591960ebf0bf4b4fcd9d842ffefd3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720685"
---
# <a name="idebugproviderprogramnode2"></a>IDebugProviderProgramNode2
이 인터페이스는 프로세스 경계를 넘어 프로그램 관련 인터페이스를 마샬링합니다.

## <a name="syntax"></a>구문

```
IDebugProviderProgramNode2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 디버그 엔진(DE)은 [IDebugProgramNode2를](../../../extensibility/debugger/reference/idebugprogramnode2.md) 구현하는 동일한 개체에 이 인터페이스를 구현하여 프로세스 경계를 넘어 마샬링 인터페이스를 지원합니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 이 인터페이스를 `IDebugProgramNode2` 얻으려면 인터페이스에서 [QueryInterface를](/cpp/atl/queryinterface) 호출합니다. 이 인터페이스를 가져올 수 없는 경우 DE는 인터페이스 마샬링을 지원하지 않습니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 이 인터페이스는 다음 방법을 구현합니다.

|방법|설명|
|------------|-----------------|
|[UnmarshalDebuggeeInterface](../../../extensibility/debugger/reference/idebugproviderprogramnode2-unmarshaldebuggeeinterface.md)|프로세스 경계를 넘어 지정된 인터페이스를 가져옵니다.|

## <a name="remarks"></a>설명
 이 인터페이스는 DE가 디버깅 중인 프로그램과 별도의 프로세스 공간에서 실행될 때 구현됩니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
