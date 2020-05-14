---
title: 아이디버그프로그램노드2::겟엔진정보 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::GetEngineInfo
helpviewer_keywords:
- IDebugProgramNode2::GetEngineInfo
ms.assetid: 664e7fe5-9100-4b7d-9dc5-e5a4dd0d0451
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c2e74ba3c0f826314818bc883778a6364ff3fb6e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722095"
---
# <a name="idebugprogramnode2getengineinfo"></a>IDebugProgramNode2::GetEngineInfo
프로그램을 실행하는 DE(디버그 엔진)의 이름과 식별자를 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetEngineInfo ( 
   BSTR* pbstrEngine,
   GUID* pguidEngine
);
```

```csharp
int GetEngineInfo(
   out string pbstrEngine,
   out Guid pguidEngine
);
```

## <a name="parameters"></a>매개 변수
`pbstrEngine`\
【아웃】 프로그램을 실행하는 DE의 이름을 반환합니다(C++-특정: 호출자는 엔진 이름에 관심이 없다는 것을 나타내는 null 포인터일 수 있습니다).

`pguidEngine`\
【아웃】 프로그램을 실행하는 DE의 전역고유 식별자를 반환합니다(C++-특정: 호출자가 엔진의 GUID에 관심이 없다는 것을 나타내는 null 포인터일 수 있음).

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="see-also"></a>참조
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
