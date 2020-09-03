---
title: 'IDebugMemoryContext2:: GetName | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80727457"
---
# <a name="idebugmemorycontext2getname"></a>IDebugMemoryContext2::GetName
이 컨텍스트에 대 한 사용자가 표시할 때 사용할 이름을 검색 합니다.

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
제한이 메모리 컨텍스트의 이름을 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 메모리 컨텍스트의 이름은 일반적으로 사용 되지 않습니다.

## <a name="see-also"></a>추가 정보
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
