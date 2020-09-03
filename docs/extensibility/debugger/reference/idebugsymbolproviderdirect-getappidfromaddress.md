---
title: 'Idebug심볼 Providerdirect:: GetAppIDFromAddress | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSymbolProviderDirect::GetAppIDFromAddress
- GetAppIDFromAddress
ms.assetid: d76a0f36-79c4-4c58-9db3-880b00d11610
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: df1dbea23cf29809c5f504359ebf02b40c14e6e2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80719162"
---
# <a name="idebugsymbolproviderdirectgetappidfromaddress"></a>IDebugSymbolProviderDirect::GetAppIDFromAddress
디버그 주소가 지정 된 경우 응용 프로그램 도메인 식별자를 검색 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetAppIDFromAddress(
   IDebugAddress* pAddress,
   DWORD*         pAppID
);
```

```csharp
int GetAppIDFromAddress(
   IDebugAddress pAddress,
   out uint      pAppID
);
```

## <a name="parameters"></a>매개 변수
`pAddress`\
진행 [Idebugaddress](../../../extensibility/debugger/reference/idebugaddress.md) 인터페이스로 표시 되는 디버그 주소입니다.

`pAppID`\
제한이 응용 프로그램 도메인의 식별자입니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="see-also"></a>추가 정보
- [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)
