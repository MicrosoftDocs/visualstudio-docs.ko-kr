---
title: IDebugProgramEx2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEx2
helpviewer_keywords:
- IDebugProgramEx2 interface
ms.assetid: 663359ed-635a-4539-addb-0cc52f19d1bd
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f206de825d021d8daa2977a839f96fabd5e9db7f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99898856"
---
# <a name="idebugprogramex2"></a>IDebugProgramEx2
이 인터페이스를 사용 하면 세션 디버그 관리자 (SDM)를 프로그램에 연결 하 고 프로그램에 연결 된 프로그램 노드를 가져올 수 있습니다.

## <a name="syntax"></a>구문

```
IDebugProgramEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 사용자 지정 포트 공급자는 SDM이 프로그램에 연결 된 모든 세션을 추적할 수 있도록 허용 하는 동시에 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 인터페이스와 동일한 개체에서이 인터페이스를 구현 합니다. 사용자 지정 포트 공급자가를 선택 하는 경우이 인터페이스를 구현할 수 있습니다.

## <a name="notes-for-callers"></a>호출자 참고 사항
 SDM은 인터페이스에서 [QueryInterface](/cpp/atl/queryinterface) 를 호출 `IDebugProgram2` 하 여 프로그램에 연결 된 세션을 추적 하기 위해이 인터페이스를 가져옵니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는의 메서드를 보여 줍니다 `IDebugProgramEx2` .

|메서드|Description|
|------------|-----------------|
|[연결](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)|프로그램을 세션에 연결 합니다.|
|[GetProgramNode](../../../extensibility/debugger/reference/idebugprogramex2-getprogramnode.md)|프로그램과 연결 된 프로그램 노드를 가져옵니다.|

## <a name="remarks"></a>설명
 이 인터페이스는 SDM 및 프로그램 사이에서 전용입니다.

## <a name="requirements"></a>요구 사항
 헤더: Portpriv. h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고 항목
- [핵심 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
