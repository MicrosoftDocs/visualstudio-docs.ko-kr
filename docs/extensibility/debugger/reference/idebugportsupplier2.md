---
title: IDebugPortSupplier2 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80724479"
---
# <a name="idebugportsupplier2"></a>IDebugPortSupplier2
이 인터페이스는 SDM (세션 디버그 관리자)에 대 한 포트를 제공 합니다.

## <a name="syntax"></a>Syntax

```
IDebugPortSupplier2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
사용자 지정 포트 공급자는이 인터페이스를 구현 하 여 포트 공급자를 나타냅니다.

## <a name="notes-for-callers"></a>호출자 참고 사항
포트 공급자의에 대 한 호출은이 인터페이스를 반환 합니다 .이 인터페이스는이 인터페이스를 `CoCreateInstance` `GUID` 가져오는 일반적인 방법입니다. 예를 들면 다음과 같습니다.

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

[Getportsupplier 업체](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md) 에 대 한 호출은이 인터페이스를 반환 하며,이 인터페이스는에서 사용 중인 현재 포트 공급자를 나타냅니다 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] .

- [Getportsupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md) 는 포트를 만든 포트 공급자를 나타내는이 인터페이스를 반환 합니다.

- [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md) 는 인터페이스 목록을 나타냅니다 `IDebugPortSupplier` `IEnumDebugPortSuppliers` .이 인터페이스는에 등록 된 모든 포트 공급자를 나타내는 [enumportsuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)에서 가져옵니다 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] .

디버그 엔진은 일반적으로 포트 공급자와 상호 작용 하지 않습니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
다음 표에서는의 메서드를 보여 줍니다 `IDebugPortSupplier2` .

|메서드|설명|
|------------|-----------------|
|[GetPortSupplierName](../../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md)|포트 공급자 이름을 가져옵니다.|
|[GetPortSupplierId](../../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md)|포트 공급자 식별자를 가져옵니다.|
|[GetPort](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md)|포트 공급자에서 포트를 가져옵니다.|
|[EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)|이미 존재 하는 포트를 열거 합니다.|
|[CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)|포트 공급자가 새 포트 추가를 지원 하는지 확인 합니다.|
|[AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)|포트를 추가 합니다.|
|[RemovePort](../../../extensibility/debugger/reference/idebugportsupplier2-removeport.md)|포트를 제거 합니다.|

## <a name="remarks"></a>설명
포트 공급자는 이름 및 ID로 자신을 식별 하 고, 포트를 추가 및 제거 하 고, 포트 공급자가 제공 하는 모든 포트를 열거할 수 있습니다.

## <a name="requirements"></a>요구 사항
헤더: msdbg .h

네임 스페이스: VisualStudio

어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>추가 정보
- [핵심 인터페이스](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md)
- [GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)
- [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)
