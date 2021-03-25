---
description: 이 인터페이스는 프로세스 경계에서 프로그램 관련 인터페이스를 마샬링합니다.
title: IDebugProviderProgramNode2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProviderProgramNode2
helpviewer_keywords:
- IDebugProviderProgramNode2
ms.assetid: f0bca1cc-afbe-44cf-b5aa-d078aa685d24
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3d09046d70d6bc766d17963ea4cdd6469c0981fb
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105083676"
---
# <a name="idebugproviderprogramnode2"></a>IDebugProviderProgramNode2
이 인터페이스는 프로세스 경계에서 프로그램 관련 인터페이스를 마샬링합니다.

## <a name="syntax"></a>구문

```
IDebugProviderProgramNode2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 DE (디버그 엔진)는 프로세스 경계에서 인터페이스 마샬링을 지원 하기 위해 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) 을 구현 하는 동일한 개체에서이 인터페이스를 구현 합니다.

## <a name="notes-for-callers"></a>호출자 참고 사항
 인터페이스에서 [QueryInterface](/cpp/atl/queryinterface) `IDebugProgramNode2` 를 호출 하 여이 인터페이스를 가져옵니다. 이 인터페이스를 가져올 수 없는 경우 DE는 인터페이스의 마샬링을 지원 하지 않습니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 이 인터페이스는 다음 메서드를 구현 합니다.

|메서드|Description|
|------------|-----------------|
|[UnmarshalDebuggeeInterface](../../../extensibility/debugger/reference/idebugproviderprogramnode2-unmarshaldebuggeeinterface.md)|프로세스 경계를 넘어 지정 된 인터페이스를 가져옵니다.|

## <a name="remarks"></a>설명
 이 인터페이스는 디버그 중인 프로그램에서 별도의 프로세스 공간으로 DE를 실행 하는 경우에 구현 됩니다. 예를 들어 DE가 디버깅 중인 프로그램의 프로세스 공간 대신 Visual Studio 프로세스 공간에서 실행 되는 경우입니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg .h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참조
- [핵심 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
