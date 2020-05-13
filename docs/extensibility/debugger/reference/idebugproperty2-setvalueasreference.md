---
title: IDebugProperty2::SetValueAs참조 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::SetValueAsReference
helpviewer_keywords:
- IDebugProperty2::SetValueAsReference method
ms.assetid: 341b1b89-4ab8-4e1c-abe2-fb955df5c6b0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 73d00ccedc6985061448170735e9ebcaac42f530
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721256"
---
# <a name="idebugproperty2setvalueasreference"></a>IDebugProperty2::SetValueAsReference
이 속성의 값을 지정된 참조 값으로 설정합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT SetValueAsReference(
   IDebugReference2** rgpArgs,
   DWORD              dwArgCount,
   IDebugReference2*  pValue,
   DWORD              dwTimeout
);
```

```csharp
int SetValueAsReference(
   IDebugReference2[] rgpArgs,
   uint               dwArgCount,
   IDebugReference2   pValue,
   uint               dwTimeout
);
```

## <a name="parameters"></a>매개 변수
`rgpArgs`\
【인】 관리 코드 속성 setter에 전달할 인수의 배열입니다. 속성 setter 인수를 사용 하지 않는 경우 또는이 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 개체는 이러한 `rgpArgs` 속성 setter를 참조 하지 않는 경우 null 값 이어야 합니다. 이 매개 변수는 일반적으로 null 값입니다.

`dwArgCount`\
【인】 배열의 인수 수입니다. `rgpArgs`

`pValue`\
【인】 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) 개체의 형태로 이 속성을 설정하는 데 사용할 값에 대한 참조입니다.

`dwTimeout`\
【인】 값을 밀리초 단위로 설정하는 데 걸리는 시간입니다. 일반적인 값은 `INFINITE`. 이는 가능한 평가가 걸릴 수 있는 기간에 영향을 줍니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드(일반적으로 다음 중 하나)를 반환합니다.

|Error|설명|
|-----------|-----------------|
|`E_SETVALUEASREFERENCE_NOTSUPPORTED`|참조에서 값을 설정하는 것은 지원되지 않습니다.|
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|이 속성은 메서드를 참조하므로 값을 설정할 수 없습니다.|
|`E_SETVALUE_VALUE_IS_READONLY`|값은 읽기 전용이며 설정할 수 없습니다.|
|`E_NOTIMPL`|메서드가 구현되지 않았습니다.|

## <a name="see-also"></a>참조
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
