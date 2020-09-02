---
title: 'IDiaPropertyStorage:: ReadBSTR | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadBSTR
ms.assetid: 7214643b-3286-48ed-90aa-0fe95b4cae5b
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e0c7a796a57d5c96d870850bb02051d745fd8473
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62538831"
---
# <a name="idiapropertystoragereadbstr"></a>IDiaPropertyStorage::ReadBSTR
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

`BSTR`속성 집합의 값을 읽습니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT ReadBSTR (   
   PROPID id,  
   BSTR*  pValue  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `id`  
 진행 읽을 속성의 식별자입니다 `PROPID` . WTypes. h에서로 정의 됩니다 `ULONG` .  
  
 `pValue`  
 제한이 속성 값을 반환 합니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다. `E_INVALIDARG`속성이 형식이 아니면를 반환 `BSTR` 합니다.  
  
## <a name="remarks"></a>설명  
 는 `BSTR` Windows에서 0으로 끝나는 와이드 문자열로 정의 됩니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)
