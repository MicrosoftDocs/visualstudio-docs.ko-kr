---
title: 아이디버그필드::겟타입정보 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetTypeInfo
helpviewer_keywords:
- IDebugField::GetTypeInfo method
ms.assetid: bb5acfa3-04c3-4088-be84-9ff8926cd16f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: faa3464f0396999f36604aa88c429235d4849688
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728785"
---
# <a name="idebugfieldgettypeinfo"></a>IDebugField::GetTypeInfo
이 메서드는 기호 또는 형식에 대 한 형식 독립적인 정보를 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetTypeInfo( 
   TYPE_INFO* pTypeInfo
);
```

```csharp
int GetTypeInfo(
   TYPE_INFO[] pTypeInfo
);
```

## <a name="parameters"></a>매개 변수
`pTypeInfo`\
【아웃】 제공된 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) 구조에서 형식 정보를 반환합니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 형식독립적 정보에는 예를 들어 AppDomain, 모듈 및 기호가 포함된 클래스가 포함됩니다.

## <a name="see-also"></a>참조
- [Gettype](../../../extensibility/debugger/reference/idebugfield-gettype.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
