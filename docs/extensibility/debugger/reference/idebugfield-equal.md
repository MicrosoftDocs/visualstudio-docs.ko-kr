---
description: 이 메서드는이 필드와 지정 된 필드가 같은지 비교 합니다.
title: 'IDebugField:: Equal | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::Equal
helpviewer_keywords:
- IDebugField::Equal method
ms.assetid: 75369fe6-ddd3-497d-80d1-2488e6100e9f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 58673703fa0e585095c9a82fe2c7a4bc3e14827c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105077111"
---
# <a name="idebugfieldequal"></a>IDebugField::Equal
이 메서드는이 필드와 지정 된 필드가 같은지 비교 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT Equal( 
   IDebugField* pField
);
```

```csharp
int Equal(
   IDebugField pField
);
```

## <a name="parameters"></a>매개 변수
`pField`\
진행 이와 비교할 필드입니다.

## <a name="return-value"></a>반환 값
 필드가 같으면는를 반환 `S_OK` 합니다. 필드가 다르면가 반환 되 고 `S_FALSE.` , 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="see-also"></a>참조
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
