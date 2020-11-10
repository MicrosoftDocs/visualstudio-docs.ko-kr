---
title: StartTrackingContext | Microsoft Docs
description: 추적 컨텍스트를 시작하는 MSBuild StartTrackingContext의 매개 변수, 요구 사항 및 반환 값에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- StartTrackingContext
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- StartTrackingContext
ms.assetid: 720cd295-38e7-4974-86db-b8106b1207ba
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 13a22e3a20b69f62fe1e7d6c8e97eb80df6de1b6
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048157"
---
# <a name="starttrackingcontext"></a>StartTrackingContext

추적 컨텍스트를 시작합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT WINAPI StartTrackingContext(LPCTSTR intermediateDirectory, LPCTSTR taskName);
```

#### <a name="parameters"></a>매개 변수

[in] `intermediateDirectory`

 추적 로그를 저장할 디렉터리입니다.

[in] `taskName`

 추적 컨텍스트를 식별합니다. 이 이름은 로그 파일 이름을 만드는 데 사용됩니다.

## <a name="return-value"></a>반환 값

 추적 컨텍스트가 만들어진 경우 **SUCCEEDED** 비트가 설정된 **HRESULT** 를 반환합니다.

## <a name="requirements"></a>요구 사항

 **헤더:** *FileTracker.h*
