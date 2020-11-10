---
title: WriteAllTLogs | Microsoft Docs
description: 모든 스레드 및 컨텍스트에 대한 추적 로그를 기록하는 WriteAllTLogs의 구문, 요구 사항 및 반환 값에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- WriteAllTLogs
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- WriteAllTLogs
ms.assetid: 1fa3e10b-263c-4960-a9ad-485c02a7a872
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 754b34b872ba0f0f677a194194b2ff893e7107e1
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93047478"
---
# <a name="writealltlogs"></a>WriteAllTLogs

모든 스레드 및 컨텍스트에 대한 추적 로그를 작성합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT WINAPI WriteAllTLogs(LPCTSTR intermediateDirectory, LPCTSTR tlogRootName);
```

#### <a name="parameters"></a>매개 변수

[in] `intermediateDirectory`

 추적 로그를 저장할 디렉터리입니다.

[in] `tlogRootName`

 로그 파일 이름의 루트 이름입니다.

## <a name="return-value"></a>반환 값

 추적 컨텍스트가 만들어진 경우 **SUCCEEDED** 비트가 설정된 **HRESULT** 를 반환합니다.

## <a name="requirements"></a>요구 사항

 **헤더:** *FileTracker.h*

## <a name="see-also"></a>추가 정보

- [WriteContextTLogs](../msbuild/writecontexttlogs.md)