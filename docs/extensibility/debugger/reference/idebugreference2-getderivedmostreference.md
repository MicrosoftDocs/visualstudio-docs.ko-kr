---
title: IDebugReference2:GetDerivedMostReference | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::GetDerivedMostReference
helpviewer_keywords:
- IDebugReference2::GetDerivedMostReference
ms.assetid: 07253b74-7d39-48e0-8e85-ac8dfd919f6e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 15e98884d040cfb2ebf1b33a56c7edea331fbff0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720619"
---
# <a name="idebugreference2getderivedmostreference"></a>IDebugReference2::GetDerivedMostReference
참조의 파생된 참조를 가져옵니다. 다음에 사용하도록 예약됩니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetDerivedMostReference( 
   IDebugReference2** ppDerivedMost
);
```

```csharp
int GetDerivedMostReference( 
   out IDebugReference2 ppDerivedMost
);
```

## <a name="parameters"></a>매개 변수
`ppDerivedMost`\
【아웃】 파생된 가장 많은 속성을 나타내는 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) 개체를 반환합니다.

## <a name="return-value"></a>Return Value
 항상 `E_NOTIMPL`를 반환합니다.

## <a name="remarks"></a>설명
 예를 들어 이 속성에서 `ClassRoot` 파생 된 실제로 인스턴스화 `ClassDerived` 하는 개체를 설명 하는 `ClassRoot`경우이 메서드는 `ClassDerived` 개체에 대 한 참조를 나타내는 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) 개체를 반환 합니다.

## <a name="see-also"></a>참조
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
