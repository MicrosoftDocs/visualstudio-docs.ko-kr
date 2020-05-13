---
title: 아이디버그프로그램엔진2 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEngines2
helpviewer_keywords:
- IDebugProgramEngines2 interface
ms.assetid: 53d648f0-6c11-4337-badd-c43f3872b62c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 94df9acc6a0478ba2cb36022bc8618c69be97b8c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722391"
---
# <a name="idebugprogramengines2"></a>IDebugProgramEngines2
이 인터페이스는 프로그램 노드에서 이 프로그램을 디버깅할 수 있는 가능한 모든 DEBUG 엔진(DE)을 지정하는 데 사용됩니다.

## <a name="syntax"></a>구문

```
IDebugProgramEngines2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 DE 또는 사용자 지정 포트 공급자는 특정 프로그램에 사용할 특정 DE를 설정하는 것을 지원하기 위해 [IDebugProgramNode2를](../../../extensibility/debugger/reference/idebugprogramnode2.md) 구현하는 동일한 개체에 이 인터페이스를 구현합니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 이 인터페이스를 `IDebugProgramNode2` 얻으려면 인터페이스에서 [QueryInterface를](/cpp/atl/queryinterface) 호출합니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는 의 `IDebugProgramEngines2`메서드를 보여 주며 의 메서드를 보여 주면 됩니다.

|방법|설명|
|------------|-----------------|
|[EnumPossibleEngines](../../../extensibility/debugger/reference/idebugprogramengines2-enumpossibleengines.md)|이 프로그램을 디버깅할 수 있는 가능한 모든 DEs를 나타냅니다.|
|[SetEngine](../../../extensibility/debugger/reference/idebugprogramengines2-setengine.md)|이 프로그램을 디버깅하는 데 사용할 DE를 선택합니다.|

## <a name="remarks"></a>설명
 사용자가 DE를 선택하면 [SetEngine](../../../extensibility/debugger/reference/idebugprogramengines2-setengine.md)을 호출하여 해당 선택 항목이 프로그램 노드에 등록됩니다. 선택한 엔진은 [GetEngineInfo에서](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)반환되는 엔진이 됩니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)
