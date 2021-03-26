---
description: 이 문서 컨텍스트를 포함 하는 문서의 표시할 때 나타나는 이름을 가져옵니다.
title: 'IDebugDocumentContext2:: GetName | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::GetName
helpviewer_keywords:
- IDebugDocumentContext2::GetName
ms.assetid: 546c5b2e-f166-4edb-9e61-57d797ca98a1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 96f0130b09a98c4064f53337aaa2e54ad7ed887b
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105066609"
---
# <a name="idebugdocumentcontext2getname"></a>IDebugDocumentContext2::GetName
이 문서 컨텍스트를 포함 하는 문서의 표시할 때 나타나는 이름을 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetName(
    GETNAME_TYPE gnType,
    BSTR*        pbstrFileName
);
```

```csharp
int GetName(
    enum_GETNAME_TYPE  gnType,
    out string         pbstrFileName
);
```

## <a name="parameters"></a>매개 변수
`gnType`\
진행 반환할 이름 유형을 지정 하는 [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md) 열거형의 값입니다.

`pbstrFileName`\
제한이 파일의 이름을 반환 합니다.

## <a name="return-value"></a>반환 값
성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
문서 컨텍스트를 문서 이름 자체를 저장 하도록 작성 하지 않는 한이 메서드는 일반적으로 [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md) 메서드에 대 한 호출을 전달 합니다 (예제 표시).

## <a name="example"></a>예제
다음 예제에서는 `CDebugContext` [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) 인터페이스를 노출 하는 간단한 개체에 대해이 메서드를 구현 하는 방법을 보여 줍니다.

```cpp
HRESULT CDebugContext::GetName(GETNAME_TYPE gnType, BSTR* pbstrFileName)
{
    HRESULT hr;

    // Check for a valid file name argument.
    if (pbstrFileName)
    {
        *pbstrFileName = NULL;

        switch (gnType)
        {
            case GN_NAME:
            case GN_FILENAME:
            {
                // Copy the member file name into the local file name.
                *pbstrFileName = SysAllocString(m_sbstrFileName);
                // Check for successful copy.
                hr = (*pbstrFileName) ? S_OK : E_OUTOFMEMORY;
                break;
            }
            default:
            {
                hr = E_FAIL;
                break;
            }
        }
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
- [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md)
