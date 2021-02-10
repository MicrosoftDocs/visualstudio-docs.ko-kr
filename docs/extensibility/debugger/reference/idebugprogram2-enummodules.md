---
title: 'IDebugProgram2:: EnumModules | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::EnumModules
helpviewer_keywords:
- IDebugProgram2::EnumModules
ms.assetid: 876ac9da-3b7c-4156-b79a-8f340e9fcea6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: da3f3dcd150d35199458e9952074f76931969175
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99958585"
---
# <a name="idebugprogram2enummodules"></a>IDebugProgram2::EnumModules
이 프로그램이 로드 되 고 실행 중인 모듈 목록을 검색 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT EnumModules( 
   IEnumDebugModules2** ppEnum
);
```

```csharp
int EnumModules( 
   out IEnumDebugModules2 ppEnum
);
```

## <a name="parameters"></a>매개 변수
`ppEnum`\
제한이 모듈 목록을 포함 하는 [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md) 개체를 반환 합니다.

## <a name="return-value"></a>Return Value
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 모듈은 DLL 또는 어셈블리 이며 일반적으로 **모듈** 디버그 창에 나열 됩니다.

## <a name="see-also"></a>참고 항목
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)
