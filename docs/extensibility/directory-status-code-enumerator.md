---
title: 디렉터리 상태 코드 열거자 | Microsoft Docs
description: SccDirStatus 열거자는 소스 제어 시스템의 디렉터리 상태를 지정하는 명명된 상수 값을 포함하며 SccDirQueryInfo에서 사용됩니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- directory status code enumerator
- source control plug-ins, directory status enumeration
ms.assetid: 616026b5-f529-40ef-90c1-1836e116d797
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a504c6c080c34b4506cf4078b64465a3bd6c7d97
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904232"
---
# <a name="directory-status-code-enumerator"></a>디렉터리 상태 코드 열거자
`SccDirStatus`열거자에는 소스 제어 시스템의 디렉터리 상태를 지정하는 명명된 상수 값이 포함되어 있습니다. 이 열거형은 [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)에서 사용됩니다. 이는 소스 제어 플러그 인 API 버전 1.2에서 도입되었습니다.

## <a name="syntax"></a>구문

```
enum SccDirStatus {
   SCC_DIRSTATUS_INVALID       = -1L,
   SCC_DIRSTATUS_NOTCONTROLLED = 0x0000L,
   SCC_DIRSTATUS_CONTROLLED    = 0x0001L,
   SCC_DIRSTATUS_EMPTYPROJ     = 0x0002L
};
```

## <a name="members"></a>멤버
 SCC_DIRSTATUS_INVALID 상태를 가져올 수 없습니다. 은 의존하지 않습니다.

 SCC_DIRSTATUS_NOTCONTROLLED Directory는 소스 제어를 받지 않습니다.

 SCC_DIRSTATUS_CONTROLLED 디렉터리에 소스 제어가 있습니다.

 SCC_DIRSTATUS_EMPTYPROJ 이 디렉터리에 해당하는 프로젝트가 비어 있습니다.

## <a name="see-also"></a>참조
- [소스 제어 플러그 인](../extensibility/source-control-plug-ins.md)
- [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)
