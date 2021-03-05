---
description: 핵심 서버가 실행 되 고 있는 컴퓨터의 이름을 가져옵니다.
title: 'IDebugCoreServer2:: GetMachineName | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer2::GetName
helpviewer_keywords:
- IDebugCoreServer2::GetName
ms.assetid: 693bd794-7215-4f07-8651-b57366d39953
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1fcde7bcc59f38aba5369059e1aeb31a61a0e8cd
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102163189"
---
# <a name="idebugcoreserver2getmachinename"></a>IDebugCoreServer2::GetMachineName
핵심 서버가 실행 되 고 있는 컴퓨터의 이름을 가져옵니다.

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
제한이 컴퓨터의 이름을 포함 하는 문자열을 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="see-also"></a>참고 항목
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
