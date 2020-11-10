---
title: SuspendTracking | Microsoft Docs
description: 현재 컨텍스트에서 추적을 일시 중단하는 MSBuild SuspendTracking의 구문, 요구 사항 및 반환 값에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- SuspendTracking
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- SuspendTracking
ms.assetid: f5e06e5a-8083-444c-99c1-07ba834226b5
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 164e1a11c7d107bf1d98419d77fdc50ed353f93b
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048088"
---
# <a name="suspendtracking"></a>SuspendTracking

현재 컨텍스트에서 추적을 일시 중단합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT WINAPI SuspendTracking(void);
```

## <a name="return-value"></a>반환 값

 추적이 일시 중단된 경우 **SUCCEEDED** 비트가 설정된 **HRESULT** 를 반환합니다.

## <a name="requirements"></a>요구 사항

 **헤더:** *FileTracker.h*

## <a name="see-also"></a>추가 정보

- [ResumeTracking](../msbuild/resumetracking.md)