---
title: EndTrackingContext | Microsoft Docs
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
ms.openlocfilehash: bf982200b8e65e404325bdbd189ff3b0f2daebac
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634242"
---
# <a name="endtrackingcontext"></a>EndTrackingContext

현재 추적 컨텍스트를 종료합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT WINAPI EndTrackingContext();
```

## <a name="return-value"></a>반환 값

추적 컨텍스트가 종료된 경우 **SUCCEEDED** 비트가 설정된 **HRESULT**를 반환합니다.

## <a name="requirements"></a>요구 사항

**헤더:** *FileTracker.h*

## <a name="see-also"></a>참조

- [StartTrackingContext](../msbuild/starttrackingcontext.md)
