---
description: Ports 열거의 요소 수를 반환 합니다.
title: 'IEnumDebugPorts2:: GetCount | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPorts2::GetCount
helpviewer_keywords:
- IEnumDebugPorts2::GetCount
ms.assetid: d714455c-e4fc-48dc-a6d4-7e8b5d7c1bce
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 22550fa1ba700a77564f6da666d6300335427e1a
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102226321"
---
# <a name="ienumdebugports2getcount"></a>IEnumDebugPorts2::GetCount
열거형의 요소 수를 반환 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetCount(
   ULONG* pcelt
);
```

```csharp
int GetCount(
   out uint pcelt
);
```

## <a name="parameters"></a>매개 변수
`pcelt`\
제한이 열거형의 요소 수를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 이 메서드는 `Next` ,, `Clone` `Skip` 및 `Reset` 메서드만 구현 해야 함을 지정 하는 일반적인 COM 열거 인터페이스의 일부가 아닙니다.

## <a name="see-also"></a>참고 항목
- [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)
