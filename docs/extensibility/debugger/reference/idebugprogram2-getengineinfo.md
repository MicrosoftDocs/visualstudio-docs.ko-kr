---
title: 'IDebugProgram2:: GetEngineInfo | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetEngineInfo
helpviewer_keywords:
- IDebugProgram2::GetEngineInfo
ms.assetid: 3a4f2dc0-e082-4d8d-aeaf-463ab09d279b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b26d6dcde31d3599c8aa8f8223c1f3cf00a59437
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99906257"
---
# <a name="idebugprogram2getengineinfo"></a>IDebugProgram2::GetEngineInfo
이 프로그램을 실행 하는 디버그 엔진 (DE)의 이름과 GUID를 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetEngineInfo( 
   BSTR* pbstrEngine,
   GUID* pguidEngine
);
```

```csharp
int GetEngineInfo( 
   out string pbstrEngine,
   out GUID   pguidEngine
);
```

## <a name="parameters"></a>매개 변수
`pbstrEngine`\
제한이 이 프로그램을 실행 하는 DE-DE의 이름을 반환 합니다.

`pguidEngine`\
제한이 이 프로그램을 실행 하는 DE-DE의 GUID를 반환 합니다.

## <a name="return-value"></a>Return Value
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 각 DE는 id에 대 한 고유한 GUID를 정의 합니다.

## <a name="see-also"></a>참고 항목
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
