---
title: 아이디버그포트공급업체2 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2
helpviewer_keywords:
- IDebugPortSupplier2 interface
ms.assetid: 37067324-2ea6-4a01-8829-a6e9c7a70068
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ddce454e6634d8cc177019e9d30b0ffcc7e7f1cc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724479"
---
# <a name="idebugportsupplier2"></a>IDebugPortSupplier2
이 인터페이스는 세션 디버그 관리자(SDM)에 포트를 제공합니다.

## <a name="syntax"></a>구문

```
IDebugPortSupplier2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자를 위한 참고 사항
사용자 지정 포트 공급자는 이 인터페이스를 구현하여 포트 공급자를 나타냅니다.

## <a name="notes-for-callers"></a>발신자에 대한 참고 사항
포트 공급자를 `CoCreateInstance` `GUID` 호출하면 이 인터페이스가 반환됩니다(이 인터페이스를 가져오는 일반적인 방법입니다). 다음은 그 예입니다.

```cpp
IDebugPortSupplier2 *GetPortSupplier(GUID *pPortSupplierGuid)
{
    IDebugPortSupplier2 *pPS = NULL;
    if (pPortSupplierGuid != NULL) {
        CComPtr<IDebugPortSupplier2> spPortSupplier;
        spPortSupplier.CoCreateInstance(*pPortSupplierGuid);
        if (spPortSupplier != NULL) {
            pPS = spPortSupplier.Detach();
        }
    }
    return (pPS);
}
```

[GetPortSupplier에](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md) 대한 호출은 에서 사용 중인 현재 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]포트 공급자를 나타내는 이 인터페이스를 반환합니다.

- [GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md) 포트를 만든 포트 공급자를 나타내는 이 인터페이스를 반환 합니다.

- [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md) 인터페이스 의 `IDebugPortSupplier` 목록을 나타냅니다 `IEnumDebugPortSuppliers` (인터페이스는 [EnumPortSuppliers에서](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)가져온, 등록 된 포트 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]공급 업체의 모든 나타내는).

디버그 엔진은 일반적으로 포트 공급자와 상호 작용하지 않습니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
다음 표에서는 의 `IDebugPortSupplier2`메서드를 보여 주며 의 메서드를 보여 주면 됩니다.

|방법|설명|
|------------|-----------------|
|[GetPortSupplierName](../../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md)|포트 공급자 이름을 가져옵니다.|
|[GetPortSupplierId](../../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md)|포트 공급자 식별자를 가져옵니다.|
|[GetPort](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md)|포트 공급자로부터 포트를 가져옵니다.|
|[EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)|이미 존재하는 포트를 연수합니다.|
|[CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)|포트 공급자가 새 포트 추가를 지원하는지 확인합니다.|
|[AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)|포트를 추가합니다.|
|[RemovePort](../../../extensibility/debugger/reference/idebugportsupplier2-removeport.md)|포트를 제거합니다.|

## <a name="remarks"></a>설명
포트 공급자는 이름과 ID로 자신을 식별하고, 포트를 추가 및 제거하고, 포트 공급자가 제공하는 모든 포트를 열거할 수 있습니다.

## <a name="requirements"></a>요구 사항
헤더: msdbg.h

네임스페이스: 마이크로소프트.비주얼스튜디오.디버거.인터롭

어셈블리: 마이크로소프트.비주얼스튜디오.디버거.인터롭.dll

## <a name="see-also"></a>참조
- [Core 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md)
- [GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)
- [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)
