---
title: 'IDiaAddressMap:: set_addressMap | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::set_addressMap method
ms.assetid: 81e82073-089b-43d5-af39-49d7a4907c7a
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 693ecf6e8fd4f0b55936bde371b7baa6975b8f2c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198654"
---
# <a name="idiaaddressmapset_addressmap"></a>IDiaAddressMap::set_addressMap
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

이미지 레이아웃 번역을 지 원하는 주소 맵을 제공 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT set_addressMap (   
   DWORD                     cbData,  
   struct DiaAddressMapEntry data[],  
   BOOL                      imagetoSymbols  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `cbData`  
 진행 매개 변수에 있는 요소의 수 `data` 입니다.  
  
 `data[]`  
 진행 번역 맵을 정의 하는 [Diaaddressmapentry 구조](../../debugger/debug-interface-access/diaaddressmapentry.md) 구조체의 배열입니다.  
  
 `imagetoSymbols`  
 [in] `TRUE` `data` 매개 변수가 디버그 기호에서 설명한 대로 새 이미지 레이아웃에서 원래 레이아웃으로 맵을 정의 하는 경우입니다. `FALSE``data`이 원래 레이아웃에서 가져온 새 이미지 레이아웃에 대 한 맵입니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.  
  
## <a name="remarks"></a>설명  
 일반적으로 DIA는 프로그램 데이터베이스 (.pdb) 파일에서 주소 변환 맵을 검색 합니다. 이러한 값이 없는 경우 [IDiaAddressMap:: set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) 메서드는 매개 변수를 `imagetoSymbols` 로 설정 하 `TRUE` 고 `imagetoSymbols` 매개 변수를로 설정 하 여 한 번 호출 됩니다 `FALSE` . [IDiaAddressMap::p ut_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md) 메서드를 사용 하 여 두 변환 맵을 모두 제공 하지 않으면 주소 맵 번역을 사용 하도록 설정할 수 없습니다.  
  
## <a name="see-also"></a>관련 항목  
 [DiaAddressMapEntry 구조체](../../debugger/debug-interface-access/diaaddressmapentry.md)   
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::p ut_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)   
 [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)
