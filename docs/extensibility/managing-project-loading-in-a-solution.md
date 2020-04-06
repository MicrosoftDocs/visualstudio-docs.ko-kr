---
title: 솔루션의 프로젝트 로딩 관리 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions, managing project loading
ms.assetid: 097c89d0-f76a-4aaf-ada9-9a778bd179a0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 21cd5e7e557e795db49aea7a14e8e4cc7caa0422
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702727"
---
# <a name="manage-project-loading-in-a-solution"></a>솔루션에서 프로젝트 로딩 관리
Visual Studio 솔루션에는 많은 수의 프로젝트가 포함될 수 있습니다. 기본 Visual Studio 동작은 솔루션을 열 때 솔루션의 모든 프로젝트를 로드하고 사용자가 로드가 완료될 때까지 프로젝트에 액세스할 수 있도록 허용하지 않는 것입니다. 프로젝트 로드 프로세스가 2분 이상 지속되면 로드된 프로젝트 수와 총 프로젝트 수를 보여주는 진행률 표시줄이 표시됩니다. 사용자는 여러 프로젝트에서 솔루션에서 작업하는 동안 프로젝트를 언로드할 수 있지만 이 절차에는 언로드된 프로젝트가 솔루션 재생 성 명령의 일부로 빌드되지 않고 닫힌 프로젝트의 형식 및 멤버에 대한 IntelliSense 설명이 표시되지 않는다는 몇 가지 단점이 있습니다.

 개발자는 솔루션 로드 관리자를 만들어 솔루션 로드 시간을 줄이고 프로젝트 로드 동작을 관리할 수 있습니다. 솔루션 로드 관리자는 백그라운드 빌드를 시작하기 전에 프로젝트가 로드되었는지 확인하고, 다른 백그라운드 작업이 완료될 때까지 백그라운드 로드를 지연하고, 다른 프로젝트 로드 관리 작업을 수행할 수 있습니다.

## <a name="create-a-solution-load-manager"></a>솔루션 로드 관리자 만들기
 개발자는 Visual Studio에서 솔루션 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager> 로드 관리자가 활성 상태임을 구현하고 조언하여 솔루션 로드 관리자를 만들 수 있습니다.

### <a name="activate-a-solution-load-manager"></a>솔루션 로드 관리자 활성화
 Visual Studio에서는 지정된 시간에 하나의 솔루션 로드 관리자만 사용할 수 있으므로 솔루션 로드 관리자를 활성화하려면 Visual Studio에 조언해야 합니다. 나중에 두 번째 솔루션 로드 관리자가 활성화되면 솔루션 로드 관리자의 연결이 끊어집니다.

 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution> 서비스를 받고 __VSPROPID4 설정해야 [합니다. VSPROPID_ActiveSolutionLoadManager](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_ActiveSolutionLoadManager>) 속성:

```csharp
IVsSolution pSolution = GetService(typeof(SVsSolution)) as IVsSolution;
object objLoadMgr = this;   //the class that implements IVsSolutionManager
pSolution.SetProperty((int)__VSPROPID4.VSPROPID_ActiveSolutionLoadManager, objLoadMgr);
```

 이 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnDisconnect%2A> 메서드는 Visual Studio가 종료될 때 또는 다른 패키지가 __VSPROPID4 호출하여 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.SetProperty%2A> 활성 솔루션 로드 관리자로 인계된 경우 호출됩니다. [ VSPROPID_ActiveSolutionLoadManager](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_ActiveSolutionLoadManager>) 속성입니다.

#### <a name="strategies-for-different-kinds-of-solution-load-manager"></a>다양한 종류의 솔루션 로드 관리자를 위한 전략
 관리하려는 솔루션 유형에 따라 솔루션 로드 관리자를 다양한 방식으로 구현할 수 있습니다.

 솔루션 로드 관리자가 일반적으로 솔루션 로드를 관리하려는 경우 VSPackage의 일부로 구현할 수 있습니다. 패키지를 값으로 <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> VSPackage에 추가하여 자동 로드하도록 설정해야 <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionOpening_guid>합니다. 그런 다음 메서드에서 솔루션 로드 <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> 관리자를 활성화할 수 있습니다.

> [!NOTE]
> 패키지 자동 로드에 대한 자세한 내용은 [VSPackage 로드를](../extensibility/loading-vspackages.md)참조하십시오.

 Visual Studio는 활성화할 마지막 솔루션 로드 관리자만 인식하므로 일반 솔루션 로드 관리자는 항상 자체 활성화전에 기존 로드 관리자가 있는지 여부를 감지해야 합니다. __VSPROPID4 `GetProperty()` 솔루션 서비스에 전화하는 [경우. 반환VSPROPID_ActiveSolutionLoadManager](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_ActiveSolutionLoadManager>) `null`활성 솔루션 로드 관리자가 없습니다. null을 반환하지 않으면 개체가 솔루션 로드 관리자와 동일한지 확인합니다.

 솔루션 로드 관리자가 몇 가지 유형의 솔루션만 관리하려는 경우 VSPackage는 호출을 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A>통해 솔루션 로드 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A> 이벤트를 구독하고 이벤트 처리기를 사용하여 솔루션 로드 관리자를 활성화할 수 있습니다.

 솔루션 로드 관리자가 특정 솔루션만 관리하려는 경우 사전 솔루션 섹션을 호출하여 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> 활성화 정보를 솔루션 파일의 일부로 유지관리할 수 있습니다.

 특정 솔루션 로드 관리자는 다른 솔루션 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents.OnAfterCloseSolution%2A> 로드 관리자와 충돌하지 않도록 이벤트 처리기에서 자신을 비활성화해야 합니다.

 전역 프로젝트 로드 속성을 유지(예: 옵션 페이지에 설정된 속성)를 유지하려면 솔루션 로드 관리자만 필요한 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> 경우 이벤트 처리기에서 솔루션 로드 관리자를 활성화하고 솔루션 속성에서 설정을 유지한 다음 솔루션 로드 관리자를 비활성화할 수 있습니다.

## <a name="handle-solution-load-events"></a>솔루션 로드 이벤트 처리
 솔루션 로드 이벤트를 구독하려면 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> 솔루션 로드 관리자를 활성화할 때 호출합니다. 을 구현하는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents>경우 다른 프로젝트 로드 속성과 관련된 이벤트에 응답할 수 있습니다.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A>: 이 이벤트는 솔루션을 열기 전에 발생합니다.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeBackgroundSolutionLoadBegins%2A>: 이 이벤트는 솔루션이 완전히 로드된 후 발생하지만 백그라운드 프로젝트 로드가 다시 시작되기 전에 발생합니다.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterBackgroundSolutionLoadComplete%2A>: 이 이벤트는 솔루션 로드 관리자가 있는지 여부에 관계없이 솔루션이 처음에 완전히 로드된 후에 발생합니다. 또한 솔루션이 완전히 로드될 때마다 백그라운드 로드 또는 수요 로드 후에 발생합니다. 동시에 다시 <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExistsAndFullyLoaded_guid> 활성화됩니다.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnQueryBackgroundLoadProjectBatch%2A>: 이 이벤트는 프로젝트(또는 프로젝트)를 로드하기 전에 발생합니다. 프로젝트를 로드하기 전에 다른 백그라운드 프로세스가 완료되도록 하려면 `pfShouldDelayLoadToNextIdle` **true로**설정합니다.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeLoadProjectBatch%2A>: 이 이벤트는 프로젝트 일괄 처리가 로드될 때 발생합니다. true이면 `fIsBackgroundIdleBatch` 프로젝트는 백그라운드에서 로드되어야 합니다. false이면 `fIsBackgroundIdleBatch` 사용자가 솔루션 탐색기에서 보류 중인 프로젝트를 확장하는 경우와 같이 사용자 요청의 결과로 프로젝트가 동기적으로 로드되어야 합니다. 이 이벤트를 처리하여 에서 수행해야 하는 고가의 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>작업을 수행할 수 있습니다.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterLoadProjectBatch%2A>: 이 이벤트는 프로젝트 일괄 처리가 로드된 후 발생합니다.

## <a name="detect-and-manage-solution-and-project-loading"></a>솔루션 및 프로젝트 로딩 감지 및 관리
 프로젝트 및 솔루션의 부하 상태를 감지하려면 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProperty%2A> 다음 값을 참조하십시오.

- [__VSPROPID4. VSPROPID_IsSolutionFullyLoaded](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_IsSolutionFullyLoaded>) `var` : `true` 그렇지 않으면 `false`솔루션및 모든 프로젝트가 로드되면 반환됩니다.

- [__VSPROPID4. VSPROPID_IsInBackgroundIdleLoadProjectBatch](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_IsInBackgroundIdleLoadProjectBatch>) `var` : `true` 프로젝트 일괄 처리가 현재 백그라운드에서 `false`로드되는 경우 반환됩니다.

- [__VSPROPID4. VSPROPID_IsInSyncDemandLoadProjectBatch](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_IsInSyncDemandLoadProjectBatch>) `var` : `true` 그렇지 않으면 `false`사용자 명령 또는 기타 명시적 로드의 결과로 프로젝트 일괄 처리가 동기적으로 로드되는 경우 반환됩니다.

- [__VSPROPID2. VSPROPID_IsSolutionClosing](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2.VSPROPID_IsSolutionClosing>) `var` : `true` 솔루션이 현재 닫혀 `false`있는 경우 반환됩니다.

- [__VSPROPID. VSPROPID_IsSolutionOpening](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID.VSPROPID_IsSolutionOpening>) `var` : `true` 그렇지 않으면 `false`솔루션이 현재 열려있는 경우 반환됩니다.

다음 방법 중 하나를 호출하여 프로젝트 및 솔루션이 로드되도록 할 수도 있습니다.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureSolutionIsLoaded%2A>: 이 메서드를 호출하면 메서드가 반환되기 전에 솔루션의 프로젝트가 로드됩니다.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectIsLoaded%2A>: 이 메서드를 호출하면 메서드가 `guidProject` 반환되기 전에 프로젝트가 로드됩니다.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectsAreLoaded%2A>: 이 메서드를 호출하면 메서드가 `guidProjectID` 반환되기 전에 프로젝트가 로드됩니다.
