---
title: 아이데버그필드::겟사이즈 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetSize
helpviewer_keywords:
- IDebugField::GetSize method
ms.assetid: 73329924-3751-4f44-af54-5986b7943374
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9f19a914de2e74613e987753c8062215fd0d0403
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728803"
---
# <a name="idebugfieldgetsize"></a>IDebugField::GetSize
이 메서드는 필드의 크기를 바이트로 가져옵니다.

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
【아웃】 크기를 반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 모든 필드에는 형식이 있고 모든 형식의 크기가 있습니다. 예를 들어 바이트 유형이 있는 필드의 크기는 1바이트입니다.

## <a name="see-also"></a>참조
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
