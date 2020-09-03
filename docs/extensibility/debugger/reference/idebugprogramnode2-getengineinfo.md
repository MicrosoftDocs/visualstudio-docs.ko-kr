---
title: 'IDebugProgramNode2:: GetEngineInfo | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80722095"
---
# <a name="idebugprogramnode2getengineinfo"></a>IDebugProgramNode2::GetEngineInfo
프로그램을 실행 하는 디버그 엔진 (DE)의 이름과 식별자를 가져옵니다.

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
제한이 프로그램 실행 취소의 이름을 반환 합니다 (c + + 관련: 호출자가 엔진의 이름에 관심이 없음을 나타내는 null 포인터 일 수 있음).

`pguidEngine`\
제한이 프로그램을 실행 하는 데 필요한 전역 고유 식별자를 반환 합니다 (c + + 관련: 호출자가 엔진의 GUID에 관심이 없음을 나타내는 null 포인터 일 수 있음).

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="see-also"></a>추가 정보
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
