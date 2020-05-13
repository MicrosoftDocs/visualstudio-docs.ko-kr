---
title: 아이디버그포트공급업체3::에이넘지속포트 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier3::EnumPersistedPorts
helpviewer_keywords:
- IDebugPortSupplier3::EnumPersistedPorts
ms.assetid: 1c3dead3-5d6c-4067-8418-4015f0b0dd07
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 92b31a6b6898b0031e4a01d5a6433d0ce77e64f4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724446"
---
# <a name="idebugportsupplier3enumpersistedports"></a>IDebugPortSupplier3::EnumPersistedPorts
이 메서드는 고정된 포트 목록을 열거할 수 있는 개체를 검색합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT EnumPersistedPorts(
   BSTR_ARRAY         PortNames,
   IEnumDebugPorts2** ppEnum
);
```

```csharp
int EnumPersistedPorts(
   BSTR_ARRAY           PortNames,
   out IEnumDebugPorts2 ppEnum
);
```

## <a name="parameters"></a>매개 변수
`PortNames`\
【인】 BSTR_ARRAY 포트 이름 목록을 포함 하는 [구조는](../../../extensibility/debugger/reference/bstr-array.md) 찾고 지속된 포트 중 반환 합니다. 이러한 이름을 가진 지속된 포트만 반환됩니다.

`ppEnum`\
【아웃】 [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md) 인터페이스를 구현하는 개체입니다.

## <a name="return-value"></a>Return Value
 성공하면 반환합니다. `S_OK` 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 지속성 포트는 포트 공급자가 인스턴스화될 때 로드되고 포트 공급자가 소멸될 때 저장됩니다.

## <a name="see-also"></a>참조
- [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)
- [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)
- [BSTR_ARRAY](../../../extensibility/debugger/reference/bstr-array.md)
