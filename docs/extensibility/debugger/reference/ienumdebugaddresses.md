---
title: IEnumDebugAddresses | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugAddresses
helpviewer_keywords:
- IEnumDebugAddresses interface
ms.assetid: 5f6f6751-e6d8-4c5a-8e81-414b6e5d8cc5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 14b42ec37babe72b47b0e832397d33029c4fc3d1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80717589"
---
# <a name="ienumdebugaddresses"></a>IEnumDebugAddresses
이 인터페이스는 [Idebugaddress](../../../extensibility/debugger/reference/idebugaddress.md) 인터페이스를 구현 하는 개체의 컬렉션을 나타냅니다.

## <a name="syntax"></a>Syntax

```
IEnumDebugAdresses : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 이 인터페이스는 [Idebugaddress](../../../extensibility/debugger/reference/idebugaddress.md) 인터페이스를 구현 하는 개체 집합을 제공 하기 위해 기호 공급자에 의해 구현 됩니다. 이는 [Getcount](../../../extensibility/debugger/reference/ienumdebugaddresses-getcount.md) 메서드가 있으므로 표준 COM 열거형이 아닙니다.

## <a name="notes-for-callers"></a>호출자 참고 사항
 이 인터페이스는 [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md) 및 [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)에 의해 반환 됩니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 이 인터페이스는 다음 메서드를 구현 합니다.

|메서드|설명|
|------------|-----------------|
|[다음](../../../extensibility/debugger/reference/ienumdebugaddresses-next.md)|열거형에서 다음 [Idebugaddress](../../../extensibility/debugger/reference/idebugaddress.md) 개체 집합을 검색 합니다.|
|[skip](../../../extensibility/debugger/reference/ienumdebugaddresses-skip.md)|지정 된 수의 항목을 건너뜁니다.|
|[재설정](../../../extensibility/debugger/reference/ienumdebugaddresses-reset.md)|열거형을 첫 번째 항목으로 다시 설정 합니다.|
|[복제](../../../extensibility/debugger/reference/ienumdebugaddresses-clone.md)|현재 열거형의 복사본을 검색 합니다.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugaddresses-getcount.md)|열거형의 항목 수를 검색 합니다.|

## <a name="remarks"></a>설명
 이 인터페이스는 일반적으로 디버그 엔진에서 식 계산기에 제공할 적절 한 주소를 결정 하는 데 사용 됩니다.

## <a name="requirements"></a>요구 사항
 헤더: sh

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>추가 정보
- [기호 공급자 인터페이스](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)
- [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)
