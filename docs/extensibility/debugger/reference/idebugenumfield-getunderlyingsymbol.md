---
title: 이데버그에넘필드::겟디어더기호 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetUnderlyingSymbol
helpviewer_keywords:
- IDebugEnumField::GetUnderlyingSymbol method
ms.assetid: c3b8a117-6708-4cfd-8ffc-5f007d706bc5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 14cac9d3f761e95b821179137f2efc23ef61b91b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730276"
---
# <a name="idebugenumfieldgetunderlyingsymbol"></a>IDebugEnumField::GetUnderlyingSymbol
이 메서드는 열거형의 이름을 나타내는 [IDebugField를](../../../extensibility/debugger/reference/idebugfield.md) 반환합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetUnderlyingSymbol(
   IDebugField** ppField
);
```

```csharp
int GetUnderlyingSymbol(
   out IDebugField ppField
);
```

## <a name="parameters"></a>매개 변수
`ppField`\
【아웃】 이 열거형의 이름을 설명하는 [IDebugField를](../../../extensibility/debugger/reference/idebugfield.md) 반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 열거형의 이름에는 [바인딩을](../../../extensibility/debugger/reference/idebugbinder-bind.md)사용하여 메모리 위치에 바인딩되는 열거형의 형식도 포함됩니다.

## <a name="see-also"></a>참조
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [바인딩](../../../extensibility/debugger/reference/idebugbinder-bind.md)
