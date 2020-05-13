---
title: MODULE_SYMBOL_SEARCH_INFO | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_SYMBOL_SEARCH_INFO
helpviewer_keywords:
- MODULE_SYMBOL_SEARCH_INFO structure
ms.assetid: 432aff03-08a5-4c5a-b2d5-e212090fc70a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5f15587759c4f665d1593d1298c47459a0e64aac
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714248"
---
# <a name="module_symbol_search_info"></a>MODULE_SYMBOL_SEARCH_INFO

검색된 기호 검색 경로에 대한 상태 정보를 포함합니다.

## <a name="syntax"></a>구문

```cpp
typedef struct _tagSYMBOL_SEARCH_INFO
{
    SYMBOL_SEARCH_INFO_FIELDS dwValidFields;
    BSTR                      bstrVerboseSearchInfo;
} MODULE_SYMBOL_SEARCH_INFO;
```

```csharp
public struct MODULE_SYMBOL_SEARCH_INFO {
    public uint   dwValidFields;
    public string bstrVerboseSearchInfo;
}
```

## <a name="members"></a>멤버

`dwValidFields`\
이 구조에 설명된 검색 정보의 종류를 지정하는 [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) 열거형의 플래그 조합입니다.

`bstrVerboseSearchInfo`\
검색 경로 및 결과가 단일 문자열로 연결됩니다.

## <a name="remarks"></a>설명

이 구조는 [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md) 메서드에 대 한 호출에서 반환 됩니다.

필드가 `bstrVerboseSearchInfo` 비어 있지 않으면 검색된 경로 목록과 해당 검색 결과가 포함됩니다. 목록은 패스로 서식이 지정되고 그 다음에 타원("...")이 뒤따르고 결과가 표시됩니다. 둘 이상의 경로 결과 쌍이 있는 경우 각 쌍은 "\r\n"(캐리지 리턴/라인피드) 쌍으로 구분됩니다. 패턴은 다음과 같습니다.

\<경로> ... \<결과>\r\n\<경로>... \<결과>\r\n\<경로>... \<결과>

마지막 항목에는 \r\n 시퀀스가 없습니다.

다음은 표준으로 `bstrVerboseSearchInfo` 전송된 가능한 문자열입니다.

`c:\symbols\user32.pdb... File not found.`

`c:\winnt\symbols\user32.pdb... Version does not match.`

`\\symbols\symbols\user32.dll\0a8sd0ad8ad\user32.pdb... Symbols loaded.`

## <a name="requirements"></a>요구 사항

헤더: msdbg.h

네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조

- [클래스 및 공용 구조체](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)
