---
title: 'IEnumDebugModules2:: Reset | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugModules2::Reset
helpviewer_keywords:
- IEnumDebugModules2::Reset
ms.assetid: f6ff364c-2644-4919-b950-3cb82eb6f601
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 81fc33620449837f3d2af883f0721d24df92e804
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80716521"
---
# <a name="ienumdebugmodules2reset"></a>IEnumDebugModules2::Reset
열거형을 첫 번째 요소로 다시 설정 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT Reset(
   void
);
```

```csharp
int Reset();
```

## <a name="return-value"></a>Return Value
 성공 하면이 반환 되 `S_OK` 고, 그렇지 않으면 오류 코드가 반환 됩니다.

## <a name="remarks"></a>설명
 이 메서드가 호출 된 후 [다음](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md) 메서드에 대 한 다음 호출에서 열거형의 첫 번째 요소를 반환 합니다.

## <a name="see-also"></a>추가 정보
- [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)
