---
title: 아이디버그프로퍼티3::D에스트로이오브젝트ID | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::DestroyObjectID
helpviewer_keywords:
- IDebugProperty3::DestroyObjectID
ms.assetid: bd08f356-cc67-4717-98c9-c3d00cad2040
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f465bc06712c5032c6e90288ebd02406de4f2330
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721205"
---
# <a name="idebugproperty3destroyobjectid"></a>IDebugProperty3::DestroyObjectID
호출자는 더 이상 다른 모든 속성에서 이 속성을 고유하게 식별하는 데 관심이 없음을 나타내면서 이 속성과 연결된 고유 ID를 삭제합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT DestroyObjectID(
   void
);
```

```csharp
int DestroyObjectID();
```

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 디버그 엔진이 속성에 대해 고유한 ID를 지원할 필요가 없는 경우(이미 내부적으로 고유하게 추적하기 `E_NOTIMPL` 때문에) 이 메서드에 대해 반환할 수 있습니다.

 고유 ID는 호출자가 이 속성이 다른 모든 속성 간에 고유하게 식별되도록 하려고 할 때 [CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md) 메서드를 호출하여 만들어집니다.

## <a name="see-also"></a>참조
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)
