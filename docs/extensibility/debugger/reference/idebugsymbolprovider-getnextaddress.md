---
title: 아이디버그 심볼공급자::GetNextAddress | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetNextAddress
helpviewer_keywords:
- IDebugSymbolProvider::GetNextAddress method
ms.assetid: 704eeb94-cb13-49d1-82b6-7d83ed0f19c0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9b314ab7006d6bbe65136451aeee6c5200cf7980
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719199"
---
# <a name="idebugsymbolprovidergetnextaddress"></a>IDebugSymbolProvider::GetNextAddress
메서드에서 지정된 디버그 주소를 따르는 디버그 주소를 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetNextAddress( 
   IDebugAddress*  pAddress,
   BOOL            fStatementOnly,
   IDebugAddress** ppAddress
);
```

```csharp
int GetNextAddress( 
   IDebugAddress     pAddress,
   bool              fStatementOnly,
   out IDebugAddress ppAddress
);
```

## <a name="parameters"></a>매개 변수
`pAddress`\
【인】 주어진 디버그 주소.

`fStatementOnly`\
【인】 TRUE인 경우 디버그 주소를 단일 문으로 제한합니다.

`ppAddress`\
【아웃】 다음 디버그 주소를 반환합니다.

## <a name="return-value"></a>Return Value
 일반적으로 S_OK `HRESULT`유효한 을 반환합니다.

## <a name="see-also"></a>참조
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
