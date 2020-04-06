---
title: 프로그램 시작 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, launching
- programs, launching
ms.assetid: 6857e9c6-e44a-468a-afa4-f7c4a0b77844
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bf638e0c96c7df1de2650260427a972a07efce23
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738481"
---
# <a name="launch-a-program"></a>프로그램 실행
프로그램을 디버깅하려는 사용자는 **F5를** 눌러 IDE에서 디버거를 실행할 수 있습니다. 이렇게 하면 IDE가 DE(디버그 엔진)에 연결되는 일련의 이벤트가 시작되며, 이 경우 다음과 같이 프로그램에 연결되거나 연결됩니다.

1. IDE는 먼저 프로젝트 패키지를 호출하여 솔루션의 활성 프로젝트 디버그 설정을 가져옵니다. 설정에는 시작 디렉터리, 환경 변수, 프로그램이 실행되는 포트 및 지정된 경우 프로그램을 만드는 데 사용할 DE가 포함됩니다. 이러한 설정은 디버그 패키지로 전달됩니다.

2. DE를 지정하면 DE는 운영 체제를 호출하여 프로그램을 시작합니다. 프로그램을 실행하면 프로그램의 런타임 환경이 로드됩니다. 예를 들어 MSIL에서 프로그램을 작성한 경우 프로그램을 실행하기 위해 공통 언어 런타임이 호출됩니다.

    또는

    DE를 지정하지 않으면 포트는 운영 체제를 호출하여 프로그램을 시작하므로 프로그램의 런타임 환경이 로드됩니다.

   > [!NOTE]
   > DE가 프로그램을 시작하는 데 사용되는 경우 동일한 DE가 프로그램에 연결될 가능성이 높습니다.

3. DE 또는 포트가 프로그램을 시작했는지 여부에 따라 DE 또는 런타임 환경은 프로그램 설명 또는 노드를 만들고 프로그램이 실행 중인 포트에 알린다.

   > [!NOTE]
   > 프로그램 노드는 디버깅할 수 있는 프로그램의 간단한 표현이므로 런타임 환경에서 프로그램 노드를 만드는 것이 좋습니다. 프로그램 노드를 만들고 등록하기 위해 전체 DE를 로드할 필요가 없습니다. DE가 IDE 프로세스에서 실행되도록 설계되었지만 실제로 실행중인 IDE가 없는 경우 포트에 프로그램 노드를 추가할 수 있는 구성 요소가 있어야 합니다.

   새로 만든 프로그램은 동일한 IDE에서 시작하거나 연결된 다른 프로그램과 함께 디버그 세션을 구성합니다.

   프로그래밍 방식으로 사용자가 **F5를**처음 누르면 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]디버그 패키지가 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A> 메서드를 통해 프로젝트 패키지(시작되는 프로그램 유형과 연관됨)를 호출하여 솔루션의 활성 프로젝트 디버그 설정으로 <xref:Microsoft.VisualStudio.Shell.Interop.VsDebugTargetInfo2> 구조를 작성합니다. 이 구조는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebugger2.LaunchDebugTargets2%2A> 메서드에 대 한 호출을 통해 디버그 패키지로 다시 전달 됩니다. 그런 다음 디버그 패키지는 세션 디버그 관리자(SDM)를 인스턴스화하여 디버깅 중인 프로그램과 연결된 디버그 엔진을 시작합니다.

   SDM에 전달된 인수 중 하나는 프로그램을 시작하는 데 사용할 DE의 GUID입니다.

   DE GUID가 아닌 `GUID_NULL`경우 SDM은 DE를 공동 으로 만들고 [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) 메서드를 호출하여 프로그램을 시작합니다. 예를 들어 프로그램이 네이티브 코드로 작성된 `IDebugEngineLaunch2::LaunchSuspended` 경우 `CreateProcess` 프로그램을 `ResumeThread` 실행하기 위해 호출하고 (Win32 함수)를 호출할 수 있습니다.

   프로그램을 실행하면 프로그램의 런타임 환경이 로드됩니다. 그런 다음 DE 또는 런타임 환경은 프로그램을 설명하는 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) 인터페이스를 만들고 이 인터페이스를 [AddProgramNode에](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) 전달하여 프로그램이 실행 중임을 포트에 알립니다.

   통과되면 `GUID_NULL` 포트가 프로그램을 시작합니다. 프로그램이 실행되면 런타임 환경은 프로그램을 `IDebugProgramNode2` 설명하는 인터페이스를 만들고 에 `IDebugPortNotify2::AddProgramNode`전달합니다. 그러면 프로그램이 실행 중인 포트에 대해 볼수 있습니다. 그런 다음 SDM은 실행 중인 프로그램에 디버그 엔진을 연결합니다.

## <a name="in-this-section"></a>섹션 내용
 [포트 알림](../../extensibility/debugger/notifying-the-port.md) 프로그램이 시작되고 포트에 알림이 전송된 후 발생하는 일을 설명합니다.

 [출시 후 연결](../../extensibility/debugger/attaching-after-a-launch.md) 디버그 세션이 프로그램에 DE를 연결할 준비가 되면 문서입니다.

## <a name="related-sections"></a>관련 단원
 [작업 디버깅](../../extensibility/debugger/debugging-tasks.md) 프로그램 실행 및 식 평가와 같은 다양한 디버깅 작업에 대한 링크가 포함되어 있습니다.
