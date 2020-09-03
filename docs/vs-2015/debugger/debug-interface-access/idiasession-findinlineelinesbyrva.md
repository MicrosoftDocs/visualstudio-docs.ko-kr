---
title: IDiaSession::findInlineeLinesByRVA | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
ms.assetid: 7a74d5ee-0dbf-47c0-92b4-47ec03b13ce9
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9991f5d70ccb0c801c210975d295b3e32e907998
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68165619"
---
# <a name="idiasessionfindinlineelinesbyrva"></a>IDiaSession::findInlineeLinesByRVA
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

클라이언트에서 지정 된 부모 기호를 사용 하 여 직접 또는 간접적으로 인라인, 지정 된 RVA (상대 가상 주소) 내에 포함 된 모든 함수의 줄 번호 정보를 반복할 수 있도록 하는 열거형을 검색 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT findInlineeLinesByRVA (   
   IDiaSymbol*           parent,  
   DWORD                 rva,  
   DWORD                 length,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `parent`  
 진행 `IDiaSymbol` 부모를 나타내는 개체입니다.  
  
 `rva`  
 진행 주소를 RVA로 지정 합니다.  
  
 `length`  
 진행 이 쿼리를 포함 하는 주소 범위 (바이트 수)를 지정 합니다.  
  
 `ppResult`  
 제한이 `IDiaEnumLineNumbers` 검색 되는 줄 번호 목록을 포함 하는 개체를 보유 합니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum 열거형](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
