---
title: 'IDebugReference2:: SetReferenceType | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::SetReferenceType
helpviewer_keywords:
- IDebugReference2::SetReferenceType
ms.assetid: 5854a172-ea82-481c-97d9-c7fc16923d44
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f33ae0203dfb3f3e6a6af67b925add8948720638
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99963668"
---
# <a name="idebugreference2setreferencetype"></a>IDebugReference2::SetReferenceType
참조 형식을 설정 합니다. 다음에 사용하도록 예약됩니다.

## <a name="syntax"></a>구문

```cpp
HRESULT SetReferenceType ( 
   REFERENCE_TYPE dwRefType
);
```

```csharp
int SetReferenceType ( 
   enum_REFERENCE_TYPE dwRefType
);
```

## <a name="parameters"></a>매개 변수
`dwRefType`\
진행 참조 형식을 지정 하는 [REFERENCE_TYPE](../../../extensibility/debugger/reference/reference-type.md) 열거형의 값입니다.

## <a name="return-value"></a>Return Value
 항상 `E_NOTIMPL`를 반환합니다.

## <a name="see-also"></a>참고 항목
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [REFERENCE_TYPE](../../../extensibility/debugger/reference/reference-type.md)
