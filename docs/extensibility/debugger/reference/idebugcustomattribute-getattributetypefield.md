---
description: 사용자 지정 특성 클래스 형식을 가져옵니다.
title: 'IDebugCustomAttribute:: Getattribut 필드 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute::GetAttributeTypeField
helpviewer_keywords:
- IDebugCustomAttribute::GetAttributeTypeField
ms.assetid: d6ce26d5-42ba-44c1-8659-0516db5bc82d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d0d0cfdfcdb49c934d9f4c0288f66a52e3e48f49
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105088096"
---
# <a name="idebugcustomattributegetattributetypefield"></a>IDebugCustomAttribute::GetAttributeTypeField
사용자 지정 특성 클래스 형식을 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetAttributeTypeField( 
   IDebugClassField** ppCAType
);
```

```csharp
int GetAttributeTypeField(
   out IDebugClassField ppCAType
);
```

## <a name="parameters"></a>매개 변수
`ppCAType`\
제한이 사용자 지정 특성이 인스턴스인 클래스를 나타내는 [Idebugclassfield](../../../extensibility/debugger/reference/idebugclassfield.md) 개체를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면 S_OK을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 사용자 지정 특성은 항상 클래스입니다. 이 메서드는 해당 클래스를 설명 하는 [Idebugclassfield](../../../extensibility/debugger/reference/idebugclassfield.md) 개체에 대 한 액세스를 제공 합니다.

## <a name="see-also"></a>참조
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
