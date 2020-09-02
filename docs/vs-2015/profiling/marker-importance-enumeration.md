---
title: marker_importance 열거형 | Microsoft 문서
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::marker_importance
helpviewer_keywords:
- Concurrency::diagnostic::marker_importance enumeration
ms.assetid: d5524ea0-0227-4d8e-9122-332291042df5
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a4451a7b222b66f0fe5bea2b0e5f2b8499c9033c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198388"
---
# <a name="marker_importance-enumeration"></a>marker_importance 열거형
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

동시성 시각화 도우미 표식의 중요도 수준을 나타냅니다.  
  
## <a name="syntax"></a>구문  
  
```  
enum marker_importance;  
```  
  
## <a name="members"></a>멤버  
  
### <a name="values"></a>값  
  
|이름|설명|  
|----------|-----------------|  
|`critical_importance`|표식의 중요도를 매우 중요로 지정합니다.|  
|`high_importance`|표식의 중요도를 높음으로 지정합니다.|  
|`low_importance`|표식의 중요도를 낮음으로 지정합니다.|  
|`normal_importance`|표식의 중요도를 보통으로 지정합니다.|  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** cvmarkersobj.h  
  
 **네임스페이스:** Concurrency::diagnostic  
  
## <a name="see-also"></a>관련 항목  
 [진단 네임 스페이스](../profiling/diagnostic-namespace.md)
