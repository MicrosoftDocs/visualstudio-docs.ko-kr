---
title: 'IDebugDocumentContext2:: GetDocument | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::GetDocument
helpviewer_keywords:
- IDebugDocumentContext2::GetDocument
ms.assetid: c6d46c5d-ade8-4dc8-9862-8fc7876658c4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6bb93fe3efb4bc114cf583e8e2c066c337109d12
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80731829"
---
# <a name="idebugdocumentcontext2getdocument"></a>IDebugDocumentContext2::GetDocument
이 문서 컨텍스트를 포함 하는 문서를 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetDocument( 
   IDebugDocument2** ppDocument
);
```

```csharp
int GetDocument( 
   out IDebugDocument2 ppDocument
);
```

## <a name="parameters"></a>매개 변수
`ppDocument`\
제한이 이 문서 컨텍스트를 포함 하는 문서를 나타내는 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) 개체를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 이 메서드는 IDE에 직접 문서를 제공 하는 디버그 엔진에 대 한 것입니다. 그렇지 않으면이 메서드는를 반환 해야 `E_NOTIMPL` 합니다.

## <a name="see-also"></a>추가 정보
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
