---
title: 아이디버그모듈2::겟정보 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule2::GetInfo
helpviewer_keywords:
- GetInfo method
- IDebugModule2::GetInfo method
ms.assetid: de337e66-294f-4ac9-b21e-71fac7418e36
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c68c583702d7def5a7bff3ee40a9b8b2c537bb31
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726954"
---
# <a name="idebugmodule2getinfo"></a>IDebugModule2::GetInfo
이 모듈에 대한 정보를 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetInfo( 
   MODULE_INFO_FIELDS dwFields,
   MODULE_INFO*       pInfo
);
```

```cpp
int GetInfo( 
   enum_MODULE_INFO_FIELDS dwFields,
   MODULE_INFO[]           pInfo
);
```

## <a name="parameters"></a>매개 변수
`dwFields`\
【인】 채울 필드를 지정하는 [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md) 열거형의 `pInfo` 플래그 조합입니다.

`pInfo`\
【인, 아웃】 모듈에 대한 설명으로 채워진 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) 구조입니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) 구조에는 모듈 창에 표시되는 모듈의 이름이 포함되어 **있습니다.**

## <a name="see-also"></a>참조
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
- [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)
