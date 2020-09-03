---
title: IDebugCustomAttribute | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute
helpviewer_keywords:
- IDebugCustomAttribute interface
ms.assetid: c5ae41e9-00b9-4cca-871d-b8de9ef390d1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a31133139d0104cd29f5d0d0e760bd78ec5783fd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80732682"
---
# <a name="idebugcustomattribute"></a>IDebugCustomAttribute
이 인터페이스는 사용자 지정 특성을 나타내며 특성의 이름, 부모 및 클래스 형식을 제공할 수 있습니다.

## <a name="syntax"></a>Syntax

```
IDebugCustomAttribute : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 기호 공급자는 기호와 연결 된 사용자 지정 특성을 지원 하기 위해이 인터페이스를 구현 합니다. 일반적으로 자체 개체에서 구현 됩니다.

## <a name="notes-for-callers"></a>호출자 참고 사항
 [Next](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md) 호출은이 인터페이스를 반환 합니다. [Enumcustomattributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md) 메서드를 호출 하면 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md) 인터페이스가 반환 됩니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는의 메서드를 보여 줍니다 `IDebugCustomAttribute` .

|메서드|설명|
|------------|-----------------|
|[GetParentField](../../../extensibility/debugger/reference/idebugcustomattribute-getparentfield.md)|현재 특성이 연결 된 필드를 가져옵니다.|
|[GetAttributeTypeField](../../../extensibility/debugger/reference/idebugcustomattribute-getattributetypefield.md)|사용자 지정 특성 클래스 형식을 가져옵니다.|
|[GetName](../../../extensibility/debugger/reference/idebugcustomattribute-getname.md)|사용자 지정 특성의 이름을 가져옵니다.|
|[GetAttributeBytes](../../../extensibility/debugger/reference/idebugcustomattribute-getattributebytes.md)|특성 정보를 바이트의 blob으로 가져옵니다.|

## <a name="remarks"></a>설명
 사용자 지정 특성은 특정 클래스 또는 메서드와 연결 된 사용자 지정 메타 데이터를 제공 하는 c #의 구조입니다.

## <a name="requirements"></a>요구 사항
 헤더: sh

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>추가 정보
- [기호 공급자 인터페이스](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)
- [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)
