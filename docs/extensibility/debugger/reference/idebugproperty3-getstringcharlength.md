---
description: 연결 된 속성의 문자열에 있는 문자 수를 반환 합니다.
title: 'IDebugProperty3:: GetStringCharLength | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::GetStringCharLength
helpviewer_keywords:
- IDebugProperty3::GetStringCharLength
ms.assetid: 89a8676b-6da9-4358-91c2-039bf33f99e4
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: eaf0792b6e0c2311b7eeb01f12b01a485739c6c9
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102171385"
---
# <a name="idebugproperty3getstringcharlength"></a>IDebugProperty3::GetStringCharLength
연결 된 속성의 문자열에 있는 문자 수를 반환 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetStringCharLength(
    ULONG *pLen
);
```

```csharp
int GetStringCharLength(
    out uint pLen
);
```

## <a name="parameters"></a>매개 변수

|매개 변수|설명|
|---------------|-----------------|
|`pLen`|제한이 속성의 문자열에 있는 문자 수를 반환 합니다.|

## <a name="return-value"></a>반환 값
성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
일반적으로이 메서드는 [Getstringchars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md) 메서드에 대 한 호출에 대 한 버퍼를 할당 하는 prelude 사용 됩니다.

## <a name="example"></a>예
다음 예제에서는 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) 인터페이스를 노출 하는 **cproperty** 개체에 대해이 메서드를 구현 하는 방법을 보여 줍니다.

```cpp
STDMETHODIMP CProperty::GetStringCharLength(ULONG *pLen)
{
    HRESULT hr = E_INVALIDARG;

    EVALFLAGS oldEVALFLAGS = m_EVALFLAGS;

    m_EVALFLAGS &= ~EVAL_NOFUNCEVAL;

    if (pLen)
    {
        DEBUG_PROPERTY_INFO dpInfo;
        dpInfo.bstrValue = NULL;
        ULONG ulen = 0;
        hr = GetPropertyInfo(DEBUGPROP_INFO_VALUE,10,DEFAULT_TIMEOUT,NULL,0,&dpInfo);
        if (hr == S_OK && dpInfo.bstrValue)
        {
            if (wcscmp(dpInfo.bstrValue,L"Nothing") == 0)
            {
                ulen = 0; //VSWhidbey#64815
            }
            else
            {
                ulen = ::SysStringLen(dpInfo.bstrValue);
                if( ulen > 2 &&
                    dpInfo.bstrValue[0] == L'"' &&
                    dpInfo.bstrValue[ulen-1] == L'"')
                {
                    ulen = ulen > 2 ? ulen - 2 : ulen; //remove two double quotes
                }
            }
        }
        ::SysFreeString(dpInfo.bstrValue);
        *pLen = ulen;
    }
    m_EVALFLAGS = oldEVALFLAGS;
    return hr;
}
```

## <a name="see-also"></a>참고 항목
- [GetStringChars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
