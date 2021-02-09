---
title: 'IDebugCoreServer3:: GetServerName | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::GetServerName
helpviewer_keywords:
- IDebugCoreServer3::GetServerName
ms.assetid: 0fc3fcf5-d6a3-4a00-bf14-458b8645714e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bb94f5a60b221728652ba05366777977a064cf6b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99880829"
---
# <a name="idebugcoreserver3getservername"></a>IDebugCoreServer3::GetServerName
서버의 이름을 검색 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetServerName(
   BSTR* pbstrName
);
```

```csharp
int GetServerName(
   out string pbstrName
);
```

## <a name="parameters"></a>매개 변수
`pbstrName`\
제한이 서버의 이름을 반환 합니다.

> [!NOTE]
> 호출자는 문자열을 해제 해야 합니다.

## <a name="return-value"></a>Return Value
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 서버 이름을 식별 하려면 [Getserverfriendlyname](../../../extensibility/debugger/reference/idebugcoreserver3-getserverfriendlyname.md) 메서드를 호출 합니다.

## <a name="see-also"></a>참고 항목
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
- [GetServerFriendlyName](../../../extensibility/debugger/reference/idebugcoreserver3-getserverfriendlyname.md)
