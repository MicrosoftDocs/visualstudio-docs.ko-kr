---
title: 'IDebugAddress2:: GetProcessID | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80736583"
---
# <a name="idebugaddress2getprocessid"></a>IDebugAddress2::GetProcessID
이 [IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md) 인터페이스가 나타내는 개체를 소유 하는 프로세스의 ID를 검색 합니다.

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
제한이 프로세스 ID입니다.

## <a name="return-value"></a>반환 값
 성공 하면 S_OK을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="see-also"></a>추가 정보
- [IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md)
