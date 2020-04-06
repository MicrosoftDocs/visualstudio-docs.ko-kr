---
title: IDebug 사용자 정의 속성::GetParentField | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute::GetParentField
helpviewer_keywords:
- IDebugCustomAttribute::GetParentField
ms.assetid: bcdfdf37-bfcf-4988-a7b8-4c731d0af1b0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1fae84a4d02438335aea00c50dd9b89520d08bae
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732692"
---
# <a name="idebugcustomattributegetparentfield"></a>IDebugCustomAttribute::GetParentField
사용자 지정 특성이 연결된 필드를 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetParentField( 
   IDebugField** ppField
);
```

```csharp
int GetParentField(
   out IDebugField ppField
);
```

## <a name="parameters"></a>매개 변수
`ppField`\
【아웃】 사용자 지정 특성이 연결된 필드를 나타내는 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 개체를 반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 S_OK 반환합니다. 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 반환된 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 개체에서 [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) 메서드를 호출하여 부모가 어떤 필드인지 확인합니다.

## <a name="see-also"></a>참조
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
