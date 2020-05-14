---
title: 아이디버그포트엑스2::이력서 처리 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEx2::ResumeProcess
helpviewer_keywords:
- IDebugPortEx2::ResumeProcess
ms.assetid: e80a6960-9456-4764-9320-e7b1bd57fe5d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0fdbd8e409208c28fbfc1ce728df3591be655c75
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725026"
---
# <a name="idebugportex2resumeprocess"></a>IDebugPortEx2::ResumeProcess
프로세스 실행을 다시 시작합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT ResumeProcess( 
   IDebugProcess2* pPortProcess
);
```

```cpp
int ResumeProcess( 
   IDebugProcess2 pPortProcess
);
```

## <a name="parameters"></a>매개 변수
`pPortProcess`\
【인】 다시 시작할 프로세스를 나타내는 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) 개체입니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="see-also"></a>참조
- [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
