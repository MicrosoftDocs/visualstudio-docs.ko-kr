---
title: 아이데버그메모리컨텍스트2::GetName | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2::GetName
helpviewer_keywords:
- IDebugMemoryContext2::GetName method
- GetName method
ms.assetid: 8c212556-7d9e-4d68-b2a9-8212f50d0287
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b8a13c078340eafcff9440e41afd468ba95f9849
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727457"
---
# <a name="idebugmemorycontext2getname"></a>IDebugMemoryContext2::GetName
이 컨텍스트에 대해 사용자가 표시할 수 있는 이름을 검색합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetName( 
   BSTR* pbstrName
);
```

```csharp
int GetName(
   out string pbstrName
);
```

## <a name="parameters"></a>매개 변수
`pbstrName`\
【아웃】 메모리 컨텍스트의 이름을 반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 메모리 컨텍스트의 이름은 일반적으로 사용되지 않습니다.

## <a name="see-also"></a>참조
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
