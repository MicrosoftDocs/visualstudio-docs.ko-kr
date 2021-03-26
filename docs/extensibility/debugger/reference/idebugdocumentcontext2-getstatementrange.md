---
description: 문서 컨텍스트의 파일 문 범위를 가져옵니다.
title: 'IDebugDocumentContext2:: GetStatementRange | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::GetStatementRange
helpviewer_keywords:
- IDebugDocumentContext2::GetStatementRange
ms.assetid: bc94851a-0ec4-47ea-99c7-0a585e54e726
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 37e08385c541c00e4f15f833487fc69b3acf12ce
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105066583"
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
[in, out] 시작 위치로 채워진 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) 구조체입니다. 이 정보가 필요 하지 않은 경우이 인수를 null 값으로 설정 합니다.

`pEndPosition`\
[in, out] 끝 위치로 채워진 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) 구조체입니다. 이 정보가 필요 하지 않은 경우이 인수를 null 값으로 설정 합니다.

## <a name="return-value"></a>반환 값
성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
문 범위는이 문서 컨텍스트가 참조 하는 코드를 제공 하는 줄의 범위입니다.

이 문서 컨텍스트 내에서 소스 코드 범위 (주석 포함)를 가져오려면 [GetSourceRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange.md) 메서드를 호출 합니다.

## <a name="example"></a>예제
다음 예제에서는 `CDebugContext` [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) 인터페이스를 노출 하는 간단한 개체에 대해이 메서드를 구현 하는 방법을 보여 줍니다. 이 예에서는 시작 위치가 null 값이 아닌 경우에만 끝 위치를 채웁니다.

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
