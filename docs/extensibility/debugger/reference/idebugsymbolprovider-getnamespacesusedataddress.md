---
title: 'Idebug Provider:: GetNamespacesUsedAtAddress | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetNamespacesUsedAtAddress
helpviewer_keywords:
- IDebugSymbolProvider::GetNamespacesUsedAtAddress method
ms.assetid: 392de54b-9af0-4567-953b-1b41acd1e05c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a259f813d2bfbcb8ec92b039d44af74e431752ec
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99880218"
---
# <a name="idebugsymbolprovidergetnamespacesusedataddress"></a>IDebugSymbolProvider::GetNamespacesUsedAtAddress
이 메서드는 디버그 주소와 연결 된 네임 스페이스에 대 한 열거자를 만듭니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetNamespacesUsedAtAddress( 
   IDebugAddress*     pAddress,
   IEnumDebugFields** ppEnum
);
```

```csharp
int GetNamespacesUsedAtAddress(
   IDebugAddress        pAddress,
   out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>매개 변수
`pAddress`\
진행 디버그 주소입니다.

`ppEnum`\
제한이 네임 스페이스에 대 한 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) 열거자를 반환 합니다.

## <a name="return-value"></a>Return Value
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 지정 된 디버그 주소와 연결 된 네임 스페이스 (예: 중첩 된 네임 스페이스 또는 여러 개)가 있을 수 있습니다 `using` .

## <a name="see-also"></a>참고 항목
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
