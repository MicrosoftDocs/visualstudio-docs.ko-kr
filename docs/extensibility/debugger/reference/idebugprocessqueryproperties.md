---
title: 아이디버그프로세스쿼리속성 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessQueryProperties
ms.assetid: ce29a248-81a0-42c0-99a7-1606e8c548ec
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 08abf401b4e8f0e7a33d882e8178d77e6f248318
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723284"
---
# <a name="idebugprocessqueryproperties"></a>IDebugProcessQueryProperties
이 인터페이스는 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) 구현자가 구현한 확장 인터페이스입니다. 구현자는 디버깅 프로세스 환경에 대한 정보를 얻을 수 있습니다.

## <a name="syntax"></a>구문

```
IDebugProcessQueryProperties: IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 이 인터페이스를 구현하여 디버깅 프로세스의 실행 환경에 대한 정보를 가져옵니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는 의 `IDebugProcessQueryProperties`메서드를 보여 주며 의 메서드를 보여 주면 됩니다.

|방법|설명|
|------------|-----------------|
|[QueryProperty](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperty.md)|속성 값에 대한 쿼리입니다.|
|[QueryProperties](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperties.md)|속성 값에 대한 쿼리입니다.|

## <a name="remarks"></a>설명
 이 인터페이스는 거의 구현되지 않습니다.

## <a name="requirements"></a>요구 사항
 헤더: 포트프리브.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
