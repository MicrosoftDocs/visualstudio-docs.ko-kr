---
description: 이 인터페이스는 포트를 설명 합니다.
title: IDebugPortRequest2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortRequest2
helpviewer_keywords:
- IDebugPortRequest2 interface
ms.assetid: 556e610d-7c4b-44a8-965a-76a9d02b601a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 035b6364b3a1dea400c96bcf179d57d6b4808ad5
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105072223"
---
# <a name="idebugportrequest2"></a>IDebugPortRequest2
이 인터페이스는 포트를 설명 합니다. 이 설명은 포트 공급자에 포트를 추가 하는 데 사용 됩니다.

## <a name="syntax"></a>구문

```
IDebugPortRequest2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 Visual Studio는 일반적으로 포트 공급자에서 디버그 포트를 가져오는 프로세스에서이 인터페이스를 구현 합니다.

## <a name="notes-for-callers"></a>호출자 참고 사항
 이 인터페이스는 디버그 포트를 만들기 위해 [Addport](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) 에 전달 됩니다. [Getportrequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md) 에 대 한 호출은이 인터페이스를 반환 하며, 첫 번째 위치의 포트를 만드는 데 사용 되는 요청을 나타냅니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는의 메서드를 보여 줍니다 `IDebugPortRequest2` .

|메서드|Description|
|------------|-----------------|
|[GetPortName](../../../extensibility/debugger/reference/idebugportrequest2-getportname.md)|만들 포트의 이름을 가져옵니다.|

## <a name="remarks"></a>설명
 디버그 엔진은 일반적으로 포트 공급자와 상호 작용 하지 않으며이 인터페이스를 사용 하지 않습니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg .h

 네임 스페이스: VisualStudio

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참조
- [핵심 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
- [GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)
