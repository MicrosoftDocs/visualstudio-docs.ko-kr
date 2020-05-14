---
title: 아이디버그메소드필드::겟글로벌컨테이너 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::GetGlobalContainer
helpviewer_keywords:
- IDebugMethodField::GetGlobalContainer method
ms.assetid: 041ac5aa-0b80-4310-b9ae-b88f8e7e0e5f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 37e3b26a265fe651216e46fa299bdd827416b8ce
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727129"
---
# <a name="idebugmethodfieldgetglobalcontainer"></a>IDebugMethodField::GetGlobalContainer
메서드의 전역 컨테이너를 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetGlobalContainer(
   IDebugClassField** ppClass
);
```

```csharp
int GetGlobalContainer(
   out IDebugClassField ppClass
);
```

## <a name="parameters"></a>매개 변수
`ppClass`\
【아웃】 이 메서드가 정의된 모듈을 나타내는 [IDebugClassField를](../../../extensibility/debugger/reference/idebugclassfield.md) 반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 S_OK 반환합니다. 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 반환된 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) 개체는 전체 모듈을 나타내며 인공 개체, 즉 모듈 자체에는 실제 클래스가 `IDebugClassField` 없지만 개체로 나타낼 수 있으므로 모듈의 다양한 요소를 열거하고 검색할 수 있습니다.

## <a name="see-also"></a>참조
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
