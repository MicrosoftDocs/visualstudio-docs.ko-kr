---
title: Interop 어셈블리의 명령 계약 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80709680"
---
# <a name="command-contracts-in-interop-assemblies"></a>Interop 어셈블리의 명령 계약
인터페이스를 통해 명령을 처리 하는 기본 계약은 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 환경에서 메서드를 호출 하 여 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 명령이 지원 되는지 여부를 확인 하 고, 지원 되는 경우 상태와 텍스트를 확인 하는 것입니다. 그런 다음 환경에서 메서드를 호출 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> 하 여 명령을 실행 합니다.

 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>메서드는 모든 명령에 대해 동일 하 게 처리 됩니다. 필요한 경우 (예: 드롭다운 목록을 사용 하 여) 추가 통신은 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> 적절 한 매개 변수를 사용 하 여 메서드를 호출 하 여 관리 됩니다. 이러한 매개 변수의 해석은 지정 된 명령에 따라 달라 집니다.

 명령 대상이 output 매개 변수에서 값을 반환 하는 경우 호출자는 항상 할당 된 리소스를 해제 해야 합니다. 이 매개 변수는 변형 이므로 변형을 지우면 리소스가 해제 됩니다.

 명령이 계층 창 내에서 작동 해야 하는 경우 인터페이스를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> 사용 해야 합니다. 인터페이스에는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> 유사한 메서드와와 유사한 계약이 있습니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> .

## <a name="see-also"></a>추가 정보
- [Vspackage 사용자 인터페이스 요소를 추가 하는 방법](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Vspackage의 명령 라우팅](../../extensibility/internals/command-routing-in-vspackages.md)
- [명령 구현](../../extensibility/internals/command-implementation.md)
