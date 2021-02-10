---
title: StartTrackingContextWithRoot | Microsoft Docs
description: MSBuild StartTrackingContextWithRoot를 사용하여 루트 마커를 지정하는 지시 파일로 추적 컨텍스트를 시작하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- StartTrackingContextWithRoot
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- StartTrackingContextWithRoot
ms.assetid: f6ef2b76-8035-4a14-8195-aa221c46ef48
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b52541c99fa81f31eddde8e6c12ad2eee04f3c20
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99967048"
---
# <a name="starttrackingcontextwithroot"></a>StartTrackingContextWithRoot

루트 마커를 지정하는 지시 파일을 사용하여 추적 컨텍스트를 시작합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT WINAPI StartTrackingContextWithRoot(LPCTSTR intermediateDirectory, LPCTSTR taskName, LPCTSTR rootMarkerResponseFile);
```

#### <a name="parameters"></a>매개 변수

[in] `intermediateDirectory`

 추적 로그를 저장할 디렉터리입니다.

[in] `taskName`

 추적 컨텍스트를 식별합니다. 이 이름은 로그 파일 이름을 만드는 데 사용됩니다.

[in] `rootMarkerResponseFile`

 루트 마커가 포함된 지시 파일의 경로 이름입니다. 루트 이름은 컨텍스트에 대한 모든 추적을 그룹화하는 데 사용됩니다.

## <a name="return-value"></a>반환 값

 추적 컨텍스트가 만들어진 경우 **SUCCEEDED** 비트가 설정된 **HRESULT** 를 반환합니다.

## <a name="requirements"></a>요구 사항

 **헤더:** *FileTracker.h*

## <a name="see-also"></a>추가 정보

- [StartTrackingContext](../msbuild/starttrackingcontext.md)