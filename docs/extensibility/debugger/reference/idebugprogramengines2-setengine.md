---
title: 'IDebugProgramEngines2:: SetEngine | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEngines2::SetEngine
helpviewer_keywords:
- IDebugProgramEngines2::SetEngine
ms.assetid: c05857ee-89cf-455e-8f1e-300cce4a2eab
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 226f5bbf11627a3171641806a673eaa15b614572
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80722412"
---
# <a name="idebugprogramengines2setengine"></a>IDebugProgramEngines2::SetEngine
프로그램 또는 프로그램 노드에서이 프로그램을 디버깅 하는 데 사용할 DE (디버그 엔진)를 알려 줍니다.

## <a name="syntax"></a>구문

```cpp
HRESULT SetEngine( 
   REFGUID guidEngine
);
```

```csharp
int SetEngine( 
   ref Guid guidEngine
);
```

## <a name="parameters"></a>매개 변수
`guidEngine`\
진행 DE의 GUID입니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="see-also"></a>추가 정보
- [IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)
