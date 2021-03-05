---
description: 지정 된 메시지 문자열을 디버거의 출력 창에 보냅니다.
title: IDebugIDECallback::D isplayMessage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugIDECallback::DisplayMessage
ms.assetid: c19b48ee-b370-4fce-91fe-f82bf1e63179
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ab7223d065df0bb77c2782ef7f66d14843a23f62
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102172547"
---
# <a name="idebugidecallbackdisplaymessage"></a>IDebugIDECallback::DisplayMessage
지정 된 메시지 문자열을 디버거의 출력 창에 보냅니다.

## <a name="syntax"></a>구문

```cpp
HRESULT DisplayMessage (
   LPCOLESTR szMessage
);
```

```csharp
int DisplayMessage (
   string szMessage
);
```

## <a name="parameters"></a>매개 변수
`szMessage`\
진행 디버거의 출력 창에 표시할 메시지 문자열입니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="see-also"></a>참고 항목
- [IDebugIDECallback](../../../extensibility/debugger/reference/idebugidecallback.md)
