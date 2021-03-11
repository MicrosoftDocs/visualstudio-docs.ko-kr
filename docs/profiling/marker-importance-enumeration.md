---
description: 동시성 시각화 도우미 표식의 중요도 수준을 나타냅니다.
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2c2e7560c91882afe1ee2608bb2ae2fc105738dc
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102223942"
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

## <a name="see-also"></a>추가 정보
- [진단 네임스페이스](../profiling/diagnostic-namespace.md)
