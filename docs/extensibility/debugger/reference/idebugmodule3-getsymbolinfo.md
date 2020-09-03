---
title: 'IDebugModule3:: Get기호 정보 | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80726896"
---
# <a name="idebugmodule3getsymbolinfo"></a>IDebugModule3::GetSymbolInfo
각 경로를 검색 한 결과 뿐만 아니라 기호를 검색 하는 경로 목록을 검색 합니다.

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
진행 채울 필드를 지정 하는 [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) 열거형의 플래그 조합입니다 `pInfo` .

`pInfo`\
제한이 지정 된 정보를 사용 하 여 해당 멤버를 채울 [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md) 구조체입니다. 이 값이 null 이면이 메서드는를 반환 `E_INVALIDARG` 합니다.

## <a name="return-value"></a>반환 값
메서드가 성공 하면가 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

> [!NOTE]
> 가 반환 되는 경우에도 구조체에서 반환 된 문자열은 `MODULE_SYMBOL_SEARCH_INFO` 비어 있을 수 있습니다 `S_OK` . 이 경우 반환할 검색 정보가 없습니다.

## <a name="remarks"></a>설명
`bstrVerboseSearchInfo`구조체의 필드가 `MODULE_SYMBOL_SEARCH_INFO` 비어 있지 않으면 검색 된 경로 및 해당 검색의 결과 목록을 포함 합니다. 목록의 형식은 경로를 사용 하 고 그 뒤에 줄임표 ("...")가 오고 그 뒤에 결과가 나옵니다. 경로 결과 쌍이 둘 이상 있는 경우 각 쌍은 "\r\n" (캐리지 리턴/줄 바꿈) 쌍으로 구분 됩니다. 패턴은 다음과 같습니다.

\<path>...\<result> \r\n \<path> \<result> ... \r\n \<path> ...\<result>

마지막 항목에는 \r\n 시퀀스가 없습니다.

## <a name="example"></a>예
이 예제에서이 메서드는 세 개의 다른 검색 결과가 포함 된 세 개의 경로를 반환 합니다. 각 줄은 캐리지 리턴/줄 바꿈 쌍으로 종료 됩니다. 예제 출력에서는 검색 결과를 단일 문자열로 인쇄 하기만 합니다.

> [!NOTE]
> 상태 결과는 "..." 바로 다음에 나오는 모든 항목입니다. 줄의 끝까지

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

**c:\symbols\user32.pdb... 파일을 찾을 수 없습니다.** 
 **c:\winnt\symbols\user32.pdb... 버전이 일치 하지 않습니다.** 
 ** \\\symbols\symbols\user32.dll \0a8sd0ad8ad\user32.pdb... 기호가 로드 되었습니다.**

## <a name="see-also"></a>추가 정보

- [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md)
- [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md)
- [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)
