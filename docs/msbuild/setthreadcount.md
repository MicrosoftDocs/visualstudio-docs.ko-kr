---
title: SetThreadCount | Microsoft Docs
description: MSBuild가 SetThreadCount를 사용하여 전역 스레드 수를 설정하고 이 개수를 현재 스레드에 할당하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
apiname:
- SetThreadCount
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- SetThreadCount
ms.assetid: 335335a5-8ca0-4e18-95f5-62aa6a691386
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 01bfdae1dcd11d7df042948308c424b7773b3bb0
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048329"
---
# <a name="setthreadcount"></a>SetThreadCount

전역 스레드 개수를 설정하고 해당 개수를 현재 스레드에 할당합니다.

## <a name="syntax"></a>구문

```cmd
HRESULT WINAPI SetThreadCount(int threadCount);
```

#### <a name="parameters"></a>매개 변수

[in] `threadCount`

 사용할 스레드 수입니다.

## <a name="return-value"></a>반환 값

 스레드 개수가 업데이트된 경우 **SUCCEEDED** 비트가 설정된 **HRESULT** 를 반환합니다.

## <a name="requirements"></a>요구 사항

 **헤더:** *FileTracker.h*