---
title: 'IDebugReference2:: SetValueAsReference | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::SetValueAsReference
helpviewer_keywords:
- IDebugReference2::SetValueAsReference
ms.assetid: 94a545d2-16b9-45e9-b2e7-4e49ff90aad0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2111f4c3b60bbdc5f8a88b5cc7777fc92af74509
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99963629"
---
# <a name="idebugreference2setvalueasreference"></a>IDebugReference2::SetValueAsReference
다른 참조에서 참조 값을 설정 합니다. 다음에 사용하도록 예약됩니다.

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
진행 참조 값을 설정 하는 방법을 결정 하는 데 사용 되는 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) 개체의 배열입니다.

`dwArgCount`\
진행 배열에 있는 참조의 수입니다.

`pValue`\
진행 속성 값을 설정 하는 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) 개체입니다.

`dwTimeout`\
진행 이 메서드에서 반환 될 때까지 대기 하는 최대 시간 (밀리초)입니다. `INFINITE`무기한 대기 하려면를 사용 합니다.

## <a name="return-value"></a>Return Value
 항상 `E_NOTIMPL`를 반환합니다.

## <a name="see-also"></a>참고 항목
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
