---
title: ResumeTracking | Microsoft Docs
description: 현재 컨텍스트에서 추적을 계속하는 MSBuild ResumeTracking의 구문, 요구 사항 및 반환 값에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- ResumeTracking
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- ResumeTracking
ms.assetid: d637e019-7c50-4b0a-812e-bc822001e697
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fd6722ca0b930d66a386732dac466a8e4fe36976
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99937916"
---
# <a name="resumetracking"></a>ResumeTracking

현재 컨텍스트에서 추적을 다시 시작합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT WINAPI ResumeTracking();
```

## <a name="return-value"></a>반환 값

 추적이 다시 시작된 경우 **SUCCEEDED** 비트가 설정된 **HRESULT** 를 반환합니다. 컨텍스트를 사용할 수 없어 추적을 다시 시작할 수 없는 경우 **E_FAIL** 이 반환됩니다.

## <a name="requirements"></a>요구 사항

 **헤더:** *FileTracker.h*

## <a name="see-also"></a>추가 정보

- [SuspendTracking](../msbuild/suspendtracking.md)