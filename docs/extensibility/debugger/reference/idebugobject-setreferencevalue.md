---
description: 이 개체의 참조 값을 설정 합니다.
title: 'IDebugObject:: SetReferenceValue | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::SetReferenceValue
helpviewer_keywords:
- IDebugObject::SetReferenceValue method
ms.assetid: 08c78a4e-98eb-41cb-8b75-02a6a43d49f7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bb376e4399157f9f9fe393086cca8fcf94c3b9de
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102161426"
---
# <a name="idebugobjectsetreferencevalue"></a>IDebugObject::SetReferenceValue
이 개체의 참조 값을 설정 합니다.

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
진행 새 참조 값을 나타내는 [Idebugobject](../../../extensibility/debugger/reference/idebugobject.md) 개체입니다.

## <a name="return-value"></a>반환 값
 성공 하면 S_OK을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 이 메서드는이 [Idebugobject](../../../extensibility/debugger/reference/idebugobject.md) 개체를 매개 변수에 지정 된 개체 값에 대 한 참조로 만들어 `pObject` 이전 참조를 모두 throw 합니다. 이 개체는 `IDebugObject` 이미 참조 형식 이어야 합니다.

## <a name="see-also"></a>참고 항목
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)
