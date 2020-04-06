---
title: 명령 라우팅 알고리즘 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, routing
- command routing
ms.assetid: 998b616b-bd08-45cb-845f-808efb8c33bc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: af8d3e53e09214ce36a80ca18856085dfb2bb746
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709546"
---
# <a name="command-routing-algorithm"></a>명령 라우팅 알고리즘
Visual Studio에서 명령은 여러 가지 구성 요소에 의해 처리됩니다. 명령은 현재 선택 영역을 기반으로 하는 가장 안쪽 컨텍스트에서 가장 바깥쪽(전역) 컨텍스트로 라우팅됩니다. 자세한 내용은 [명령 가용성](../../extensibility/internals/command-availability.md)을 참조하십시오.

## <a name="order-of-command-resolution"></a>명령 확인 순서
 명령은 다음 수준의 명령 컨텍스트를 통해 전달됩니다.

1. 추가 기능: 환경은 먼저 존재하는 모든 추가 기능에 명령을 제공합니다.

2. 우선 순위 명령: 이러한 명령은 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterPriorityCommandTarget>을 사용하여 등록됩니다. Visual Studio의 모든 명령에 대해 호출되며 등록된 순서대로 호출됩니다.

3. 컨텍스트 메뉴 명령: 컨텍스트 메뉴에 있는 명령은 먼저 컨텍스트 메뉴에 제공되는 명령 대상에 제공되며, 그 다음에는 일반적인 라우팅으로 제공됩니다.

4. 도구 모음 세트 명령 대상: 이러한 명령 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell4.SetupToolbar2%2A>대상은 호출할 때 등록됩니다. 합니다 `pCmdTarget` 매개 변수 수 `null`입니다. 그렇지 않은 `null`경우 이 명령 대상은 설정하려는 도구 모음에 있는 명령을 업데이트하는 데 사용됩니다. 셸이 도구 모음을 설정하는 경우 포커스가 없는 경우에도 `pCmdTarget` 도구 모음의 명령에 대한 모든 업데이트가 창 프레임을 통해 흐르도록 창 프레임을 전달합니다.

5. 도구 창: 일반적으로 인터페이스를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> 구현하는 도구 창은 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 도구 창이 활성 창일 때 Visual Studio에서 명령 대상을 얻을 수 있도록 인터페이스를 구현해야 합니다. 그러나 포커스가 있는 도구 창이 **프로젝트** 창인 경우 명령은 선택한 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> 항목의 공통 상위 인 인터페이스로 라우팅됩니다. 이 선택이 여러 프로젝트에 걸쳐 있는 경우 명령은 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution> 계층구조로 라우팅됩니다. 인터페이스에는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> 인터페이스의 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> 해당 명령과 유사한 메서드와 메서드가 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 포함되어 있습니다.

6. 문서 창: 명령에 *.vsct* 파일에 `RouteToDocs` 플래그가 설정된 경우 Visual Studio는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> 인터페이스의 인스턴스 또는 문서 개체의 인스턴스(일반적으로 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> 인터페이스 또는 인터페이스)인 문서 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> 뷰 개체에서 명령 대상을 찾습니다. 문서 뷰 개체가 명령을 지원하지 않는 경우 Visual Studio는 명령을 반환되는 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 인터페이스로 라우팅합니다. 문서 데이터 개체에 대한 선택적 인터페이스입니다.

7. 현재 계층 구조: 현재 계층은 활성 문서 창을 소유하는 프로젝트또는 **솔루션 탐색기에서**선택된 계층 구조일 수 있습니다. Visual Studio는 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 현재 또는 활성 계층 구조에서 구현되는 인터페이스를 찾습니다. 계층 구조는 프로젝트 항목의 문서 창에 포커스가 있는 경우에도 계층이 활성화될 때마다 유효한 명령을 지원해야 합니다. 그러나 **솔루션 탐색기** 포커스가 있는 경우에만 적용되는 명령은 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> 인터페이스와 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> 해당 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> 메서드 및 메서드를 사용하여 지원되어야 합니다.

     **잘라내기,** **복사,** **붙여넣기,** **삭제**, **이름 바꾸기,** **Enter**및 **DoubleClick** 명령은 특별한 처리가 필요합니다. 계층 구조에서 **명령 삭제** 및 **제거를** 처리하는 방법에 대한 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler> 자세한 내용은 인터페이스를 참조하십시오.

8. 전역: 앞에서 언급한 컨텍스트에서 명령을 처리하지 않은 경우 Visual Studio는 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 인터페이스를 구현하는 명령을 소유하는 VSPackage로 명령을 라우팅하려고 시도합니다. VSPackage가 아직 로드되지 않은 경우 Visual Studio에서 메서드를 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 호출할 때 로드되지 않습니다. VSPackage는 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> 메서드가 호출될 때만 로드됩니다.

## <a name="see-also"></a>참조
- [명령 디자인](../../extensibility/internals/command-design.md)
