---
title: 'IDiaSymbol:: findChildren | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::findChildren method
ms.assetid: 5fe7573a-e48b-428d-9c17-7421b7209246
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a09a62a2e6b94dbccda3afce4bdd286270149c15
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150039"
---
# <a name="idiasymbolfindchildren"></a>IDiaSymbol::findChildren
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

기호의 자식을 검색 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT findChildren (   
   enum SymTagEnum   symtag,  
   LPCOLESTR         name,  
   DWORD             compareFlags,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `symtag`  
 진행 [SymTagEnum 열거](../../debugger/debug-interface-access/symtagenum.md)에 정의 된 대로 검색할 자식의 기호 태그를 지정 합니다. `SymTagNull`모든 자식을 검색 하려면로 설정 합니다.  
  
 `name`  
 진행 검색할 자식의 이름을 지정 합니다. `NULL`모든 자식을 검색 하려면로 설정 합니다.  
  
 `compareFlags`  
 진행 이름 일치에 적용 되는 비교 옵션을 지정 합니다. [Namesearchoptions 열거형](../../debugger/debug-interface-access/namesearchoptions.md) 열거형의 값은 단독으로 사용 하거나 함께 사용할 수 있습니다.  
  
 `ppResult`  
 제한이 검색 된 자식 기호의 목록을 포함 하는 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) 개체를 반환 합니다.  
  
## <a name="return-value"></a>반환 값  
 `S_OK`기호의 자식이 하나 이상 발견 되었으면를 반환 하 고, 자식이 없으면를 반환 하며 `S_FALSE` , 그렇지 않으면 오류 코드를 반환 합니다.  
  
## <a name="remarks"></a>설명  
 이 메서드는이 기호를 첫 번째 매개 변수로 사용 하 여 [IDiaSession:: findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md) 메서드를 호출 하는 것과 동일 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum 열거형](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSession:: findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [NameSearchOptions 열거형](../../debugger/debug-interface-access/namesearchoptions.md)
