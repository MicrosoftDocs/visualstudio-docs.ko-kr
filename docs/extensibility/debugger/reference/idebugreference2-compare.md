---
title: 'IDebugReference2:: Compare | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::Compare
helpviewer_keywords:
- IDebugReference2::Compare
ms.assetid: 3361c495-2673-4b7c-82e3-dee74e1fa58d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6cebc34bdd1515ad632a0165fcdc900999b383fd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99909742"
---
# <a name="idebugreference2compare"></a>IDebugReference2::Compare
한 참조를 다른 참조와 비교 합니다. 다음에 사용하도록 예약됩니다.

## <a name="syntax"></a>구문

```cpp
HRESULT Compare ( 
   REFERENCE_COMPARE dwCompare,
   IDebugReference2* pReference
);
```

```csharp
int Compare ( 
   enum_REFERENCE_COMPARE dwCompare,
   IDebugReference2       pReference
);
```

## <a name="parameters"></a>매개 변수
`dwCompare`\
진행 비교 연산을 지정 하는 [REFERENCE_COMPARE](../../../extensibility/debugger/reference/reference-compare.md) 열거형의 값입니다 (예: 같음, 보다 작음 또는 보다 큼).

`pReference`\
진행 비교할 참조를 나타내는 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) 개체입니다.

## <a name="return-value"></a>Return Value
 항상 `E_NOTIMPL`를 반환합니다.

## <a name="see-also"></a>참고 항목
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [REFERENCE_COMPARE](../../../extensibility/debugger/reference/reference-compare.md)
