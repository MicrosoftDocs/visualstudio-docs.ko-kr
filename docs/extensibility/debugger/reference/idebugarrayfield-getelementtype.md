---
title: 'IDebugArrayField:: GetElementType | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayField::GetElementType
helpviewer_keywords:
- IDebugArrayField::GetElementType method
ms.assetid: c46bf625-0a48-4cbb-8f1f-286356f2c065
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 44b49cbcd52137b31dd456c4cf45bb3fe8ead947
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99944655"
---
# <a name="idebugarrayfieldgetelementtype"></a>IDebugArrayField::GetElementType
배열에 있는 요소의 형식을 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetElementType( 
   IDebugField** ppType
);
```

```csharp
int GetElementType(
   out IDebugField ppType
);
```

## <a name="parameters"></a>매개 변수
`ppType`\
제한이 요소의 형식을 설명 하는 [Idebugfield](../../../extensibility/debugger/reference/idebugfield.md) 개체를 반환 합니다.

## <a name="return-value"></a>Return Value
 성공 하면 S_OK을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 [Idebugarrayfield](../../../extensibility/debugger/reference/idebugarrayfield.md) 개체는 배열의 모든 요소가 동일한 형식 이라고 가정 합니다.

## <a name="see-also"></a>참고 항목
- [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
