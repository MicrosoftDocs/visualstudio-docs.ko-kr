---
title: 아이디버그 오브젝트::설정값 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::SetValue
helpviewer_keywords:
- IDebugObject::SetValue method
ms.assetid: d652e09c-cdc1-4519-8116-d7c743f5679b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9e4652eb3c77a1871063dfa71b464fb1f7c43f94
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726363"
---
# <a name="idebugobjectsetvalue"></a>IDebugObject::SetValue
연속된 바이트 시리즈에서 개체값을 설정합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT SetValue( 
   BYTE* pValue,
   UINT  nSize
);
```

```csharp
int SetValue(
   byte[] pValue,
   uint   nSize
);
```

## <a name="parameters"></a>매개 변수
`pValue`\
【인】 새 값을 나타내는 바이트 배열입니다.

`nSize`\
【인】 바이트 의 값 크기입니다.

## <a name="return-value"></a>Return Value
 성공하면 S_OK 반환합니다. 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 배열의 값은 이 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 개체에 복사되어 기존 값을 대체합니다. 새 값의 크기는 기존 값보다 크거나 작을 수 있습니다. null `IDebugObject` 참조가 될 수 없습니다.

## <a name="see-also"></a>참조
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)
