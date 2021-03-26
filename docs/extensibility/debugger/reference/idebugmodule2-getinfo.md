---
description: 이 모듈에 대 한 정보를 가져옵니다.
title: 'IDebugModule2:: GetInfo | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule2::GetInfo
helpviewer_keywords:
- GetInfo method
- IDebugModule2::GetInfo method
ms.assetid: de337e66-294f-4ac9-b21e-71fac7418e36
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 69286a7bf50c32aa3aa720deff78ee957f53fc65
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105065660"
---
# <a name="idebugmodule2getinfo"></a>IDebugModule2::GetInfo
이 모듈에 대 한 정보를 가져옵니다.

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
진행 채울 필드를 지정 하는 [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md) 열거형의 플래그 조합입니다 `pInfo` .

`pInfo`\
[in, out] 모듈에 대 한 설명과 함께 채워지는 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) 구조체입니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) **구조체는 모듈 창에** 표시 되는 모듈의 이름을 포함 합니다.

## <a name="see-also"></a>참조
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
- [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)
