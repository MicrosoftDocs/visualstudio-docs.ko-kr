---
title: IDebugProgramNode연결2::On첨부 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNodeAttach2::OnAttach
helpviewer_keywords:
- IDebugProgramNodeAttach2::OnAttach
ms.assetid: 5fe52761-a508-4ab5-abdb-334fb6590334
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dfb8a39af3c030dadddcb148a79a96b57f20e183
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721882"
---
# <a name="idebugprogramnodeattach2onattach"></a>IDebugProgramNodeAttach2::OnAttach
연결된 프로그램에 연결하거나 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) 메서드에 대한 연결 프로세스를 연기합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT OnAttach(
   [in] REFGUID guidProgramId
);
```

```csharp
int OnAttach(
   ref Guid guidProgramId
};
```

## <a name="parameters"></a>매개 변수
`guidProgramId`\
【인】 `GUID` 을 사용하여 연결된 프로그램에 할당할 수 있습니다.

## <a name="return-value"></a>Return Value
 성공하면 `S_OK`를 반환합니다. `S_FALSE` [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) 메서드를 호출하지 않아야 하는 경우 반환합니다. 그러지 않으면 오류 코드가 반환됩니다.

## <a name="remarks"></a>설명
 이 메서드는 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) 메서드가 호출되기 전에 연결 프로세스 중에 호출됩니다. `OnAttach` 메서드는 연결 프로세스 자체를 수행하거나(이 메서드가 `S_FALSE`반환) `IDebugEngine2::Attach` 메서드에 대한 연결 `OnAttach` 프로세스를 `S_OK`연기할 수 있습니다(메서드반환). 두 경우 모두 `OnAttach` 메서드는 `GUID` 디버깅 중인 프로그램의 지정된 `GUID`을 설정할 수 있습니다.

## <a name="see-also"></a>참조
- [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [연결](../../../extensibility/debugger/reference/idebugengine2-attach.md)
