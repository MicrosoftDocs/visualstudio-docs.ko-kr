---
title: 아이디버그포트요청2 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortRequest2
helpviewer_keywords:
- IDebugPortRequest2 interface
ms.assetid: 556e610d-7c4b-44a8-965a-76a9d02b601a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 163718fda344ba5f3f44ef630b4eba3e5613dc61
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724792"
---
# <a name="idebugportrequest2"></a>IDebugPortRequest2
이 인터페이스는 포트를 설명합니다. 이 설명은 포트 공급자에 포트를 추가하는 데 사용됩니다.

## <a name="syntax"></a>구문

```
IDebugPortRequest2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
 Visual Studio는 일반적으로 포트 공급자로부터 디버그 포트를 가져오는 과정에서 이 인터페이스를 구현합니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
 이 인터페이스는 [AddPort로](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) 전달되어 디버그 포트를 만듭니다. [GetPortRequest에](../../../extensibility/debugger/reference/idebugport2-getportrequest.md) 대 한 호출은 처음에 포트를 만드는 데 사용 되는 요청을 나타내는이 인터페이스를 반환 합니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는 의 `IDebugPortRequest2`메서드를 보여 주며 의 메서드를 보여 주면 됩니다.

|방법|설명|
|------------|-----------------|
|[GetPortName](../../../extensibility/debugger/reference/idebugportrequest2-getportname.md)|만들 포트의 이름을 가져옵니다.|

## <a name="remarks"></a>설명
 디버그 엔진은 일반적으로 포트 공급자와 상호 작용하지 않으며 이 인터페이스에 사용할 수 없습니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

 어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
- [GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)
