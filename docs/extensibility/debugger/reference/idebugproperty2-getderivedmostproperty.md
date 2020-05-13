---
title: IDebugProperty2::GetDerivedMostProperty | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetDerivedMostProperty
helpviewer_keywords:
- IDebugProperty2::GetDerivedMostProperty
ms.assetid: cc86b461-62d1-4340-8209-c65037fd8b02
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2086aded4361049d722ec36ba1d470ed8f7ac6e5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721496"
---
# <a name="idebugproperty2getderivedmostproperty"></a>IDebugProperty2::GetDerivedMostProperty
속성의 파생 된 대부분의 속성을 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetDerivedMostProperty ( 
   IDebugProperty2** ppDerivedMost
);
```

```csharp
int GetDerivedMostProperty ( 
   out IDebugProperty2 ppDerivedMost
);
```

## <a name="parameters"></a>매개 변수
`ppDerivedMost`\
【아웃】 파생된 가장 많은 속성을 나타내는 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 개체를 반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다. 검색할 파생-가장 많은 속성이 없는 경우 반환합니다. `S_GETDERIVEDMOST_NO_DERIVED_MOST`

## <a name="remarks"></a>설명
 예를 들어 이 속성에서 파생 `ClassRoot` 된 구현 하지만 실제로 는 인스턴스화 `ClassDerived` `ClassRoot`개체를 설명 하는 경우이 메서드는 개체를 설명 하는 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 개체를 `ClassDerived` 반환 합니다.

## <a name="see-also"></a>참조
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
