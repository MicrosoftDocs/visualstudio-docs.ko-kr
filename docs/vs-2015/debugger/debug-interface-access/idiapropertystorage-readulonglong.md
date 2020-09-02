---
title: 'IDiaPropertyStorage:: ReadULONGLONG | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadULONGLONG
ms.assetid: f80a2e24-5744-4fec-bab0-3ed51aef6e58
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6da509e226a612e80a10ca0759b5e264f31a1e13
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62538683"
---
# <a name="idiapropertystoragereadulonglong"></a>IDiaPropertyStorage::ReadULONGLONG
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

`ULONGLONG`속성 집합의 값을 읽습니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT ReadULONGLONG (   
   PROPID     id,  
   ULONGLONG* pValue  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `id`  
 진행 읽을 속성의 식별자입니다 `PROPID` . WTypes. h에서로 정의 됩니다 `ULONG` .  
  
 `pValue`  
 제한이 속성 값을 반환 합니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다. `E_INVALIDARG`속성이 형식이 아니면를 반환 `ULONGLONG` 합니다.  
  
## <a name="remarks"></a>설명  
 는 `ULONGLONG` Windows에서 64 비트 부호 없는 정수로 정의 됩니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)
