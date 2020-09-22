---
title: 'IDiaSymbol:: get_isCTypes | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalker2 interface
ms.assetid: 00c73cf9-2933-472e-bc1d-d041f4d7e412
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d2a4ebe70d8cf26907446494009838e9ba2f795e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842010"
---
# <a name="idiasymbolget_isctypes"></a>IDiaSymbol::get_isCTypes
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

기호 파일에 C 형식이 포함 되어 있는지 여부를 나타내는 플래그를 검색 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT get_isCTypes(  
   BOOL *pFlag  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pFlag`  
 제한이 `TRUE` 기호 파일에 C 형식이 포함 되어 있으면를 반환 하 고, 그렇지 않으면를 반환 `FALSE` 합니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 `S_FALSE` 또는 오류 코드가 반환 됩니다.  
  
> [!NOTE]
> 반환 값은 `S_FALSE` 기호에 대해 속성을 사용할 수 없음을 의미 합니다.  
  
## <a name="remarks"></a>설명  
 이 속성은 `SymTagExe` 기호 형식 ( [Exe](../../debugger/debug-interface-access/exe.md)참조)에서 사용할 수 있습니다.  
  
## <a name="requirements"></a>요구 사항  
  
|요구 사항|Description|  
|-----------------|-----------------|  
|헤더:|dia2.h|  
|버전:|DIA SDK v8.0|  
  
## <a name="see-also"></a>참고 항목  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Exe](../../debugger/debug-interface-access/exe.md)
