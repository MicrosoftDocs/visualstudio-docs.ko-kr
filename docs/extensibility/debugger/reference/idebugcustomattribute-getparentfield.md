---
title: 'IDebugCustomAttribute:: GetParentField | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute::GetParentField
helpviewer_keywords:
- IDebugCustomAttribute::GetParentField
ms.assetid: bcdfdf37-bfcf-4988-a7b8-4c731d0af1b0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b9845954a2be9ec57edb6ca555fb89a6ad20f7d4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99842474"
---
# <a name="idebugcustomattributegetparentfield"></a>IDebugCustomAttribute::GetParentField
사용자 지정 특성이 연결 된 필드를 가져옵니다.

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
제한이 사용자 지정 특성이 연결 된 필드를 나타내는 [Idebugfield](../../../extensibility/debugger/reference/idebugfield.md) 개체를 반환 합니다.

## <a name="return-value"></a>Return Value
 성공 하면 S_OK을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 반환 된 [Idebugfield](../../../extensibility/debugger/reference/idebugfield.md) 개체에서 [getkind](../../../extensibility/debugger/reference/idebugfield-getkind.md) 메서드를 호출 하 여 부모 필드의 종류를 확인 합니다.

## <a name="see-also"></a>참고 항목
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
