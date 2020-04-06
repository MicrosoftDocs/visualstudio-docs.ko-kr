---
title: 파일 상태 코드 열거자 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- named constants, SccStatus enumerator
- source control plug-ins, file status enumeration
- SccStatus enumerator
- file status code enumerator
ms.assetid: 5c37876b-c83c-4ca1-837b-57cd465a879a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 184c8686ea184aea2cbd0a64873718cbe72f7615
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711448"
---
# <a name="file-status-code-enumerator"></a>파일 상태 코드 열거자
열거체에는 `SccStatus` 소스 제어 시스템에서 파일의 상태를 지정하는 명명된 상수 값이 포함되어 있습니다. 이 열거형은 [SccQueryInfo](../extensibility/sccqueryinfo-function.md) 및 `POPLISTFUNC` 콜백 함수에서 사용됩니다(자세한 내용은 [POPLISTFUNC](../extensibility/poplistfunc.md) 참조).

## <a name="syntax"></a>구문

```
enum SccStatus {
   SCC_STATUS_INVALID          = -1L,
   SCC_STATUS_NOTCONTROLLED    = 0x0000L,
   SCC_STATUS_CONTROLLED       = 0x0001L,
   SCC_STATUS_CHECKEDOUT       = 0x0002L,
   SCC_STATUS_OUTOTHER         = 0x0004L,
   SCC_STATUS_OUTEXCLUSIVE     = 0x0008L,
   SCC_STATUS_OUTMULTIPLE      = 0x0010L,
   SCC_STATUS_OUTOFDATE        = 0x0020L,
   SCC_STATUS_DELETED          = 0x0040L,
   SCC_STATUS_LOCKED           = 0x0080L,
   SCC_STATUS_MERGED           = 0x0100L,
   SCC_STATUS_SHARED           = 0x0200L,
   SCC_STATUS_PINNED           = 0x0400L,
   SCC_STATUS_MODIFIED         = 0x0800L,
   SCC_STATUS_OUTBYUSER        = 0x1000L
   SCC_STATUS_NOMERGE          = 0x2000L
   SCC_STATUS_RESERVED_1       = 0x4000L
   SCC_STATUS_RESERVED_2       = 0x8000L
};
```

## <a name="members"></a>멤버
 SCC_STATUS_INVALID 상태를 얻을 수 없습니다. 그것에 의존하지 마십시오.

 SCC_STATUS_NOTCONTROLLED 파일은 소스 제어하에 있지 않습니다.

 SCC_STATUS_CONTROLLED 파일이 소스 제어를 받고 있습니다.

 SCC_STATUS_CHECKEDOUT 로컬 디스크의 현재 사용자가 체크 아웃했습니다.

 SCC_STATUS_OUTOTHER 다른 사용자가 파일을 체크 아웃했습니다.

 SCC_STATUS_OUTEXCLUSIVE 파일은 독점적으로 체크 아웃됩니다.

 SCC_STATUS_OUTMULTIPLE 사용자가 파일을 체크 아웃한 SCC_STATUS_OUTMULTIPLE.

 SCC_STATUS_OUTOFDATE 파일이 최신 파일이 아닙니다.

 SCC_STATUS_DELETED 파일이 프로젝트에서 삭제되었습니다.

 SCC_STATUS_LOCKED 파일이 잠겨 있습니다. 더 이상 버전이 허용되지 않습니다.

 SCC_STATUS_MERGED 파일이 병합되었지만 아직 고정/확인되지 않았습니다.

 SCC_STATUS_SHARED 파일은 프로젝트 간에 공유됩니다.

 SCC_STATUS_PINNED 파일이 명시적 버전에 공유됩니다.

 SCC_STATUS_MODIFIED 파일이 수정/파손/위반되었습니다.

 SCC_STATUS_OUTBYUSER 파일은 현재 사용자가 체크 아웃합니다.

 SCC_STATUS_NOMERGE 파일은 병합할 수 없으며 GET 이전에 저장할 필요가 없습니다.

 SCC_STATUS_RESERVED_1 내부 용으로 예약되었습니다.

 SCC_STATUS_RESERVED_2 내부 용으로 예약되었습니다.

## <a name="see-also"></a>참조
- [소스 제어 플러그인](../extensibility/source-control-plug-ins.md)
- [SccQueryInfo](../extensibility/sccqueryinfo-function.md)
- [POPLISTFUNC](../extensibility/poplistfunc.md)
