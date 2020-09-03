---
title: MODULE_SYMBOL_SEARCH_INFO | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- MODULE_SYMBOL_SEARCH_INFO
helpviewer_keywords:
- MODULE_SYMBOL_SEARCH_INFO structure
ms.assetid: 432aff03-08a5-4c5a-b2d5-e212090fc70a
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e2cfbaf8c3756bf758956d1f1e5964d8e9f8f0c8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205177"
---
# <a name="module_symbol_search_info"></a>MODULE_SYMBOL_SEARCH_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

검색 된 기호 검색 경로에 대 한 상태 정보를 포함 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
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
  
#### <a name="parameters"></a>매개 변수  
 `dwValidFields`  
 이 구조에서 설명 하는 검색 정보의 종류를 지정 하는 [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) 열거형의 플래그 조합입니다.  
  
 `bstrVerboseSearchInfo`  
 단일 문자열로 연결 된 검색 경로 및 결과입니다.  
  
## <a name="remarks"></a>설명  
 이 구조는 [Get기호 정보](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md) 메서드 호출에서 반환 됩니다.  
  
 `bstrVerboseSearchInfo`필드가 비어 있지 않으면 검색 된 경로 및 해당 검색의 결과 목록을 포함 합니다. 목록의 형식은 경로를 사용 하 고 그 뒤에 줄임표 ("...")가 오고 그 뒤에 결과가 나옵니다. 경로 결과 쌍이 둘 이상 있는 경우 각 쌍은 "\r\n" (캐리지 리턴/줄 바꿈) 쌍으로 구분 됩니다. 패턴은 다음과 같습니다.  
  
 \<path>...\<result> \r\n \<path> \<result> ... \r\n \<path> ...\<result>  
  
 마지막 항목에는 \r\n 시퀀스가 없습니다.  
  
 다음은 `bstrVerboseSearchInfo` 표준 출력으로 전송 된 가능한 문자열입니다.  
  
 `c:\symbols\user32.pdb... File not found.`  
  
 `c:\winnt\symbols\user32.pdb... Version does not match.`  
  
 `\\symbols\symbols\user32.dll\0a8sd0ad8ad\user32.pdb... Symbols loaded.`  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg .h  
  
 네임 스페이스: VisualStudio  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>관련 항목  
 [구조체 및 공용 구조체](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)
