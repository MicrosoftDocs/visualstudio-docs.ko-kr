---
title: IDebug참조2::SetValueAs참조 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::SetValueAsReference
helpviewer_keywords:
- IDebugReference2::SetValueAsReference
ms.assetid: 94a545d2-16b9-45e9-b2e7-4e49ff90aad0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f4767dbe08e716d64ea03c18a1c4a6f7d6690a7b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720300"
---
# <a name="idebugreference2setvalueasreference"></a>IDebugReference2::SetValueAsReference
다른 참조에서 참조 값을 설정합니다. 다음에 사용하도록 예약됩니다.

## <a name="syntax"></a>구문

```cpp
HRESULT SetValueAsReference ( 
   IDebugReference2** rgpArgs,
   DWORD              dwArgCount,
   IDebugReference2*  pValue,
   DWORD              dwTimeout
);
```

```cpp
int SetValueAsReference ( 
   IDebugReference2[] rgpArgs,
   uint               dwArgCount,
   IDebugReference2   pValue,
   uint               dwTimeout
);
```

## <a name="parameters"></a>매개 변수
`rgpArgs`\
【인】 참조 값을 설정하는 방법을 결정하는 데 사용되는 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) 개체의 배열입니다.

`dwArgCount`\
【인】 배열의 참조 수입니다.

`pValue`\
【인】 속성 값을 설정할 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) 개체입니다.

`dwTimeout`\
【인】 이 메서드에서 반환하기 전에 기다릴 수 있는 최대 시간(밀리초)입니다. 무기한 `INFINITE` 대기하는 데 사용합니다.

## <a name="return-value"></a>Return Value
 항상 `E_NOTIMPL`를 반환합니다.

## <a name="see-also"></a>참조
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
