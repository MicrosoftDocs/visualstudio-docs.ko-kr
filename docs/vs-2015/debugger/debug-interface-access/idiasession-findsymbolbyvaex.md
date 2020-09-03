---
title: IDiaSession::findSymbolByVAEx | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findSymbolByVAEx method
ms.assetid: 11c685f6-cda2-4474-a432-214ecaae4ffa
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 14a0b573609d52269809dcaa6e900e17affcecfd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196371"
---
# <a name="idiasessionfindsymbolbyvaex"></a>IDiaSession::findSymbolByVAEx
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

지정 된 VA (가상 주소) 및 오프셋을 포함 하거나 가장 가까이 있는 지정 된 기호 형식을 검색 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT findSymbolByVAEx (   
   ULONGLONG    va,  
   SymTagEnum   symtag,  
   IDiaSymbol** ppSymbol,  
   LONG*        displacement  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `va`  
 진행 VA를 지정 합니다.  
  
 `symtag`  
 진행 찾을 기호 형식입니다. 값은 [SymTagEnum 열거형](../../debugger/debug-interface-access/symtagenum.md) 열거에서 가져옵니다.  
  
 `ppSymbol`  
 제한이 검색 된 기호를 나타내는 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) 개체를 반환 합니다.  
  
 `displacement`  
 제한이 에서 제공 하는 가상 주소에서 오프셋을 지정 하는 값을 반환 합니다 `va` .  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.  
  
## <a name="example"></a>예제  
  
```cpp#  
IDiaSymbol* pFunc;  
LONG disp = 0;  
pSession->findSymbolByVAEx( va, SymTagFunction, &pFunc, &disp );  
```  
  
## <a name="see-also"></a>참고 항목  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSession:: findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [IDiaSession:: Find기호 Byva](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum 열거형](../../debugger/debug-interface-access/symtagenum.md)
