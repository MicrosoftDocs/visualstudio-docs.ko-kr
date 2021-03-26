---
description: 한 참조를 다른 참조와 비교 합니다.
title: 'IDebugReference2:: Compare | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::Compare
helpviewer_keywords:
- IDebugReference2::Compare
ms.assetid: 3361c495-2673-4b7c-82e3-dee74e1fa58d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 017dfa60c1f854a36f1087bef87203f0b22ae4dc
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105083637"
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

## <a name="return-value"></a>반환 값
 항상 `E_NOTIMPL`를 반환합니다.

## <a name="see-also"></a>참조
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [REFERENCE_COMPARE](../../../extensibility/debugger/reference/reference-compare.md)
