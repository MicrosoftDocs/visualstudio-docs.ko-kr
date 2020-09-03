---
title: 'IDiaSymbol:: get_isHLSLData | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
ms.assetid: 4662058b-c505-4ccf-ae03-739a62c814ca
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fd67253ffeb266ba1d700b7271e95e9e40c736ce
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155890"
---
# <a name="idiasymbolget_ishlsldata"></a>IDiaSymbol::get_isHLSLData
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

이 기호가 HLSL (High Level Shader Language) 데이터를 나타내는지 여부를 지정 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT get_isHLSLData(   
   BOOL* pRetVal);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pRetVal`  
 제한이 `BOOL` 이 기호가 HLSL 데이터를 나타내는지 여부를 지정 하는에 대 한 포인터입니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 `S_FALSE` 또는 오류 코드가 반환 됩니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
