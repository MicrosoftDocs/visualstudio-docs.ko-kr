---
description: 이 이벤트의 위치를 설명 하는 문서 컨텍스트를 가져옵니다.
title: 'IDebugCanStopEvent2:: GetDocumentContext | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2::GetDocumentContext
helpviewer_keywords:
- IDebugCanStopEvent2::GetDocumentContext
ms.assetid: 936a6c4e-30c5-4c7e-9ad5-910cc605a4b5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b58f5a45c30abcb7d1f11719ce131060526705c5
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102173513"
---
# <a name="idebugcanstopevent2getdocumentcontext"></a>IDebugCanStopEvent2::GetDocumentContext
이 이벤트의 위치를 설명 하는 문서 컨텍스트를 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetDocumentContext ( 
   IDebugDocumentContext2** ppDocCxt
);
```

```csharp
int GetDocumentContext ( 
   out IDebugDocumentContext2 ppDocCxt
);
```

## <a name="parameters"></a>매개 변수
`ppDocCxt`\
제한이 소스 파일 문서에서 현재 코드 위치에 해당 하는 위치를 나타내는 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) 인터페이스를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 일반적으로 문서 컨텍스트는 소스 파일의 위치로 간주할 수 있습니다.

 코드 지침을 중심으로 하는 코드 컨텍스트를 가져오려면 [GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md) 메서드를 호출 합니다.

## <a name="see-also"></a>참고 항목
- [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)
