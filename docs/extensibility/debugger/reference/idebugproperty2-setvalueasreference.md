---
title: 'IDebugProperty2:: SetValueAsReference | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80721256"
---
# <a name="idebugproperty2setvalueasreference"></a>IDebugProperty2::SetValueAsReference
이 속성의 값을 지정 된 참조의 값으로 설정 합니다.

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
진행 관리 코드 속성 setter에 전달할 인수 배열입니다. 속성 setter가 인수를 사용 하지 않거나이 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 개체가 이러한 속성 setter를 참조 하지 않는 경우는 `rgpArgs` null 값 이어야 합니다. 이 매개 변수는 일반적으로 null 값입니다.

`dwArgCount`\
진행 배열의 인수 개수 `rgpArgs` 입니다.

`pValue`\
진행 이 속성을 설정 하는 데 사용할 값에 대 한 참조 ( [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) 개체 형식)입니다.

`dwTimeout`\
진행 값을 설정 하는 데 소요 되는 시간 (밀리초)입니다. 일반적인 값은 `INFINITE` 입니다. 이는 가능한 평가에서 수행할 수 있는 시간에 영향을 줍니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다. 일반적으로 다음 중 하나를 반환 합니다.

|오류|설명|
|-----------|-----------------|
|`E_SETVALUEASREFERENCE_NOTSUPPORTED`|참조에서 값을 설정 하는 것은 지원 되지 않습니다.|
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|이 속성은 메서드를 참조 하므로 값을 설정할 수 없습니다.|
|`E_SETVALUE_VALUE_IS_READONLY`|값은 읽기 전용 이며 설정할 수 없습니다.|
|`E_NOTIMPL`|메서드가 구현되지 않았습니다.|

## <a name="see-also"></a>추가 정보
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
