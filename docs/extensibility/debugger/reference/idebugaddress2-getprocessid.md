---
title: IDebugAddress2::GetProcessID | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAddress2::GetProcessID
helpviewer_keywords:
- IDebugAddress2::GetProcessID method
ms.assetid: 2c18889d-074a-4b95-87b4-bf1a067f44ed
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 94873e9a9c05a0c5e9253ce53240ab6b4ca39064
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736583"
---
# <a name="idebugaddress2getprocessid"></a>IDebugAddress2::GetProcessID
이 [IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md) 인터페이스로 표시되는 개체를 소유하는 프로세스의 ID를 검색합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetProcessID (
   DWORD* pProcID
);
```

```csharp
int GetProcessID (
   out uint pProcID
);
```

## <a name="parameters"></a>매개 변수
`pProcID`\
【아웃】 프로세스 ID입니다.

## <a name="return-value"></a>Return Value
 성공하면 S_OK 반환합니다. 그렇지 않으면 오류 코드를 반환합니다.

## <a name="see-also"></a>참조
- [IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md)
