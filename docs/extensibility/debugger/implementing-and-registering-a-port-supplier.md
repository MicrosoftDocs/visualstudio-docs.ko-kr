---
title: 항구 공급업체 구현 및 등록 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], registering port suppliers
- port suppliers, registering
ms.assetid: fb057052-ee16-4272-8e16-a4da5dda0ad4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: efa9cdd8740648b66fe7190177b5fe769c4b2539
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738525"
---
# <a name="implement-and-register-a-port-supplier"></a>포트 공급업체 구현 및 등록
포트 공급업체의 역할은 포트를 추적하고 공급하는 것이며, 포트는 프로세스를 관리합니다. 포트를 만들어야 하는 경우 포트 공급자는 포트 공급자의 GUID를 사용하여 CoCreate를 사용하여 인스턴스화됩니다(세션 디버그 관리자 [SDM]는 사용자가 선택한 포트 공급자 또는 프로젝트 시스템에서 지정한 포트 공급자를 사용합니다). 그런 다음 SDM은 [CanAddPort를](../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md) 호출하여 포트를 추가할 수 있는지 확인합니다. 포트를 추가할 수 있는 경우 [AddPort를](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) 호출하 고 포트를 설명 하는 [IDebugPortRequest2를](../../extensibility/debugger/reference/idebugportrequest2.md) 전달 하 여 새 포트를 요청 합니다. `AddPort`[은 IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) 인터페이스로 표시되는 새 포트를 반환합니다.

## <a name="discussion"></a>토론
 포트는 컴퓨터 또는 디버그 서버와 연결된 포트 공급자에 의해 만들어집니다. 서버는[EnumPortSuppliers](../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md) 메서드를 통해 포트 공급자를 열거하고 포트 공급자는 [EnumPorts](../../extensibility/debugger/reference/idebugportsupplier2-enumports.md) 메서드를 통해 포트를 열거합니다.

 일반적인 COM 등록 외에도 포트 공급자는 특정 레지스트리 위치에 CLSID와 이름을 배치하여 Visual Studio에 등록해야 합니다. 디버깅 SDK 도우미 함수라는 `SetMetric` 이 집안일을 처리합니다: 각 항목을 등록할 때 한 번 호출되므로 다음과 같이 됩니다.

```cpp
SetMetric(metrictypePortSupplier,
          <GUID of your port supplier>,
          metricCLSID,
          <CLSID of your port supplier>,
          false,
          NULL)
SetMetric(metrictypePortSupplier,
          <GUID of your port supplier>,
          metricName,
          <name of your port supplier>,
          false,
          NULL);
```

 포트 공급자는 등록된 각 `RemoveMetric` 항목에 대해 한 번(다른 디버깅 SDK 도우미 함수)을 호출하여 자체 등록을 취소합니다.

```cpp
RemoveMetric(metrictypePortSupplier,
             <GUID of your port supplier>,
             metricCLSID,
             NULL);
RemoveMetric(metrictypePortSupplier,
             <GUID of your port supplier>,
             metricName,
             NULL);
```

> [!NOTE]
> `SetMetric` `RemoveMetric` [디버깅을 위한 SDK 도우미이며](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) *dbgmetric.h에* 정의되고 *ad2de.lib로*컴파일된 정적 함수입니다. `metrictypePortSupplier`및 `metricCLSID` `metricName` 도우미는 *dbgmetric.h에*정의되어 있습니다.

 포트 공급자는 각각 [GetPortSupplierName](../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md) 및 [GetPortSupplierId](../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md)메서드를 통해 이름과 GUID를 제공할 수 있습니다.

## <a name="see-also"></a>참조
- [포트 공급업체 구현](../../extensibility/debugger/implementing-a-port-supplier.md)
- [디버깅을 위한 SDK 도우미](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
- [항구 공급업체](../../extensibility/debugger/port-suppliers.md)
