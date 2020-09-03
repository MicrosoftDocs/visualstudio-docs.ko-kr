---
title: DiaAddressMapEntry | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- DiaAddressMapEntry enumeration
ms.assetid: 5d0ae226-981d-4541-a801-fc4993fe663b
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 67c0a3e297f3eebfbf44724e64c4989d9bb979fb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68164351"
---
# <a name="diaaddressmapentry"></a>DiaAddressMapEntry
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

주소 맵의 항목을 설명 합니다.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
struct DiaAddressMapEntry {   
   DWORD rva,  
   DWORD rvaTo  
};  
```  
  
## <a name="elements"></a>요소  
 `rva`  
 이미지 A의 RVA (상대 가상 주소)입니다.  
  
 `rvaTo`  
 상대 가상 주소는 `rva` 이미지 B에서로 매핑됩니다.  
  
## <a name="remarks"></a>설명  
 주소 맵은 한 이미지 레이아웃 (A)에서 다른 이미지 레이아웃 (B)으로의 변환을 제공 합니다. `DiaAddressMapEntry`를 기준으로 정렬 된 구조체의 배열은 `rva` 주소 맵을 정의 합니다.  
  
 이미지 A의 주소를 변환 하려면 `addrA` `addrB` 이미지 B에서 다음 단계를 수행 합니다.  
  
1. 에서 `e` `rva` 보다 작거나 같은 항목에 대 한 맵을 검색 합니다 `addrA` .  
  
2. `delta = addrA – e.rva`을 설정합니다.  
  
3. `addrB = e.rvaTo + delta`을 설정합니다.  
  
   구조체의 배열이 `DiaAddressMapEntry` [IDiaAddressMap:: set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) 메서드에 전달 됩니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: dia2  
  
## <a name="see-also"></a>관련 항목  
 [열거형 및 구조체](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)
