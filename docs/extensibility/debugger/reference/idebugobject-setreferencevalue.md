---
title: IDebugObject::설정참조값 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::SetReferenceValue
helpviewer_keywords:
- IDebugObject::SetReferenceValue method
ms.assetid: 08c78a4e-98eb-41cb-8b75-02a6a43d49f7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cc0db8ee7f0581a4c336111d3876c24f0e5c12d1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726370"
---
# <a name="idebugobjectsetreferencevalue"></a>IDebugObject::SetReferenceValue
이 개체의 참조 값을 설정합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT SetReferenceValue( 
   IDebugObject* pObject
);
```

```csharp
int SetReferenceValue(
   [In] IDebugObject pObject
);
```

## <a name="parameters"></a>매개 변수
`pObject`\
【인】 새 참조 값을 나타내는 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 개체입니다.

## <a name="return-value"></a>Return Value
 성공하면 S_OK 반환합니다. 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 이 메서드는 이 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 개체 매개 `pObject` 변수에 주어진 개체의 값에 대 한 참조를 사용 하 고 이전 참조를 버리지 않습니다. 이 `IDebugObject` 개체는 이미 참조 형식이어야 합니다.

## <a name="see-also"></a>참조
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)
