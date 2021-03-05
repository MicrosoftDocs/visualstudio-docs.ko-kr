---
description: 이 스택 프레임의 문서 컨텍스트를 가져옵니다.
title: 'IDebugStackFrame2:: GetDocumentContext | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetDocumentContext
helpviewer_keywords:
- IDebugStackFrame2::GetDocumentContext
ms.assetid: 69e81439-1238-4f18-9028-6fd1c1ba5e4a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9e1645cb7daebb9dc344085d13a2fecb87fc0106
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102145978"
---
# <a name="idebugstackframe2getdocumentcontext"></a>IDebugStackFrame2::GetDocumentContext
이 스택 프레임의 문서 컨텍스트를 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetDocumentContext ( 
   IDebugDocumentContext2** ppCxt
);
```

```csharp
int GetDocumentContext ( 
   out IDebugDocumentContext2 ppCxt
);
```

## <a name="parameters"></a>매개 변수
`ppCxt`\
제한이 소스 문서에서 현재 위치를 나타내는 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) 개체를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 이 메서드는 [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md) 메서드를 호출한 다음 코드 컨텍스트에서 [getdocumentcontext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md) 메서드를 호출 하는 것 보다 빠릅니다. 그러나 모든 디버그 엔진 (DE)이이 메서드를 구현 하는 것은 아닙니다.

## <a name="see-also"></a>참고 항목
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)
