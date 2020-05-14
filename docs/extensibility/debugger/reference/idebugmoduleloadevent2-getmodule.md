---
title: IDebugModule로드이벤트2::GetModule | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModuleLoadEvent2::GetModule
helpviewer_keywords:
- IDebugModuleLoadEvent2::GetModule
ms.assetid: c86482bb-9ce5-4e63-bbe0-969b50169424
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b90547709e5524ce005b0598b0b8d482cfecf173
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726729"
---
# <a name="idebugmoduleloadevent2getmodule"></a>IDebugModuleLoadEvent2::GetModule
로드 또는 언로드 중인 모듈을 가져옵니다.

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
【아웃】 로드 또는 언로드되는 모듈을 나타내는 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) 개체를 반환합니다.

`pbstrDebugMessage`\
【인, 아웃】 이 이벤트를 설명하는 선택적 메시지를 반환합니다. 이 매개 변수가 null 값인 경우 메시지가 요청되지 않습니다.

`pbLoad`\
【인, 아웃】 모듈이`TRUE`로드중이면 () ()`FALSE`모듈이 언로드중이면 이 매개 변수가 null 값인 경우 상태가 요청되지 않습니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="see-also"></a>참조
- [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
