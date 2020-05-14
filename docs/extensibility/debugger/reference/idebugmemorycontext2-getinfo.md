---
title: 아이데버그메모리컨텍스트2::겟정보 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2::GetInfo
helpviewer_keywords:
- GetInfo method
- IDebugMemoryContext2::GetInfo method
ms.assetid: 08c7f091-1816-4d64-8834-f9ecaac5c58d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c190710afc9231662fa12c5552d6f73e0268b643
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727469"
---
# <a name="idebugmemorycontext2getinfo"></a>IDebugMemoryContext2::GetInfo
컨텍스트를 설명하는 [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) 구조를 검색합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetInfo( 
   CONTEXT_INFO_FIELDS dwFields,
   CONTEXT_INFO*       pInfo
);
```

```csharp
int GetInfo(
   enum_CONTEXT_INFO_FIELDS dwFields,
   CONTEXT_INFO[]           pinfo
);
```

## <a name="parameters"></a>매개 변수
`dwFields`\
【인】 [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info-fields.md) 구조의 필드를 입력할 CONTEXT_INFO_FIELDS 열거형의 [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) 플래그 조합입니다.

`pInfo`\
【인, 아웃】 채워진 `CONTEXT_INFO` 구조입니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="see-also"></a>참조
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
- [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md)
- [Context_info](../../../extensibility/debugger/reference/context-info.md)
