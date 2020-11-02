---
title: EndTrackingContext | Microsoft Docs
description: MSBuild EndTrackingContext를 사용하여 현재 추적 컨텍스트를 종료하는 구문, 반환 값, 요구 사항을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- EndTrackingContext
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- EndTrackingContext
ms.assetid: c2c5d794-8dc8-4594-8717-70dc79a0e75d
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: da1ef921106732a7787f68a979bc88f3ac012b6d
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2020
ms.locfileid: "92436664"
---
# <a name="endtrackingcontext"></a>EndTrackingContext

현재 추적 컨텍스트를 종료합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT WINAPI EndTrackingContext();
```

## <a name="return-value"></a>반환 값

추적 컨텍스트가 종료된 경우 **SUCCEEDED** 비트가 설정된 **HRESULT** 를 반환합니다.

## <a name="requirements"></a>요구 사항

**헤더:** *FileTracker.h*

## <a name="see-also"></a>추가 정보

- [StartTrackingContext](../msbuild/starttrackingcontext.md)
