---
description: 이 메서드는 필드의 크기 (바이트)를 가져옵니다.
title: 'IDebugField:: GetSize | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetSize
helpviewer_keywords:
- IDebugField::GetSize method
ms.assetid: 73329924-3751-4f44-af54-5986b7943374
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 471b6dce3c4795f8059e64aff5e7522b3ba91842
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105077033"
---
# <a name="idebugfieldgetsize"></a>IDebugField::GetSize
이 메서드는 필드의 크기 (바이트)를 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetSize( 
   DWORD* pdwSize
);
```

```csharp
int GetSize(
   out uint pdwSize
);
```

## <a name="parameters"></a>매개 변수
`pdwSize`\
제한이 크기를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 모든 필드에는 형식이 있으며 모든 형식에는 크기가 있습니다. 예를 들어 byte 형식의 필드는 크기가 1 바이트입니다.

## <a name="see-also"></a>참조
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
