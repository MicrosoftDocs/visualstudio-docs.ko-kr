---
title: 아이디버그코어서버3:GetServer친화적네임 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::GetServerFriendlyName
helpviewer_keywords:
- IDebugCoreServer3::GetServerFriendlyName
ms.assetid: 7035b904-b3d7-4d9b-98d9-65714b8a8b9f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: eec30783041a1240d8f85815c06f4ca60729a484
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732888"
---
# <a name="idebugcoreserver3getserverfriendlyname"></a>IDebugCoreServer3::GetServerFriendlyName
서버에 대 한 친한 이름을 검색 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetServerFriendlyName(
   BSTR* pbstrName
);
```

```csharp
int GetServerFriendlyName(
   out string pbstrName
);
```

## <a name="parameters"></a>매개 변수
`pbstrName`\
【아웃】 서버에 대한 친숙한 이름을 반환합니다.

> [!NOTE]
> 호출자는 문자열을 해제할 책임이 있습니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 사용자가 시작한 서버의 경우 이 메서드에서 반환하는 이름은 서버의 전체 이름입니다. 자동 실행 서버의 경우 이름은 서버가 실행 중인 컴퓨터의 이름입니다.

 컴퓨터 지향 이름의 경우 [GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md) 메서드를 호출합니다.

## <a name="see-also"></a>참조
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
- [GetServer이름](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)
