---
title: WriteContextTLogs | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- WriteContextTLogs
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- WriteContextTLogs
ms.assetid: ffc6c7be-3f22-4624-9ffc-0122fe72b6ec
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e5c0793cc6d9f11cd1074c5cd0091687b154c069
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/25/2020
ms.locfileid: "77579464"
---
# <a name="writecontexttlogs"></a>WriteContextTLogs
현재 컨텍스트에 대한 로그 파일을 작성합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT WINAPI WriteContextTLogs(LPCTSTR intermediateDirectory, LPCTSTR tlogRootName);
```

#### <a name="parameters"></a>매개 변수
[in] `intermediateDirectory`

 추적 로그를 저장할 디렉터리입니다.

[in] `tlogRootName`

 로그 파일 이름의 루트 이름입니다.

## <a name="return-value"></a>반환 값
 추적 컨텍스트가 만들어진 경우 **SUCCEEDED** 비트가 설정된 **HRESULT**를 반환합니다.

## <a name="requirements"></a>요구 사항
 **헤더:** *FileTracker.h*

## <a name="see-also"></a>참조
- [WriteAllTLogs](../msbuild/writealltlogs.md)