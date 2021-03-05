---
description: 이 메서드는이 포인터 개체가 가리키는 개체의 형식을 반환 합니다.
title: 'IDebugPointerField:: GetDereferencedField | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerField::GetDereferencedField
helpviewer_keywords:
- IDebugPointerField::GetDereferencedField method
ms.assetid: 8de988ab-cd79-4287-be72-3c900f2fe407
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 765ad40be87b7700ca1087745bef43ff0575dfa6
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102169706"
---
# <a name="idebugpointerfieldgetdereferencedfield"></a>IDebugPointerField::GetDereferencedField
이 메서드는이 포인터 개체가 가리키는 개체의 형식을 반환 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetDereferencedField(
   IDebugField** ppField
);
```

```csharp
int GetDereferencedField(
   out IDebugField ppField
);
```

## <a name="parameters"></a>매개 변수
`ppField`\
제한이 대상 개체의 형식을 설명 하는 [Idebugfield](../../../extensibility/debugger/reference/idebugfield.md) 를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 예를 들어 [Idebugpointerfield](../../../extensibility/debugger/reference/idebugpointerfield.md) 개체가 정수를 가리키는 경우이 메서드에서 반환 된 [idebugfield](../../../extensibility/debugger/reference/idebugfield.md) 형식은 해당 정수 형식을 설명 합니다.

## <a name="see-also"></a>참고 항목
- [IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
