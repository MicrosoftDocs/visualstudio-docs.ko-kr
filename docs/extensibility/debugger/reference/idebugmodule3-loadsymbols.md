---
description: 현재 모듈에 대 한 기호를 로드 합니다.
title: 'IDebugModule3:: LoadSymbols | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule3::LoadSymbols
helpviewer_keywords:
- IDebugModule3::LoadSymbols
ms.assetid: 7548c8c1-cbc6-48aa-a845-19058d4a85bb
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0612be8ffdde8a942331a89e08298f71414a4c76
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102164827"
---
# <a name="idebugmodule3loadsymbols"></a>IDebugModule3::LoadSymbols
현재 모듈에 대 한 기호를 로드 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT LoadSymbols(
   void
);
```

```csharp
int LoadSymbols();
```

## <a name="return-value"></a>Return Value
 메서드가 성공하면 `S_OK`가 반환되고, 그렇지 않으면 오류 코드가 반환됩니다.

## <a name="remarks"></a>설명
 이 메서드는 현재 검색 경로에서 기호를 로드 합니다 .이 기호는 [Setsymbol path](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md) 메서드를 호출 하 여 변경할 수 있습니다.

 이 메서드는 [ReloadSymbols_Deprecated](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md) 방법 보다 선호 됩니다.

## <a name="see-also"></a>참고 항목
- [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)
- [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)
