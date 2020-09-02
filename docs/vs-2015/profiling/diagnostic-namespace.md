---
title: 진단 네임스페이스 | Microsoft 문서
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic
helpviewer_keywords:
- Concurrency::diagnostic namespace
ms.assetid: ad786b19-7c4c-46ee-bfb6-c4752b373a09
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d412cfa5a9b5e7e90aeac3ac6bbb530b0ef48ad0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157584"
---
# <a name="diagnostic-namespace"></a>진단 네임스페이스
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`diagnostics` 네임스페이스는 동시성 시각화 도우미 표식을 내보내는 기능을 제공합니다.  
  
## <a name="syntax"></a>구문  
  
```  
namespace diagnostic;  
```  
  
## <a name="members"></a>멤버  
  
### <a name="classes"></a>클래스  
  
|이름|설명|  
|----------|-----------------|  
|[marker_series 클래스](../profiling/marker-series-class.md)|단일 공급자가 생성한 이벤트의 직렬 채널을 나타냅니다.|  
|[span 클래스](../profiling/span-class.md)|애플리케이션의 단계를 정의합니다.|  
  
### <a name="enumerations"></a>열거형  
  
|이름|설명|  
|----------|-----------------|  
|[marker_importance 열거형](../profiling/marker-importance-enumeration.md)|동시성 시각화 도우미 표식의 중요도 수준을 나타냅니다.|  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** cvmarkersobj.h  
  
 **네임스페이스:** 동시성  
  
## <a name="see-also"></a>관련 항목  
 [동시성 네임스페이스(동시성 시각화 도우미)](../profiling/concurrency-namespace-concurrency-visualizer.md)
