---
title: 아이디버그프로퍼티3:겟스트링차 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::GetStringChars
helpviewer_keywords:
- IDebugProperty3::GetStringChars
ms.assetid: 832c37f3-85cb-4227-8ab2-f27a80eafe90
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 693a29bc30ef206428713ace36275389de1b7f0a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721088"
---
# <a name="idebugproperty3getstringchars"></a>IDebugProperty3::GetStringChars
이 속성과 연결된 문자열을 검색하고 사용자 제공 버퍼에 저장합니다.

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
【인】 사용자가 제공한 버퍼가 보유할 수 있는 최대 문자 수입니다.

`rgString`\
【아웃】 문자열을 반환합니다.

 [C++ `rgString` 전용]은 문자열의 유니코드 문자를 수신하는 버퍼에 대한 포인터입니다. 이 버퍼의 크기는 바이트가 아닌 최소 `buflen` 문자여야 합니다.

`pceltFetched`\
【아웃】 버퍼에 실제로 저장된 문자 수가 반환되는 위치입니다. (C `NULL` ++에 있을 수 있습니다.)

## <a name="return-value"></a>Return Value
성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
C++에서는 버퍼가 유니코드 문자 가 적어도 `buflen` 긴지 확인하려면 주의해야 합니다. 유니코드 문자는 2바이트 길이입니다.

> [!NOTE]
> C++에서 반환된 문자열에는 종료 null 문자가 포함되지 않습니다. 주어진 `pceltFetched` 경우 문자열의 문자 수를 지정합니다.

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

## <a name="see-also"></a>참조
- [GetStringCharLength](../../../extensibility/debugger/reference/idebugproperty3-getstringcharlength.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
