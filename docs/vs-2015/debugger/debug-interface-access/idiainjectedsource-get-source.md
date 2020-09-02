---
title: IDiaInjectedSource::get_source | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaInjectedSource::get_source method
ms.assetid: 3c0b5386-321f-4f8f-85cc-e2ee7b4cc3d2
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 856d0111e65b51b798dfe44a324c58c4db5457fd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68192414"
---
# <a name="idiainjectedsourceget_source"></a>IDiaInjectedSource::get_source
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

소스 코드 바이트를 검색 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT get_source (   
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `cbData`  
 진행 데이터 버퍼의 크기를 나타내는 바이트 수입니다.  
  
 `pcbData`  
 제한이 반환 된 바이트 수를 나타내는 바이트 수를 반환 합니다. 가 이면는 `data` `NULL` `pcbData` 사용할 수 있는 데이터의 총 바이트 수입니다.  
  
 `data[]`  
 제한이 원본 바이트로 채워질 버퍼입니다.  
  
## <a name="return-value"></a>반환 값  
 성공하면 `S_OK`를 반환합니다. `S_FALSE`이 속성이 지원 되지 않으면를 반환 합니다. 그러지 않으면 오류 코드가 반환됩니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)
