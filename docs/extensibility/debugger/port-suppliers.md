---
title: 항구 공급업체 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- port suppliers
- debugging [Debugging SDK], port suppliers
ms.assetid: a8f3db96-1a13-4e93-9ef6-0861880369e0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6313a7afce9ed272177a26d8da1a9d1516c8022e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738307"
---
# <a name="port-suppliers"></a>항구 공급업체
디버거 아키텍처에서 포트 *공급자:*

- 서버에 포함되며 요청 시 해당 서버에 포트를 제공합니다.

- 포함된 서버에서 포트를 추가하고 제거할 수 있습니다.

- 서버에 제공된 모든 포트를 열거할 수 있습니다.

- 레지스트리를 통해 Visual Studio에 등록된 [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) 인터페이스로 표시됩니다. 이 인터페이스는 [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)를 호출하여 가져올 수 있습니다.

  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]는 기본 포트 공급자와 기본 포트를 제공합니다. 사용자 지정 포트를 구현해야 하는 경우 사용자 지정 포트 공급자도 구현하여 이러한 사용자 지정 포트를 제공해야 합니다.

## <a name="see-also"></a>참조
- [서버](../../extensibility/debugger/servers-visual-studio-sdk.md)
- [Ports](../../extensibility/debugger/ports.md)
- [디버거 개념](../../extensibility/debugger/debugger-concepts.md)
- [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)
- [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)
