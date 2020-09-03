---
title: IDebugProcessQueryProperties | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80723284"
---
# <a name="idebugprocessqueryproperties"></a>IDebugProcessQueryProperties
이 인터페이스는 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) 구현자에 의해 구현 되는 확장 인터페이스입니다. 이를 통해 구현자는 디버깅 프로세스 환경에 대 한 정보를 가져올 수 있습니다.

## <a name="syntax"></a>Syntax

```
IDebugProcessQueryProperties: IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 디버깅 프로세스의 실행 환경에 대 한 정보를 가져오려면이 인터페이스를 구현 합니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는의 메서드를 보여 줍니다 `IDebugProcessQueryProperties` .

|메서드|설명|
|------------|-----------------|
|[QueryProperty](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperty.md)|속성 값을 쿼리 합니다.|
|[QueryProperties](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperties.md)|속성 값을 쿼리 합니다.|

## <a name="remarks"></a>설명
 이 인터페이스는 거의 구현 되지 않습니다.

## <a name="requirements"></a>요구 사항
 헤더: Portpriv. h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>추가 정보
- [핵심 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
