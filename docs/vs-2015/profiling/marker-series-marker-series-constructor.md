---
title: marker_series::marker_series 생성자 | Microsoft 문서
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::marker_series::marker_series
helpviewer_keywords:
- Concurrency::diagnostic::marker_series constructor
ms.assetid: 042c7d23-f1d8-4e09-9e76-a21c30243790
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b42058e0501612acbf454df725a9f1631489d26e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155296"
---
# <a name="marker_seriesmarker_series-constructor"></a>marker_series::marker_series 생성자
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`marker_series` 클래스의 새 인스턴스를 초기화합니다.  
  
## <a name="syntax"></a>구문  
  
```  
marker_series();  
marker_series(  
   _In_ LPCTSTR _SeriesName  
);  
marker_series(  
   _In_ const GUID* _ProviderGuid  
);  
marker_series(  
   _In_ const GUID* _ProviderGuid,  
   _In_ LPCTSTR _SeriesName  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `_SeriesName`  
 만들려는 계열의 이름입니다.  
  
 `_ProviderGuid`  
 계열 공급자의 GUID입니다.  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** cvmarkersobj.h  
  
 **네임스페이스:** Concurrency::diagnostic  
  
## <a name="see-also"></a>관련 항목  
 [marker_series 클래스](../profiling/marker-series-class.md)
