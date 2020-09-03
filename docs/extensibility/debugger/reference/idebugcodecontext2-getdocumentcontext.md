---
title: 'IDebugCodeContext2:: GetDocumentContext | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCodeContext2::GetDocumentContext
helpviewer_keywords:
- IDebugCodeContext2::GetDocumentContext
ms.assetid: d552cc92-963f-43c1-949f-ae6b63a427b8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 46510ce794ea30fdd365a77007b962a1eafd5d31
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80734339"
---
# <a name="idebugcodecontext2getdocumentcontext"></a>IDebugCodeContext2::GetDocumentContext
이 코드 컨텍스트에 해당 하는 문서 컨텍스트를 가져옵니다. 문서 컨텍스트는이 명령을 생성 한 소스 코드에 해당 하는 소스 파일의 위치를 나타냅니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetDocumentContext( 
   IDebugDocumentContext2** ppSrcCxt
);
```

```csharp
int GetDocumentContext( 
   out IDebugDocumentContext2 ppSrcCxt
);
```

## <a name="parameters"></a>매개 변수
`ppSrcCxt`\
제한이 코드 컨텍스트에 해당 하는 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) 개체를 반환 합니다. `S_OK`이 반환 되는 경우는이 아니어야 `null` 합니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다. 디버그 엔진은 `E_FAIL` `out` `null` 코드 컨텍스트에 연결 된 소스 위치가 없는 경우와 같이 매개 변수가와 같은 오류 코드를 반환 해야 합니다.

## <a name="remarks"></a>설명
 일반적으로 문서 컨텍스트는 소스 파일의 위치로 간주할 수 있으며 코드 컨텍스트는 실행 스트림에서 코드 명령의 위치입니다.

## <a name="see-also"></a>추가 정보
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
