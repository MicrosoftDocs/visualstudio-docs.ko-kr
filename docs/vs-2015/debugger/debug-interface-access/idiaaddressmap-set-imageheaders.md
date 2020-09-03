---
title: 'IDiaAddressMap:: set_imageHeaders | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::set_imageHeaders method
ms.assetid: a46b9d0e-43e6-433f-b2c7-aa203981e4e4
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 18fa69929f78d5ae661169a09db97697d98f4d94
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198634"
---
# <a name="idiaaddressmapset_imageheaders"></a>IDiaAddressMap::set_imageHeaders
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

상대 가상 주소 변환을 사용 하도록 이미지 헤더를 설정 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT set_imageHeaders (   
   DWORD cbData,  
   BYTE  data[],  
   BOOL  originalHeaders  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 cbData  
 진행 헤더 데이터의 바이트 수입니다. 가 여야 `n*sizeof(IMAGE_SECTION_HEADER)` 합니다 `n` . 여기서은 실행 파일의 섹션 헤더 수입니다.  
  
 data[]  
 진행  `IMAGE_SECTION_HEADER` 이미지 헤더로 사용할 구조체의 배열입니다.  
  
 originalHeaders  
 진행 `FALSE` 이미지 머리글이 업그레이드 전에 원래 이미지를 반영 하는 경우 새 이미지의 이미지 머리글이 면로 설정 `TRUE` 합니다. 일반적으로 `TRUE` [IDiaAddressMap:: set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) 메서드에 대 한 호출과 함께 사용 하도록 설정 됩니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.  
  
## <a name="remarks"></a>설명  
 `IMAGE_SECTION_HEADER`구조는 winnt.sif에서 선언 되 고 실행 파일의 이미지 섹션 헤더 형식을 나타냅니다.  
  
 상대 가상 주소 계산은 값에 따라 결정 `IMAGE_SECTION_HEADER` 됩니다. 일반적으로 DIA는 프로그램 데이터베이스 (.pdb) 파일에서이 파일을 검색 합니다. 이러한 값이 없는 경우 DIA는 상대 가상 주소를 계산할 수 없으며 [IDiaAddressMap:: get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md) 메서드는를 반환 `FALSE` 합니다. 그런 다음 클라이언트는 [IDiaAddressMap::p ut_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md) 메서드를 호출 하 여 이미지 자체에서 누락 된 이미지 헤더를 제공한 후 상대 가상 주소 계산을 사용 하도록 설정 해야 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap:: set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)   
 [IDiaAddressMap:: get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)   
 [IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)
