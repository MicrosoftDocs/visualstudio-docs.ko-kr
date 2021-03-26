---
description: 사용되지 않습니다. 이 모듈에 대 한 기호를 다시 로드 합니다.
title: 'IDebugModule2:: ReloadSymbols_Deprecated | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule2::ReloadSymbols
helpviewer_keywords:
- IDebugModule2::ReloadSymbols method
ms.assetid: 0f9f0133-7d58-4cd9-a6ca-1141e095749d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5dfcd1edd92048cde6da6cc195c3e0ba8f1cd392
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105065712"
---
# <a name="idebugmodule2reloadsymbols_deprecated"></a>IDebugModule2::ReloadSymbols_Deprecated
사용되지 않습니다. 사용 하지 마십시오. 이 모듈에 대 한 기호를 다시 로드 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT ReloadSymbols( 
   LPCOLESTR pszUrlToSymbols,
   BSTR*     pbstrDebugMessage
);
```

```csharp
int ReloadSymbols( 
   string     pszUrlToSymbols,
   out string pbstrDebugMessage
);
```

## <a name="parameters"></a>매개 변수
`pszUrlToSymbols`\
진행 기호 저장소에 대 한 경로입니다.

`pbstrDebugMessage`\
제한이 모듈 창에서 모듈 이름 오른쪽에 표시 되는 상태 메시지 (예: 상태 또는 오류 메시지)를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다. 디버그 엔진은 항상를 반환 해야 합니다 `E_FAIL` .

## <a name="remarks"></a>설명
 이 메서드는 더 이상 지원 되지 않습니다. 대신 [loadsymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md) 메서드를 구현 합니다.

## <a name="see-also"></a>참조
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
- [LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)
