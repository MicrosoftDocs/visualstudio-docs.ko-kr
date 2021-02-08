---
title: 'IDebugPortSupplier3:: EnumPersistedPorts | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier3::EnumPersistedPorts
helpviewer_keywords:
- IDebugPortSupplier3::EnumPersistedPorts
ms.assetid: 1c3dead3-5d6c-4067-8418-4015f0b0dd07
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 09b1fabaeb5bf887eedaa53d57bdeb3604bf2257
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99840329"
---
# <a name="idebugportsupplier3enumpersistedports"></a>IDebugPortSupplier3::EnumPersistedPorts
이 메서드는 지속형 포트 목록을 열거할 수 있도록 하는 개체를 검색 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT EnumPersistedPorts(
   BSTR_ARRAY         PortNames,
   IEnumDebugPorts2** ppEnum
);
```

```csharp
int EnumPersistedPorts(
   BSTR_ARRAY           PortNames,
   out IEnumDebugPorts2 ppEnum
);
```

## <a name="parameters"></a>매개 변수
`PortNames`\
진행 지속형 포트 간에 찾고 반환할 포트 이름 목록을 포함 하는 [BSTR_ARRAY](../../../extensibility/debugger/reference/bstr-array.md) 구조체입니다. 이러한 이름을 가진 지속형 포트만 반환 됩니다.

`ppEnum`\
제한이 [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md) 인터페이스를 구현 하는 개체입니다.

## <a name="return-value"></a>Return Value
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 지속형 포트는 포트 공급자가 인스턴스화될 때 로드 되 고 포트 공급자가 제거 되 면 저장 됩니다.

## <a name="see-also"></a>참고 항목
- [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)
- [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)
- [BSTR_ARRAY](../../../extensibility/debugger/reference/bstr-array.md)
