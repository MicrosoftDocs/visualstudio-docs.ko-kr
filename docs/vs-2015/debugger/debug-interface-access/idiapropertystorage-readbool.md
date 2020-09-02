---
title: 'IDiaPropertyStorage:: ReadBOOL | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadBOOL
ms.assetid: ad1822db-4572-48f7-9919-f8137f6701f2
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 64eee421a5ed5bd46a64b51694d913a4f2dc4d41
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62538878"
---
# <a name="idiapropertystoragereadbool"></a>IDiaPropertyStorage::ReadBOOL
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

`BOOL`속성 집합의 값을 읽습니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT ReadBOOL (   
   PROPID id,  
   BOOL*  pValue  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `id`  
 진행 읽을 속성의 식별자입니다 `PROPID` . WTypes. h에서로 정의 됩니다 `ULONG` .  
  
 `pValue`  
 제한이 속성 값을 반환 합니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다. `E_INVALIDARG`속성이 형식이 아니면를 반환 `BOOL` 합니다.  
  
## <a name="remarks"></a>설명  
 일관 된 결과를 위해 `BOOL` 값은 0이 아닌 값은 `TRUE` 이 고 0은로 해석 됩니다 `FALSE` .  
  
## <a name="see-also"></a>관련 항목  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)
