---
description: 이 인터페이스는 IDebugProcess2 구현자에 의해 구현 되는 확장 인터페이스입니다.
title: IDebugProcessQueryProperties | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessQueryProperties
ms.assetid: ce29a248-81a0-42c0-99a7-1606e8c548ec
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ae5fb8766e9cd0f48e85fa0b060efb4faa7bc496
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105076292"
---
# <a name="idebugprocessqueryproperties"></a>IDebugProcessQueryProperties
이 인터페이스는 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) 구현자에 의해 구현 되는 확장 인터페이스입니다. 이를 통해 구현자는 디버깅 프로세스 환경에 대 한 정보를 가져올 수 있습니다.

## <a name="syntax"></a>구문

```
IDebugProcessQueryProperties: IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 디버깅 프로세스의 실행 환경에 대 한 정보를 가져오려면이 인터페이스를 구현 합니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는의 메서드를 보여 줍니다 `IDebugProcessQueryProperties` .

|메서드|Description|
|------------|-----------------|
|[QueryProperty](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperty.md)|속성 값을 쿼리 합니다.|
|[QueryProperties](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperties.md)|속성 값을 쿼리 합니다.|

## <a name="remarks"></a>설명
 이 인터페이스는 거의 구현 되지 않습니다.

## <a name="requirements"></a>요구 사항
 헤더: Portpriv. h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참조
- [핵심 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
