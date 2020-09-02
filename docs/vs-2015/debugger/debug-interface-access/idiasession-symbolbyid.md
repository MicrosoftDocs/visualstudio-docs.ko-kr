---
title: 'IDiaSession:: symbolById | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::symbolById method
ms.assetid: 062e4b5a-9c4d-4703-88da-ec13102c2b66
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ac409edcee7657e724822d1a72737c3142d8d93e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150199"
---
# <a name="idiasessionsymbolbyid"></a>IDiaSession::symbolById
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

고유한 식별자로 기호를 검색 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT symbolById (   
   DWORD        id,  
   IDiaSymbol** ppSymbol  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `id`  
 진행 고유 식별자입니다.  
  
 `ppSymbol`  
 제한이 검색 된 기호를 나타내는 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) 개체를 반환 합니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.  
  
## <a name="remarks"></a>설명  
 지정 된 식별자는 모든 기호를 고유 하 게 만들기 위해 DIA SDK에서 내부적으로 사용 하는 고유 값입니다.  
  
 예를 들어이 메서드를 사용 하 여 다른 기호의 형식을 나타내는 기호를 검색할 수 있습니다 (예제 참조).  
  
## <a name="example"></a>예  
 이 예제에서는 다른 기호의 형식을 나타내는 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) 을 검색 합니다. 이 예제에서는 세션에서 메서드를 사용 하는 방법을 보여 줍니다 `symbolById` . 더 간단한 방법은 [IDiaSymbol:: get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md) 메서드를 호출 하 여 형식 기호를 직접 검색 하는 것입니다.  
  
```cpp#  
IDiaSymbol *GetSymbolType(IDiaSymbol *pSymbol, IDiaSession *pSession)  
{  
    IDiaSymbol *pTypeSymbol = NULL;  
    if (pSymbol != NULL && pSession != NULL)  
    {  
        DWORD symbolTypeId;  
        pSymbol->get_typeId(&symbolTypeId);  
        pSession->symbolById(symbolTypeId, &pTypeSymbol);  
    }  
    return(pTypeSymbol);  
}  
```  
  
## <a name="see-also"></a>관련 항목  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)
