---
title: 아이디버그모듈3::겟심볼정보 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule3::GetSymbolInfo
helpviewer_keywords:
- GetSymbolInfo method
- IDebugModule3::GetSymbolInfo method
ms.assetid: dda5e8e1-6878-4aa9-9ee4-e7d0dcc11210
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3aafb28715f58eaba4499b47a2e1dee15b82ed14
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726896"
---
# <a name="idebugmodule3getsymbolinfo"></a>IDebugModule3::GetSymbolInfo
기호를 검색하는 경로 목록과 각 경로를 검색한 결과를 검색합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetSymbolInfo(
    SYMBOL_SEARCH_INFO_FIELDS  dwFields,
    MODULE_SYMBOL_SEARCH_INFO* pInfo
);
```

```csharp
int GetSymbolInfo(
    enum_SYMBOL_SEARCH_INFO_FIELDS dwFields,
    MODULE_SYMBOL_SEARCH_INFO[]    pinfo
);
```

## <a name="parameters"></a>매개 변수
`dwFields`\
【인】 채울 필드를 지정하는 [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) 열거형의 `pInfo` 플래그 조합입니다.

`pInfo`\
【아웃】 멤버를 지정된 정보로 채워야 하는 [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md) 구조입니다. null 값인 경우 이 메서드는 을 반환합니다. `E_INVALIDARG`

## <a name="return-value"></a>Return Value
메서드가 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

> [!NOTE]
> 구조에서 반환된 `MODULE_SYMBOL_SEARCH_INFO` 문자열은 반환되더라도 `S_OK` 비어 있을 수 있습니다. 이 경우 반환할 검색 정보가 없습니다.

## <a name="remarks"></a>설명
`MODULE_SYMBOL_SEARCH_INFO` 구조체의 `bstrVerboseSearchInfo` 필드가 비어 있지 않으면 검색된 경로 목록과 해당 검색 결과가 포함됩니다. 목록은 패스로 서식이 지정되고 그 다음에 타원("...")이 뒤따르고 결과가 표시됩니다. 둘 이상의 경로 결과 쌍이 있는 경우 각 쌍은 "\r\n"(캐리지 리턴/라인피드) 쌍으로 구분됩니다. 패턴은 다음과 같습니다.

\<경로> ... \<결과>\r\n\<경로>... \<결과>\r\n\<경로>... \<결과>

마지막 항목에는 \r\n 시퀀스가 없습니다.

## <a name="example"></a>예제
이 예제에서 이 메서드는 세 가지 다른 검색 결과 있는 세 개의 경로를 반환합니다. 각 줄은 캐리지 리턴/라인피드 쌍으로 종료됩니다. 예제 출력은 검색 결과를 단일 문자열로 인쇄합니다.

> [!NOTE]
> 상태 결과는 "..." 바로 다음에 있는 모든 것입니다. 줄의 끝까지.

```cpp
void ShowSymbolSearchResults(IDebugModule3 *pIDebugModule3)
{
    MODULE_SYMBOL_SEARCH_INFO ssi = { 0 };
    HRESULT hr;
    hr = pIDebugModule3->GetSymbolInfo(SSIF_VERBOSE_SEARCH_INFO,&ssi);
    if (SUCCEEDED(hr)) {
        CComBSTR searchInfo = ssi.bstrVerboseSearchInfo;
        if (searchInfo.Length() != 0) {
            std::wcout << (wchar_t *)(BSTR)searchInfo;
            std::wcout << std::endl;
        }
    }
}
```

**c:\기호\user32.pdb... 파일을 찾을 수 없습니다.** 
 **c:\winnt\기호\user32.pdb... 버전이 일치하지 않습니다.** 
 ** \\\기호\기호\user32.dll\0a8sd0ad8ad\user32.pdb... 기호가 로드되었습니다.**

## <a name="see-also"></a>참조

- [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md)
- [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md)
- [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)
