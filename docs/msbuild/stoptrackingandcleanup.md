---
title: StopTrackingAndCleanup | Microsoft Docs
description: MSBuild가 StopTrackingAndCleanup을 사용하여 모든 추적을 중지하고 추적 세션에서 사용하는 모든 메모리를 해제하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- StopTrackingAndCleanup
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- StopTrackingAndCleanup
ms.assetid: 9f8c5994-2dfc-43c3-a5fb-89b2f8990429
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 05aec8bc85ac392670469da8073da02888b2f063
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048099"
---
# <a name="stoptrackingandcleanup"></a>StopTrackingAndCleanup

모든 추적을 중지하고 추적 세션에 사용된 메모리를 해제합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT WINAPI StopTrackingAndCleanup(void);
```

## <a name="return-value"></a>반환 값

 추적이 중지된 경우 **SUCCEEDED** 비트가 설정된 **HRESULT** 를 반환합니다.

## <a name="requirements"></a>요구 사항

 **헤더:** *FileTracker.h*

## <a name="see-also"></a>추가 정보

- [StartTrackingContext](../msbuild/starttrackingcontext.md)