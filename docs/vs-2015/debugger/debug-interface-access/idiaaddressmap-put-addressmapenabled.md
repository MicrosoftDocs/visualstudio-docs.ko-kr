---
title: IDiaAddressMap::p ut_addressMapEnabled | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::put_addressMapEnabled method
ms.assetid: 0f205337-4e59-4383-8059-7b1d207d6dcd
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4f2f7fc6fd512fa121cf96cb64f4ce4b961772e1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198678"
---
# <a name="idiaaddressmapput_addressmapenabled"></a>IDiaAddressMap::put_addressMapEnabled
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

주소 맵을 사용 하 여 기호 주소를 변환 해야 하는지 여부를 지정 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT put_addressMapEnabled (   
   BOOL NewVal  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 NewVal  
 진행 `TRUE` 기호를 변환 하거나 사용 하지 않도록 설정 하려면로 설정 `FALSE` 합니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.  
  
## <a name="remarks"></a>설명  
 실행 가능 사후 프로세서는 때때로 실행 파일을 업데이트 합니다. DIA에는 기호를 새 레이아웃으로 변환할 수 있도록 지 원하는 메커니즘이 포함 되어 있습니다.  
  
 PDB 파일이 로드 될 때 파일에 저장 된 주소 맵을 사용할 수 있습니다. 그러나 클라이언트 응용 프로그램에서 [IDiaAddressMap:: set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) 메서드를 호출 하 여 자체 주소 맵을 제공 해야 하는 경우도 있습니다. `set_addressMap`메서드가 성공적으로 수행 되 면 클라이언트 응용 프로그램은의 매개 변수를 사용 하 여 메서드를 호출 하 여 `put_addressMapEnabled` `NewVal` `TRUE` 해당 주소 맵을 사용할 수 있도록 해야 합니다.  
  
 [IDiaAddressMap:: get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md) 메서드를 호출 하 여 사용할 수 있는 주소 맵의 현재 상태를 검색할 수 있습니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap:: set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)   
 [IDiaAddressMap::get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md)
