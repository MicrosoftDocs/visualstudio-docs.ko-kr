---
title: 파일 상태 코드 열거자 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- named constants, SccStatus enumerator
- source control plug-ins, file status enumeration
- SccStatus enumerator
- file status code enumerator
ms.assetid: 5c37876b-c83c-4ca1-837b-57cd465a879a
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1b6e74caa9eedd42e25339d62f5837ccfe82d001
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204369"
---
# <a name="file-status-code-enumerator"></a>파일 상태 코드 열거자
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

열거자에는 `SccStatus` 소스 제어 시스템에서 파일의 상태를 지정 하는 명명 된 상수 값이 포함 되어 있습니다. 이 열거형은 [Sccqueryinfo](../extensibility/sccqueryinfo-function.md) 및 콜백 함수에서 사용 됩니다 `POPLISTFUNC` (자세한 내용은 [POPLISTFUNC](../extensibility/poplistfunc.md) 참조).  
  
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
 SCC_STATUS_INVALID  
 상태를 가져올 수 없습니다. 사용 하지 마십시오.  
  
 SCC_STATUS_NOTCONTROLLED  
 파일이 소스 제어에 있지 않습니다.  
  
 SCC_STATUS_CONTROLLED  
 파일이 소스 제어에 있습니다.  
  
 SCC_STATUS_CHECKEDOUT  
 로컬 디스크에서 현재 사용자가 체크 아웃 했습니다.  
  
 SCC_STATUS_OUTOTHER  
 다른 사용자가 파일을 체크 아웃 했습니다.  
  
 SCC_STATUS_OUTEXCLUSIVE  
 파일을 단독으로 체크 아웃 했습니다.  
  
 SCC_STATUS_OUTMULTIPLE  
 두 명 이상의 사용자가 파일을 체크 아웃 했습니다.  
  
 SCC_STATUS_OUTOFDATE  
 파일이 최신 파일이 아닙니다.  
  
 SCC_STATUS_DELETED  
 파일이 프로젝트에서 삭제 되었습니다.  
  
 SCC_STATUS_LOCKED  
 파일이 잠겼습니다. 더 이상 사용할 수 있는 버전이 없습니다.  
  
 SCC_STATUS_MERGED  
 파일이 병합 되었지만 아직 수정/확인 되지 않았습니다.  
  
 SCC_STATUS_SHARED  
 프로젝트 간에 파일을 공유 합니다.  
  
 SCC_STATUS_PINNED  
 파일이 명시적 버전으로 공유 되었습니다.  
  
 SCC_STATUS_MODIFIED  
 파일이 수정/중단/위반 되었습니다.  
  
 SCC_STATUS_OUTBYUSER  
 현재 사용자가 파일을 체크 아웃 했습니다.  
  
 SCC_STATUS_NOMERGE  
 파일은에 병합할 수 없으며 가져오기 전에 저장할 필요가 없습니다.  
  
 SCC_STATUS_RESERVED_1  
 내부용으로 예약된 속성입니다.  
  
 SCC_STATUS_RESERVED_2  
 내부용으로 예약된 속성입니다.  
  
## <a name="see-also"></a>관련 항목  
 [소스 제어 플러그 인](../extensibility/source-control-plug-ins.md)   
 [SccQueryInfo](../extensibility/sccqueryinfo-function.md)   
 [POPLISTFUNC](../extensibility/poplistfunc.md)
