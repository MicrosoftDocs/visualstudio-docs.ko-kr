---
title: 'IDiaInjectedSource:: get_filename | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaInjectedSource::get_filename method
ms.assetid: 20f4fc68-335a-4971-b3a6-76501f0e8b19
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 68db108fe6193517d26957fd74807c2ed2b89035
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68161396"
---
# <a name="idiainjectedsourceget_filename"></a>IDiaInjectedSource::get_filename
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

소스에 대 한 파일 이름을 검색 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT get_filename (   
   BSTR* pRetVal  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 pRetVal  
 제한이 원본에 대 한 파일 이름을 반환 합니다.  
  
## <a name="return-value"></a>반환 값  
 성공하면 `S_OK`를 반환합니다. `S_FALSE`이 속성이 지원 되지 않으면를 반환 합니다. 그러지 않으면 오류 코드가 반환됩니다.  
  
## <a name="see-also"></a>관련 항목  
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)
