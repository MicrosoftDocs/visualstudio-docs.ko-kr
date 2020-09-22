---
title: IDiaAddressMap::p ut_imageAlign | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::put_imageAlign method
ms.assetid: f9ce875d-c263-43e5-a534-f34c37f9866f
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5e0fa57c38c8451bde84d96ab32bc7980c5e2d8b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841663"
---
# <a name="idiaaddressmapput_imagealign"></a>IDiaAddressMap::put_imageAlign
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

이미지 맞춤을 설정 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT put_imageAlign (   
   DWORD NewVal  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 NewVal  
 진행 실행 파일에 대 한 새 이미지 맞춤 값입니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.  
  
## <a name="remarks"></a>설명  
 이미지 (로드 된 실행 파일)는 지정 된 메모리 경계에 맞춰집니다. 이 맞춤은 현재 시스템 아키텍처와 컴파일 및 링크 시간 옵션의 영향을 받을 수 있습니다. 이미지 맞춤이 항상 설정 된 바이트 경계입니다. 다음 이미지 맞춤 값은 올바릅니다. 1, 2, 4, 8, 16, 32 및 64 바이트 경계입니다.  
  
 현재 이미지 맞춤은 [IDiaAddressMap:: get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md) 메서드를 호출 하 여 검색할 수 있습니다.  
  
> [!NOTE]
> 이 메서드를 호출할 수 있는 시간에 의해 이미지가 이미 로드 된 경우 `put_imageAlign`메서드는 일반적으로 이미지를 이동 하거나 변경 하 고 새 맞춤이 필요한 경우에 사용 됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)
