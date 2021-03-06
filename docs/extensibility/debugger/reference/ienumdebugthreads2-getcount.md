---
description: Threads 열거의 요소 수를 반환 합니다.
title: 'IEnumDebugThreads2:: GetCount | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugThreads2::GetCount
helpviewer_keywords:
- IEnumDebugThreads2::GetCount
ms.assetid: 81b7f139-d24e-4040-9adc-d664d77563ba
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: aaa9c670b3f09985edb34f2165f000861c12a31c
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102225853"
---
# <a name="ienumdebugthreads2getcount"></a>IEnumDebugThreads2::GetCount
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
- [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)
