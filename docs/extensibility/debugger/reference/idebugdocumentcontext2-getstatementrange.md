---
title: IDebugDocument컨텍스트2:GetStatementRange | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::GetStatementRange
helpviewer_keywords:
- IDebugDocumentContext2::GetStatementRange
ms.assetid: bc94851a-0ec4-47ea-99c7-0a585e54e726
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 50e521d98f10477d56dfece30e20fd000b87b632
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731775"
---
# <a name="idebugdocumentcontext2getstatementrange"></a>IDebugDocumentContext2::GetStatementRange
문서 컨텍스트의 파일 문 범위를 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetStatementRange(
    TEXT_POSITION* pBegPosition,
    TEXT_POSITION* pEndPosition
);
```

```csharp
int GetStatementRange(
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
문 범위는 이 문서 컨텍스트가 참조하는 코드를 기여한 줄의 범위입니다.

이 문서 컨텍스트 내에서 소스 코드(주석 포함)의 범위를 얻으려면 GetSourceRange 메서드를 [호출합니다.](../../../extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange.md)

## <a name="example"></a>예제
다음 예제에서는 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) `CDebugContext` 인터페이스를 노출 하는 간단한 개체에 대 한이 메서드를 구현 하는 방법을 보여 줍니다. 이 예제에서는 시작 위치가 null 값이 아닌 경우에만 끝 위치를 채웁니다.

```cpp
HRESULT CDebugContext::GetStatementRange(TEXT_POSITION* pBegPosition,
                                         TEXT_POSITION* pEndPosition)
{
    HRESULT hr;

    // Check for a valid beginning position argument pointer.
    if (pBegPosition)
    {
        // Copy the member TEXT_POSITION into the local pBegPosition.
        memcpy(pBegPosition, &m_pos, sizeof (TEXT_POSITION));

        // Check for a valid ending position argument pointer.
        if (pEndPosition)
        {
            // Copy the member TEXT_POSITION into the local pEndPosition.
            memcpy(pEndPosition, &m_pos, sizeof (TEXT_POSITION));
        }
        hr = S_OK;
    }
    else
    {
        hr = E_INVALIDARG;
    }

    return hr;
}
```

## <a name="see-also"></a>참조
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [GetSourceRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
