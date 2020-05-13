---
title: IDebugCode컨텍스트2::GetDocument컨텍스트 | 마이크로 소프트 문서
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734339"
---
# <a name="idebugcodecontext2getdocumentcontext"></a>IDebugCodeContext2::GetDocumentContext
이 코드 컨텍스트에 해당하는 문서 컨텍스트를 가져옵니다. 문서 컨텍스트는 이 명령을 생성한 소스 코드에 해당하는 소스 파일의 위치를 나타냅니다.

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
【아웃】 코드 컨텍스트에 해당하는 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) 개체를 반환합니다. 반환되는 경우 `S_OK` ths는 비-`null`

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다. 디버그 엔진은 코드 컨텍스트에 `E_FAIL` `out` 연결된 소스 `null` 위치가 없는 경우와 같이 매개 변수가 있는 경우와 같은 오류 코드를 반환해야 합니다.

## <a name="remarks"></a>설명
 일반적으로 문서 컨텍스트는 소스 파일의 위치로 생각할 수 있으며 코드 컨텍스트는 실행 스트림의 코드 명령의 위치입니다.

## <a name="see-also"></a>참조
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
