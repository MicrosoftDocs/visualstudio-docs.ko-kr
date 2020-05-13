---
title: IDebugModule2::ReloadSymbols_Deprecated | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule2::ReloadSymbols
helpviewer_keywords:
- IDebugModule2::ReloadSymbols method
ms.assetid: 0f9f0133-7d58-4cd9-a6ca-1141e095749d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e776434e17d90cd2c61c926bbf0100a44ecc524b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726924"
---
# <a name="idebugmodule2reloadsymbols_deprecated"></a>IDebugModule2::ReloadSymbols_Deprecated
사용되지 않습니다. 사용하지 마십시오. 이 모듈의 기호를 다시 로드합니다.

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
【인】 기호 저장소에 대한 경로입니다.

`pbstrDebugMessage`\
【아웃】 모듈 창의 모듈 이름 오른쪽에 표시되는 상태 또는 오류 메시지와 같은 정보 메시지를 반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다. 디버그 엔진은 항상 `E_FAIL`반환해야 합니다.

## <a name="remarks"></a>설명
 이 메서드는 더 이상 지원되지 않습니다. 대신 [Load Symbols 메서드를 구현합니다.](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)

## <a name="see-also"></a>참조
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
- [LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)
