---
title: 'IDebugMethodField:: EnumParameters | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumParameters
helpviewer_keywords:
- IDebugMethodField::EnumParameters method
ms.assetid: d77b1197-deb6-4144-8d1b-8b09949ccfac
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 13df02cf5870e630c4aecb34e9295d218ba7a0eb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80727188"
---
# <a name="idebugmethodfieldenumparameters"></a>IDebugMethodField::EnumParameters
메서드의 매개 변수에 대 한 열거자를 만듭니다.

## <a name="syntax"></a>구문

```cpp
HRESULT EnumParameters( 
   IEnumDebugFields** ppParams
);
```

```csharp
int EnumParameters(
   out IEnumDebugFields ppParams
);
```

## <a name="parameters"></a>매개 변수
`ppParams`\
제한이 메서드에 대 한 매개 변수 목록을 나타내는 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) 개체를 반환 합니다. 그렇지 않으면 매개 변수가 없는 경우 null 값을 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면 S_OK 반환 하거나 매개 변수가 없는 경우 S_FALSE을 반환 합니다. 그러지 않으면 오류 코드가 반환됩니다.

## <a name="remarks"></a>설명
 각 요소는 서로 다른 유형의 매개 변수를 나타내는 [Idebugfield](../../../extensibility/debugger/reference/idebugfield.md) 개체입니다. 각 개체에 대해 [Getkind](../../../extensibility/debugger/reference/idebugfield-getkind.md) 메서드를 호출 하 여 개체가 나타내는 매개 변수의 종류를 정확 하 게 확인 합니다.

 매개 변수에는 변수 이름과 해당 형식이 모두 포함 됩니다. 클래스 메서드의 첫 번째 매개 변수는 일반적으로 "this" 포인터입니다.

 매개 변수의 유형만 필요한 경우에는 [Enumarguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) 메서드를 호출 합니다.

## <a name="see-also"></a>추가 정보
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)
