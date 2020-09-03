---
title: 'IEnumDebugAddresses:: GetCount | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugAddresses::GetCount
helpviewer_keywords:
- IEnumDebugAddresses::GetCount method
ms.assetid: f2ca8ff8-539f-457c-83f8-9bbf97618065
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4610613b6fef5e80ae0fd36c3548b4dfdcbc8591
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80717683"
---
# <a name="ienumdebugaddressesgetcount"></a>IEnumDebugAddresses::GetCount
이 메서드는 열거형의 요소 수를 반환 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetCount(
   [out] ULONG* pcelt
);
```

```csharp
int GetCount(
   out uint pcelt
);
```

## <a name="parameters"></a>매개 변수
`pcelt`\
제한이 열거형의 요소 수를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 이 메서드는 다음, 복제, 건너뛰기 및 다시 설정을 구현 해야 하도록 지정 하는 일반적인 COM 열거 인터페이스의 일부가 아닙니다.

## <a name="see-also"></a>추가 정보
- [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)
