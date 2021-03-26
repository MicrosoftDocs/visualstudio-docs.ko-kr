---
description: 로드 되거나 언로드될 모듈을 가져옵니다.
title: 'IDebugModuleLoadEvent2:: GetModule | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModuleLoadEvent2::GetModule
helpviewer_keywords:
- IDebugModuleLoadEvent2::GetModule
ms.assetid: c86482bb-9ce5-4e63-bbe0-969b50169424
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4605b5eab9137fd918238143d8f0453f9f8c54b8
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105065374"
---
# <a name="idebugmoduleloadevent2getmodule"></a>IDebugModuleLoadEvent2::GetModule
로드 되거나 언로드될 모듈을 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetModule( 
   IDebugModule2** pModule,
   BSTR*           pbstrDebugMessage,
   BOOL*           pbLoad
);
```

```csharp
int GetModule( 
   out IDebugModule2 pModule,
   ref string        pbstrDebugMessage,
   ref int           pbLoad
);
```

## <a name="parameters"></a>매개 변수
`pModule`\
제한이 로드 또는 언로드 중인 모듈을 나타내는 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) 개체를 반환 합니다.

`pbstrDebugMessage`\
[in, out] 이 이벤트를 설명 하는 선택적 메시지를 반환 합니다. 이 매개 변수가 null 값 이면 메시지가 요청 되지 않습니다.

`pbLoad`\
[in, out] `TRUE`모듈이 로드 되 고 있는 경우 0이 아닌 ()이 고, `FALSE` 모듈이 언로드되고 있으면 ()입니다. 이 매개 변수가 null 값 이면 상태를 요청 하지 않습니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="see-also"></a>참조
- [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
