---
title: IDebugField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField
helpviewer_keywords:
- IDebugField interface
ms.assetid: adecdd1c-b1b9-4027-92da-74cbe910636f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8c7a25246f42d288020481330fe60e312849862d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80728758"
---
# <a name="idebugfield"></a>IDebugField
이 인터페이스는 필드, 즉 기호 또는 형식에 대 한 설명을 나타냅니다.

## <a name="syntax"></a>Syntax

```
IDebugField : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 기호 공급자는이 인터페이스를 모든 필드에 대 한 기본 클래스로 구현 합니다.

## <a name="notes-for-callers"></a>호출자 참고 사항
 이 인터페이스는 모든 필드의 기본 클래스입니다. [Getkind](../../../extensibility/debugger/reference/idebugfield-getkind.md)의 반환 값에 따라이 인터페이스는 [QueryInterface](/cpp/atl/queryinterface)를 사용 하 여 보다 특수화 된 인터페이스를 반환할 수 있습니다. 또한 많은 인터페이스는 `IDebugField` 다양 한 메서드의 개체를 반환 합니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는의 메서드를 보여 줍니다 `IDebugField` .

|메서드|설명|
|------------|-----------------|
|[GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)|기호 또는 형식에 대 한 표시할 정보를 가져옵니다.|
|[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)|필드의 종류를 가져옵니다.|
|[GetType](../../../extensibility/debugger/reference/idebugfield-gettype.md)|필드의 형식을 가져옵니다.|
|[GetContainer](../../../extensibility/debugger/reference/idebugfield-getcontainer.md)|필드의 컨테이너를 가져옵니다.|
|[GetAddress](../../../extensibility/debugger/reference/idebugfield-getaddress.md)|필드의 주소를 가져옵니다.|
|[GetSize](../../../extensibility/debugger/reference/idebugfield-getsize.md)|필드의 크기 (바이트)를 가져옵니다.|
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugfield-getextendedinfo.md)|필드에 대 한 확장 정보를 가져옵니다.|
|[같음](../../../extensibility/debugger/reference/idebugfield-equal.md)|두 필드를 비교 합니다.|
|[GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)|기호 또는 형식에 대 한 형식 독립적 정보를 가져옵니다.|

## <a name="remarks"></a>설명
 형식은 C 언어와 동일 `typedef` 합니다.

 다음 c + + 언어 예제에서 `weather` 은 클래스 형식이 고 `sunny` 및 `stormy` 는 기호입니다.

```cpp
class weather;
weather sunny;
weather stormy;
```

 [Getkind](../../../extensibility/debugger/reference/idebugfield-getkind.md) 를 호출 하 고 [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) 결과를 검사 하 여 필드가 기호 또는 형식을 나타내는지 여부를 결정할 수 있습니다. `FIELD_KIND_TYPE`비트가 설정 된 경우 필드는 형식이 고 비트가 설정 된 경우에는 `FIELD_KIND_SYMBOL` 기호입니다.

## <a name="requirements"></a>요구 사항
 헤더: sh

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>추가 정보
- [기호 공급자 인터페이스](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
