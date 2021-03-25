---
description: 이 인터페이스는이 인터페이스로 주소가 표시 되는 개체를 소유 하는 프로세스의 ID에 대 한 액세스를 제공 합니다.
title: IDebugAddress2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAddress2
helpviewer_keywords:
- IDebugAddress2 interface
ms.assetid: b150e0ed-4ac0-4f8c-9732-4b3e54b9d243
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7e74833768ed1a287c0dcf3b641b858261c2d661
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105059185"
---
# <a name="idebugaddress2"></a>IDebugAddress2
이 인터페이스는이 인터페이스로 주소가 표시 되는 개체를 소유 하는 프로세스의 ID에 대 한 액세스를 제공 합니다.

## <a name="syntax"></a>구문

```
IDebugAddress2 : IDebugAddress
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 기호 공급자는 [Idebugaddress](../../../extensibility/debugger/reference/idebugaddress.md) 인터페이스를 구현 하는 동일한 개체에서이 인터페이스를 구현 합니다. 이 인터페이스는이 주소와 관련 된 개체를 소유 하는 프로세스의 ID에 대 한 액세스를 제공 합니다.

## <a name="notes-for-callers"></a>호출자 참고 사항
 [QueryInterface](/cpp/atl/queryinterface) 를 사용 하 여 [idebugaddress](../../../extensibility/debugger/reference/idebugaddress.md) 인터페이스에서이 인터페이스를 가져옵니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 [Idebugaddress](../../../extensibility/debugger/reference/idebugaddress.md) 인터페이스에서 상속 된 메서드 외에도이 인터페이스는 다음 메서드를 구현 합니다.

|메서드|Description|
|------------|-----------------|
|[GetProcessID](../../../extensibility/debugger/reference/idebugaddress2-getprocessid.md)|이 인터페이스가 나타내는 개체를 소유 하는 프로세스의 ID를 검색 합니다.|

## <a name="requirements"></a>요구 사항
 헤더: sh

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참조
- [기호 공급자 인터페이스](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
