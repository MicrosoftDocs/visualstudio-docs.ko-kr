---
title: 디렉터리 상태 코드 열거자 | Microsoft Docs
description: SccDirStatus 열거자에는 소스 제어 시스템의 디렉터리 상태를 지정 하는 명명 된 상수 값이 포함 되어 있으며 Scctqueryinfo에 사용 됩니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- directory status code enumerator
- source control plug-ins, directory status enumeration
ms.assetid: 616026b5-f529-40ef-90c1-1836e116d797
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3e995fb1dcb879645f59d6d8750852a790c99e90
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105091255"
---
# <a name="directory-status-code-enumerator"></a>디렉터리 상태 코드 열거자
열거자에는 `SccDirStatus` 소스 제어 시스템의 디렉터리 상태를 지정 하는 명명 된 상수 값이 포함 되어 있습니다. 이 열거형은 [Sccdirqueryinfo](../extensibility/sccdirqueryinfo-function.md)에서 사용 됩니다. 이는 소스 제어 플러그 인 API 버전 1.2에서 도입 되었습니다.

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
 SCC_DIRSTATUS_INVALID 상태를 가져올 수 없습니다. 사용 하지 마십시오.

 SCC_DIRSTATUS_NOTCONTROLLED 디렉터리가 소스 제어에 있지 않습니다.

 SCC_DIRSTATUS_CONTROLLED 디렉터리가 소스 제어에 있습니다.

 이 디렉터리에 해당 하는 SCC_DIRSTATUS_EMPTYPROJ 프로젝트가 비어 있습니다.

## <a name="see-also"></a>참조
- [소스 제어 플러그 인](../extensibility/source-control-plug-ins.md)
- [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)
