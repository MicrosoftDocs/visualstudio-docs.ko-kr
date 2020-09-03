---
title: marker_series::is_enabled 메서드 | Microsoft 문서
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::marker_series::is_enabled
helpviewer_keywords:
- Concurrency::diagnostic::marker_series::is_enabled method
ms.assetid: 8ce4dd50-ca29-4c72-98d6-582693f7d501
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9ccef8ebbf63835a71027643b518280d5f4f867b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156408"
---
# <a name="marker_seriesis_enabled-method"></a>marker_series::is_enabled 메서드
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

모든 세션에서 공급자를 사용하도록 설정했는지 확인합니다.  
  
## <a name="syntax"></a>구문  
  
```  
bool is_enabled();  
bool is_enabled(  
   marker_importance _Importance,  
   int _Category  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `_Importance`  
 중요도 수준입니다.  
  
 `_Category`  
 범주입니다.  
  
## <a name="return-value"></a>반환 값  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** cvmarkersobj.h  
  
 **네임스페이스:** Concurrency::diagnostic  
  
## <a name="see-also"></a>관련 항목  
 [marker_series 클래스](../profiling/marker-series-class.md)
