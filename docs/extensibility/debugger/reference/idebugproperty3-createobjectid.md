---
title: 아이디버그프로퍼퍼피3:오브젝트ID 생성 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::CreateObjectID
helpviewer_keywords:
- IDebugProperty3::CreateObjectID
ms.assetid: f2fa81e7-822f-456e-8729-a96a18eea771
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1d3993d674f029260dbe32d16c576cb239ff8d6d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721183"
---
# <a name="idebugproperty3createobjectid"></a>IDebugProperty3::CreateObjectID
이 속성에 대 한 고유 ID를 만들어 다른 모든 속성 간에 고유한지 확인 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT CreateObjectID(
   void
);
```

```csharp
int CreateObjectID();
```

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 이 메서드는 세션 디버그 관리자가 이 속성이 다른 모든 속성 간에 고유하게 식별되도록 하려고 할 때 호출됩니다. 디버그 엔진(DE)은 해당 기관이 처리하는 속성이 이미 고유하게 식별되지 않는 한 이 메서드를 지원합니다. DE가 이 메서드를 지원하지 않으면 `E_NOTIMPL`반환합니다.

 `CreateObjectID` [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md) 메서드가 호출될 때 생성된 모든 고유 ID가 소멸됩니다. 이것은 또한 이 속성을 고유하게 식별할 필요성이 끝났음을 나타냅니다.

> [!NOTE]
> 이 고유 ID를 검색하는 방법은 없으므로 DE는 `CreateObjectID` 메서드가 호출될 때 고유 ID에 대해 원하는 대로 수행할 수 있습니다.

## <a name="see-also"></a>참조
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)
