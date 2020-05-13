---
title: 아이디버그프로그램2::에넘모듈 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::EnumModules
helpviewer_keywords:
- IDebugProgram2::EnumModules
ms.assetid: 876ac9da-3b7c-4156-b79a-8f340e9fcea6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 967b9b4a06f382e5da2ee2422dd48209184e474b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723020"
---
# <a name="idebugprogram2enummodules"></a>IDebugProgram2::EnumModules
이 프로그램이 로드하고 실행 중이면 모듈 목록을 검색합니다.

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
【아웃】 모듈 목록이 포함된 [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md) 개체를 반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 모듈은 DLL 또는 어셈블리이며 일반적으로 모듈 디버그 창에 **나열됩니다.**

## <a name="see-also"></a>참조
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)
