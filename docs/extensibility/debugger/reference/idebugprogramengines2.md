---
description: 이 인터페이스는 프로그램 노드에서이 프로그램을 디버그할 수 있는 모든 가능한 디버그 엔진 (DE)을 지정 하는 데 사용 됩니다.
title: IDebugProgramEngines2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEngines2
helpviewer_keywords:
- IDebugProgramEngines2 interface
ms.assetid: 53d648f0-6c11-4337-badd-c43f3872b62c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9c19b4dc3967cf7001144d38114a1f873776cb2b
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102149589"
---
# <a name="idebugprogramengines2"></a>IDebugProgramEngines2
이 인터페이스는 프로그램 노드에서이 프로그램을 디버그할 수 있는 모든 가능한 디버그 엔진 (DE)을 지정 하는 데 사용 됩니다.

## <a name="syntax"></a>Syntax

```
IDebugProgramEngines2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 DE 또는 사용자 지정 포트 공급자는 특정 프로그램에 사용할 특정 DE를 설정 하는 것을 지원 하기 위해 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) 을 구현 하는 동일한 개체에서이 인터페이스를 구현 합니다.

## <a name="notes-for-callers"></a>호출자 참고 사항
 인터페이스에서 [QueryInterface](/cpp/atl/queryinterface) `IDebugProgramNode2` 를 호출 하 여이 인터페이스를 가져옵니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는의 메서드를 보여 줍니다 `IDebugProgramEngines2` .

|메서드|설명|
|------------|-----------------|
|[EnumPossibleEngines](../../../extensibility/debugger/reference/idebugprogramengines2-enumpossibleengines.md)|이 프로그램을 디버그할 수 있는 모든 가능한 DEs를 나타냅니다.|
|[SetEngine](../../../extensibility/debugger/reference/idebugprogramengines2-setengine.md)|이 프로그램을 디버깅 하는 데 사용할 DE를 선택 합니다.|

## <a name="remarks"></a>설명
 사용자가 DE를 선택 하면 해당 선택은 [Setengine](../../../extensibility/debugger/reference/idebugprogramengines2-setengine.md)을 호출 하 여 program 노드에 등록 됩니다. 선택한 엔진은 [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)에서 반환 하는 엔진이 됩니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg .h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고 항목
- [핵심 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)
