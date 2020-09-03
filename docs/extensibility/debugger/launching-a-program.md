---
title: 프로그램 시작 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738481"
---
# <a name="launch-a-program"></a>프로그램 시작
프로그램을 디버깅 하려는 사용자는 **F5** 키를 눌러 IDE에서 디버거를 실행할 수 있습니다. 그러면 다음과 같이 IDE에서 디버그 엔진 (DE)에 연결 하는 일련의 이벤트가 시작 됩니다. 그러면 프로그램에 연결 되거나 연결 됩니다.

1. IDE는 먼저 프로젝트 패키지를 호출 하 여 솔루션의 활성 프로젝트 디버그 설정을 가져옵니다. 설정에는 시작 디렉터리, 환경 변수, 프로그램이 실행 되는 포트 및 프로그램을 만드는 데 사용할 DE (지정 된 경우)가 포함 됩니다. 이러한 설정은 디버그 패키지에 전달 됩니다.

2. DE를 지정 하는 경우 DE는 운영 체제를 호출 하 여 프로그램을 시작 합니다. 프로그램을 시작 하면 프로그램의 런타임 환경이 로드 됩니다. 예를 들어 프로그램을 MSIL로 작성 하는 경우 프로그램을 실행 하기 위해 공용 언어 런타임이 호출 됩니다.

    또는

    DE를 지정 하지 않으면 포트에서 운영 체제를 호출 하 여 프로그램을 시작 합니다. 그러면 프로그램의 런타임 환경이 로드 됩니다.

   > [!NOTE]
   > 프로그램을 시작 하는 데 DE를 사용 하는 경우 동일한 DE-DE가 프로그램에 연결 될 가능성이 높습니다.

3. De 나 포트에서 프로그램을 시작 했는지 여부에 따라 DE 또는 런타임 환경은 프로그램 설명 또는 노드를 만들고 프로그램이 실행 중임을 포트에 알립니다.

   > [!NOTE]
   > 프로그램 노드는 디버그할 수 있는 프로그램을 간단 하 게 표시 하기 때문에 런타임 환경에서 프로그램 노드를 만드는 것이 좋습니다. 프로그램 노드를 만들고 등록 하는 경우에만 전체 DE를 로드할 필요가 없습니다. DE가 IDE 프로세스에서 실행 되도록 설계 되었지만 실제로 실행 되 고 있는 IDE가 없는 경우에는 프로그램 노드를 포트에 추가할 수 있는 구성 요소가 있어야 합니다.

   새로 만든 프로그램은 동일한 IDE에서 관련 되거나 관련 되지 않은 다른 프로그램과 함께 시작 되거나 연결 되어 디버그 세션을 구성 합니다.

   사용자가 처음으로 **F5 키**를 누를 때 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 의 디버그 패키지는 메서드를 통해 프로젝트 패키지 (시작 하는 프로그램의 형식에 연결 됨)를 호출 하 여 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A> <xref:Microsoft.VisualStudio.Shell.Interop.VsDebugTargetInfo2> 솔루션의 활성 프로젝트 디버그 설정으로 구조체를 채웁니다. 이 구조체는 메서드를 호출 하 여 디버그 패키지로 다시 전달 됩니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebugger2.LaunchDebugTargets2%2A> . 그런 다음 디버그 패키지는 디버깅 중인 프로그램 및 관련 디버그 엔진을 시작 하는 SDM (세션 디버그 관리자)을 인스턴스화합니다.

   SDM에 전달 되는 인수 중 하나는 프로그램을 시작 하는 데 사용할 DE의 GUID입니다.

   DE GUID가이 아닌 경우에는 `GUID_NULL` SDM에서 de를 공동 만든 다음 해당 [launchsuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) 메서드를 호출 하 여 프로그램을 시작 합니다. 예를 들어 프로그램이 네이티브 코드로 작성 되는 경우는 `IDebugEngineLaunch2::LaunchSuspended` `CreateProcess` 및 `ResumeThread` (Win32 함수)를 호출 하 여 프로그램을 실행 합니다.

   프로그램을 시작 하면 프로그램의 런타임 환경이 로드 됩니다. 그러면 DE 또는 런타임 환경에서 프로그램을 설명 하는 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) 인터페이스를 만들고이 인터페이스를 [add프로그램 노드에](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) 전달 하 여 프로그램을 실행 하 고 있음을 포트에 알립니다.

   `GUID_NULL`이 전달 되 면 포트가 프로그램을 시작 합니다. 프로그램이 실행 되 면 런타임 환경에서 `IDebugProgramNode2` 프로그램을 설명 하는 인터페이스를 만들어에 전달 `IDebugPortNotify2::AddProgramNode` 합니다. 그러면 프로그램이 실행 중임을 포트에 알립니다. 그런 다음 SDM은 디버그 엔진을 실행 중인 프로그램에 연결 합니다.

## <a name="in-this-section"></a>섹션 내용
 [포트에 알림](../../extensibility/debugger/notifying-the-port.md) 프로그램이 시작 되 고 포트에 알림이 표시 되는 경우 발생 하는 상황을 설명 합니다.

 [시작 후 연결](../../extensibility/debugger/attaching-after-a-launch.md) 디버그 세션에서 프로그램에 DE를 연결할 준비가 되었을 때의 문서입니다.

## <a name="related-sections"></a>관련 단원
 [디버깅 작업](../../extensibility/debugger/debugging-tasks.md) 프로그램 시작 및 식 계산과 같은 다양 한 디버깅 태스크에 대 한 링크를 포함 합니다.
