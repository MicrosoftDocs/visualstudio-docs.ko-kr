---
title: 'IDebugPortEx2:: TerminateProcess | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEx2::TerminateProcess
helpviewer_keywords:
- IDebugPortEx2::TerminateProcess
ms.assetid: bf8fa94c-6d9d-4e4f-ac08-3b44ba5ace68
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 73c9a02f5b114d49afffec2b349ce6621871f789
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80725013"
---
# <a name="idebugportex2terminateprocess"></a>IDebugPortEx2::TerminateProcess
프로세스를 종료 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT TerminateProcess( 
   IDebugProcess2* pPortProcess
);
```

```csharp
int TerminateProcess( 
   IDebugProcess2 pPortProcess
);
```

## <a name="parameters"></a>매개 변수
`pPortProcess`\
진행 종료할 프로세스를 나타내는 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) 개체입니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="see-also"></a>추가 정보
- [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
