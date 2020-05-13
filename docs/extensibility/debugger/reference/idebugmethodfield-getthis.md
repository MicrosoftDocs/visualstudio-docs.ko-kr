---
title: 이데버그메소드필드::GetThis | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::GetThis
helpviewer_keywords:
- IDebugMethodField::GetThis method
ms.assetid: cc235bea-e909-4d8c-ab54-936736c803fc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b29252d1586d039084ec1d21f1fc4967aea68baf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727172"
---
# <a name="idebugmethodfieldgetthis"></a>IDebugMethodField::GetThis
메서드를 `this` `Me` 포함하는 [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)]개체의 (in) 포인터를 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetThis( 
   IDebugClassField** ppClass
);
```

```csharp
int GetThis(
   out IDebugClassField ppClass
);
```

## <a name="parameters"></a>매개 변수
`ppClass`\
【아웃】 "this" 포인터를 나타내는 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) 개체를 반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 S_OK 반환합니다. 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 개체 지향 언어에는 일반적으로 클래스의 현재 인스턴스화에 대한 암시적 포인터가 있습니다. 이를 C#/C++와 에서 `this` 와 `Me` [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)]같이 합니다.

## <a name="see-also"></a>참조
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
