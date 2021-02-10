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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5e74e44289e4fd04acf82170584af8645767b63e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905238"
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