---
title: 인터롭 어셈블리의 명령 계약 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- command handling with interop assemblies, command contracts
- interop assemblies, command contracts
ms.assetid: 57245708-f539-42dc-8963-2754a48f0189
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4f20a4f479d62cd1b64c3b13ff6e1a949656a668
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709680"
---
# <a name="command-contracts-in-interop-assemblies"></a>인터옵 어셈블리에서 명령 계약
<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 인터페이스를 통해 명령을 처리하기 위한 기본 계약은 환경이 메서드를 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 호출하여 명령이 지원되는지 여부를 확인하고 지원되는 경우 해당 상태 및 텍스트를 결정하는 것입니다. 그런 다음 환경은 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> 명령을 실행하는 메서드를 호출합니다.

 메서드는 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 모든 명령에 대해 동일하게 처리됩니다. 필요한 경우(예: 드롭다운 목록)에 해당하는 추가 통신은 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> 적절한 매개 변수를 사용하여 메서드를 호출하여 관리됩니다. 이러한 매개 변수의 해석은 지정된 명령에 따라 다릅니다.

 명령 대상이 출력 매개 변수에서 값을 반환하는 경우 호출자는 항상 할당된 리소스를 해제해야 합니다. 이 매개 변수는 변형이므로 변형을 지우면 리소스가 해제됩니다.

 명령이 계층 구조 창 내에서 작동해야 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> 하는 경우 인터페이스를 사용해야 합니다. 인터페이스는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> 비슷한 메서드와 비슷한 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> 계약을 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>가지고 있습니다.

## <a name="see-also"></a>참조
- [VSPackage사용자 인터페이스 요소를 추가하는 방법](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [VS패키지의 명령 라우팅](../../extensibility/internals/command-routing-in-vspackages.md)
- [명령 구현](../../extensibility/internals/command-implementation.md)
