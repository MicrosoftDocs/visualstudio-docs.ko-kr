---
title: 아이디버그문서컨텍스트2::겟소스레인지 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::GetSourceRange
helpviewer_keywords:
- IDebugDocumentContext2::GetSourceRange
ms.assetid: 5903c75e-5390-4d13-9314-1ee276255313
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 782cf230c38af77da09b49f69c093e2e95bf7199
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731793"
---
# <a name="idebugdocumentcontext2getsourcerange"></a>IDebugDocumentContext2::GetSourceRange
이 문서 컨텍스트의 소스 코드 범위를 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetSourceRange( 
   TEXT_POSITION* pBegPosition,
   TEXT_POSITION* pEndPosition
);
```

```csharp
int GetSourceRange( 
   TEXT_POSITION[] pBegPosition,
   TEXT_POSITION[] pEndPosition
);
```

## <a name="parameters"></a>매개 변수
`pBegPosition`\
【인, 아웃】 시작 위치로 채워진 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) 구조입니다. 이 정보가 필요하지 않은 경우 이 인수를 null 값으로 설정합니다.

`pEndPosition`\
【인, 아웃】 끝 위치로 채워진 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) 구조입니다. 이 정보가 필요하지 않은 경우 이 인수를 null 값으로 설정합니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 소스 범위는 현재 문부터 코드를 제공한 이전 문 바로 직후까지 소스 코드의 전체 범위입니다. 소스 범위는 일반적으로 주석을 비롯한 소스 문을 디스어셈블리 창의 코드와 혼합하는 데 사용됩니다.

 이 문서 컨텍스트에 포함된 코드 문의 범위만 얻으려면 GetStatementRange 메서드를 [호출합니다.](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)

## <a name="see-also"></a>참조
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
