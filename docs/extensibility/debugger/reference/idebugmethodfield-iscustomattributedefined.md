---
title: IDebugMethodField::IsCustom속성 정의 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::IsCustomAttributeDefined
helpviewer_keywords:
- IDebugMethodField::IsCustomAttributeDefined method
ms.assetid: 1b5d95a8-cc87-4acb-9e6a-3928f3632b7c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d60e7a451a18ff8efbf47a008831109cd7f747c9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727111"
---
# <a name="idebugmethodfieldiscustomattributedefined"></a>IDebugMethodField::IsCustomAttributeDefined
특정 사용자 지정 특성이 정의되었는지 여부를 결정합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT IsCustomAttributeDefined( 
   LPCOLESTR pszCustomAttributeName
);
```

```csharp
int IsCustomAttributeDefined(
   [In] string pszCustomAttributeName
);
```

## <a name="parameters"></a>매개 변수
`pszCustomAttributeName`\
【인】 찾을 사용자 지정 특성의 이름을 포함하는 문자열입니다.

## <a name="return-value"></a>Return Value
 사용자 지정 특성이 이 메서드에 정의된 경우 S_OK 반환하고 그렇지 않으면 S_FALSE 반환합니다.

## <a name="see-also"></a>참조
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
