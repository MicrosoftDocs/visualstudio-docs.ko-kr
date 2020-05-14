---
title: 디렉토리 상태 코드 열거자 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- directory status code enumerator
- source control plug-ins, directory status enumeration
ms.assetid: 616026b5-f529-40ef-90c1-1836e116d797
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7b5ebf61f2baa6e4277e27cd3c4d18a51e64f835
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712152"
---
# <a name="directory-status-code-enumerator"></a>디렉터리 상태 코드 열거자
열거체에는 `SccDirStatus` 소스 제어 시스템에서 디렉터리 상태를 지정하는 명명된 상수 값이 포함되어 있습니다. 이 열거형은 [SccDirQueryInfo에서](../extensibility/sccdirqueryinfo-function.md)사용됩니다. 이것은 소스 제어 플러그인 API의 버전 1.2에 도입되었습니다.

## <a name="syntax"></a>구문

```
enum SccDirStatus {
   SCC_DIRSTATUS_INVALID       = -1L,
   SCC_DIRSTATUS_NOTCONTROLLED = 0x0000L,
   SCC_DIRSTATUS_CONTROLLED    = 0x0001L,
   SCC_DIRSTATUS_EMPTYPROJ     = 0x0002L
};
```

## <a name="members"></a>멤버
 SCC_DIRSTATUS_INVALID 상태를 얻을 수 없습니다. 그것에 의존하지 마십시오.

 SCC_DIRSTATUS_NOTCONTROLLED 디렉터리 소스 제어하에 있지 않습니다.

 SCC_DIRSTATUS_CONTROLLED 디렉터리 소스 제어하에 있습니다.

 이 디렉터리에 해당하는 SCC_DIRSTATUS_EMPTYPROJ 프로젝트가 비어 있습니다.

## <a name="see-also"></a>참조
- [소스 제어 플러그인](../extensibility/source-control-plug-ins.md)
- [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)
