---
title: 'IDebugObject2:: GetBackingFieldForProperty | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::GetBackingFieldForProperty
helpviewer_keywords:
- IDebugObject2::GetBackingFieldForProperty method
ms.assetid: e72c6338-5573-4fad-8075-f3ade3435424
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f502479d4c74eb0b5cfa71db52698121830e66e6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99953476"
---
# <a name="idebugobject2getbackingfieldforproperty"></a>IDebugObject2::GetBackingFieldForProperty
이 개체가 나타내는 속성을 지원 하 고 있을 수 있는 필드 또는 변수 (있는 경우)를 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetBackingFieldForProperty(
   IDebugObject2** ppObject
);
```

```csharp
int GetBackingFieldForProperty(
   out IDebugObject2 ppObject
);
```

## <a name="parameters"></a>매개 변수
`ppObject`\
제한이 지원 필드를 설명 하는 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) 개체입니다.

## <a name="return-value"></a>Return Value
 성공 하면 S_OK을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) 개체는 관리 코드 클래스 속성, 즉 get 및/또는 set 접근자가 있는 메서드를 나타냅니다. 이러한 속성에는 일반적으로 속성에 의해 조작 되는 값을 포함 하는 변수가 필요 합니다. 이 변수를 지원 필드 라고 합니다. 개체에 대 한 지원 필드가 없는 경우에는 null 값을 반환 해야 합니다. 일부 호출자는 반환 값에 주의를 기울여야 하지 않을 수 있지만 대신에서 null 값이 반환 되었는지 확인 `ppObject` 합니다.

## <a name="see-also"></a>참고 항목
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
