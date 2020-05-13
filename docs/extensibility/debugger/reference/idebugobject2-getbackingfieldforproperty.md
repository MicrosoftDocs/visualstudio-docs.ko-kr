---
title: IDebugObject2::겟백필드포퍼퍼 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::GetBackingFieldForProperty
helpviewer_keywords:
- IDebugObject2::GetBackingFieldForProperty method
ms.assetid: e72c6338-5573-4fad-8075-f3ade3435424
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b5b9fed9b071f34c119c8e4a5af12c1df7990f4c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726247"
---
# <a name="idebugobject2getbackingfieldforproperty"></a>IDebugObject2::GetBackingFieldForProperty
이 개체로 표시되는 속성을 백업할 수 있는 필드 또는 변수(있는 경우)를 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetBackingFieldForProperty(
   IDebugObject2** ppObject
);
```

```csharp
int GetBackingFieldForProperty(
   out IDebugObject2 ppObject
);
```

## <a name="parameters"></a>매개 변수
`ppObject`\
【아웃】 백업 필드를 설명하는 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) 개체입니다.

## <a name="return-value"></a>Return Value
 성공하면 S_OK 반환합니다. 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) 개체는 관리 되는 코드 클래스 속성, 즉 get 및/또는 집합 접근자가 있는 메서드를 나타냅니다. 이러한 속성은 일반적으로 속성에서 조작한 값을 포함하기 위해 변수가 필요합니다. 이 변수를 백업 필드라고 합니다. 개체에 대한 백업 필드가 없는 경우 null 값을 반환해야 합니다: 일부 호출자는 반환 값에 주의를 기울이지 않고 대신 null `ppObject`값이 에서 반환되었는지 확인합니다.

## <a name="see-also"></a>참조
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
