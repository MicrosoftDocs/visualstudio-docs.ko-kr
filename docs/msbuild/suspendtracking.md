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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e8be768bc48c1815fc00069640e5bf3f4370f434
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99945281"
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