---
title: marker_importance 열거형 | Microsoft 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cvmarkersobj/Concurrency, diagnostic::marker_importance
helpviewer_keywords:
- Concurrency, diagnostic::marker_importance enumeration
ms.assetid: d5524ea0-0227-4d8e-9122-332291042df5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d67a1806034d55147379626b6eb4f868532e4d77
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85330739"
---
# <a name="marker_importance-enumeration"></a>marker_importance 열거형
동시성 시각화 도우미 표식의 중요도 수준을 나타냅니다.

## <a name="syntax"></a>구문

```cpp
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
 **헤더:** *cvmarkersobj.h*

 **네임스페이스:** Concurrency::diagnostic

## <a name="see-also"></a>참조
- [진단 네임스페이스](../profiling/diagnostic-namespace.md)