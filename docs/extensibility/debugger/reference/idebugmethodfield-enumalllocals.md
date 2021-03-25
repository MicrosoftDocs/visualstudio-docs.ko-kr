---
description: 컴파일러에서 내부적으로 생성 된 변수를 포함 하 여 메서드의 모든 지역 변수에 대 한 열거자를 만듭니다.
title: 'IDebugMethodField:: EnumAllLocals | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumAllLocals
helpviewer_keywords:
- IDebugMethodField::EnumAllLocals method
ms.assetid: 0bc7cc13-2628-4bd8-8c06-4d2aa6755ea8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 021dd54157a46e35c0acbb7dd7315fe155304b6d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105076695"
---
# <a name="idebugmethodfieldenumalllocals"></a>IDebugMethodField::EnumAllLocals
컴파일러에서 내부적으로 생성 된 변수를 포함 하 여 메서드의 모든 지역 변수에 대 한 열거자를 만듭니다.

## <a name="syntax"></a>구문

```cpp
HRESULT EnumAllLocals( 
   IDebugAddress*     pAddress,
   IEnumDebugFields** ppLocals
);
```

```csharp
int EnumAllLocals(
   IDebugAddress        pAddress,
   out IEnumDebugFields ppLocals
);
```

## <a name="parameters"></a>매개 변수
`pAddress`\
진행 특정 범위 또는 컨텍스트를 가리키는 메서드 내의 디버그 주소를 나타내는 [Idebugaddress](../../../extensibility/debugger/reference/idebugaddress.md) 개체입니다.

`ppLocals`\
제한이 지정 된 범위에 있는 모든 지역 목록을 나타내는 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) 개체를 반환 합니다. 그렇지 않으면 로컬이 없음을 나타내는 null 값을 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면 S_OK 반환 하거나 로컬이 없는 경우 S_FALSE을 반환 합니다. 그러지 않으면 오류 코드가 반환됩니다.

## <a name="remarks"></a>설명
 지정 된 디버그 주소를 포함 하는 블록 내에 정의 된 변수만 열거 됩니다. 이 메서드에는 컴파일러에서 생성 된 로컬이 포함 됩니다. 소스에서 명시적으로 정의 된 지역만 필요한 경우에는 [enumlocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) 메서드를 호출 합니다.

 메서드에는 여러 범위 지정 컨텍스트 또는 블록이 포함 될 수 있습니다.

## <a name="see-also"></a>참조
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)
