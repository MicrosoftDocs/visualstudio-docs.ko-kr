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
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0d293fcb89c92a19acc4f5a3910015914ef4231a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80720645"
---
# <a name="idebugreference2compare"></a>IDebugReference2::Compare
한 참조를 다른 참조와 비교 합니다. 나중에 사용하기 위해 예약되어 있습니다.

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

## <a name="see-also"></a>추가 정보
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [REFERENCE_COMPARE](../../../extensibility/debugger/reference/reference-compare.md)
