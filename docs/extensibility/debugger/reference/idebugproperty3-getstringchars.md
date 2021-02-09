---
title: 'IDebugProperty3:: GetStringChars | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::GetStringChars
helpviewer_keywords:
- IDebugProperty3::GetStringChars
ms.assetid: 832c37f3-85cb-4227-8ab2-f27a80eafe90
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8b188b386dea7279530e186073847e26915af63d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99897284"
---
# <a name="idebugproperty3getstringchars"></a>IDebugProperty3::GetStringChars
이 속성과 연결 된 문자열을 검색 하 여 사용자가 제공 하는 버퍼에 저장 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetStringChars(
    ULONG  buflen,
    WCHAR* rgString,
    ULONG* pceltFetched
);
```

```csharp
int GetStringChars(
    uint       buflen,
    out string rgString,
    out uint   pceltFetched
);
```

## <a name="parameters"></a>매개 변수
`buflen`\
진행 사용자가 제공한 버퍼에 포함할 수 있는 최대 문자 수입니다.

`rgString`\
제한이 문자열을 반환 합니다.

 [C + +만] `rgString` 은 문자열의 유니코드 문자를 받는 버퍼에 대 한 포인터입니다. 이 버퍼의 크기는 바이트이 하 여야 합니다 `buflen` .

`pceltFetched`\
제한이 실제로 버퍼에 저장 된 문자 수가 반환 됩니다. `NULL`C + +에 있을 수 있습니다.

## <a name="return-value"></a>Return Value
성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
C + +에서는 버퍼가 유니코드 문자 길이 이상으로 유지 되도록 주의를 기울여야 합니다 `buflen` . 유니코드 문자는 2 바이트 길이입니다.

> [!NOTE]
> C + +에서 반환 된 문자열에는 종료 null 문자가 포함 되지 않습니다. 지정 된 경우 `pceltFetched` 는 문자열의 문자 수를 지정 합니다.

## <a name="example"></a>예제

```cpp
CStringW RetrievePropertyString(IDebugProperty2 *pPropInfo)
{
    CStringW returnString = L"";
    CComQIPtr<IDebugProperty3> pProp3 = pPropInfo->pProperty;
    If (pProp3 != NULL) {
        ULONG dwStrLen = 0;
        HRESULT hr;
        hr = pProp3->GetStringCharLength(&dwStrLen);
        if (SUCCEEDED(hr) && dwStrLen > 0) {
            ULONG dwRead;
            CStrBufW buf(returnString,dwStrLen,CStrBuf::SET_LENGTH);
            hr = pProp3->GetStringChars(dwStrLen,
                                        reinterpret_cast<WCHAR*>(static_cast<CStringW::PXSTR>(buf)),
                                        &dwRead);
        }
    }
    return(returnString);
}
```

## <a name="see-also"></a>참고 항목
- [GetStringCharLength](../../../extensibility/debugger/reference/idebugproperty3-getstringcharlength.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
