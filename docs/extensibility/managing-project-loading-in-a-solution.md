---
title: 솔루션에서 프로젝트 로드 관리 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80702727"
---
# <a name="manage-project-loading-in-a-solution"></a>솔루션에서 프로젝트 로드 관리
Visual Studio 솔루션에는 여러 개의 프로젝트가 포함 될 수 있습니다. 기본 Visual Studio 동작은 솔루션이 열릴 때 솔루션의 모든 프로젝트를 로드 하 고, 모든 프로젝트가 로드를 완료할 때까지 사용자가 프로젝트에 액세스할 수 없도록 하는 것입니다. 프로젝트 로드 프로세스가 2 분 이상 지속 되 면 로드 된 프로젝트 수와 총 프로젝트 수를 보여 주는 진행률 표시줄이 표시 됩니다. 사용자는 여러 프로젝트를 사용 하는 솔루션에서 작업 하는 동안 프로젝트를 언로드할 수 있지만이 절차에는 몇 가지 단점이 있습니다. 언로드된 프로젝트는 솔루션 다시 빌드 명령의 일부로 빌드되지 않으며 닫힌 프로젝트의 형식 및 멤버에 대 한 IntelliSense 설명이 표시 되지 않습니다.

 개발자는 솔루션 로드 시간을 줄이고 솔루션 부하 관리자를 만들어 프로젝트 로드 동작을 관리할 수 있습니다. 솔루션 로드 관리자는 백그라운드 빌드를 시작 하기 전에 프로젝트가 로드 되 고 다른 백그라운드 작업이 완료 될 때까지 백그라운드 로드를 지연 하 고 다른 프로젝트 로드 관리 작업을 수행할 수 있습니다.

## <a name="create-a-solution-load-manager"></a>솔루션 부하 관리자 만들기
 개발자는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager> Visual Studio에서 솔루션 부하 관리자를 구현 하 고이를 구현 하 여 솔루션 부하 관리자를 만들 수 있습니다.

### <a name="activate-a-solution-load-manager"></a>솔루션 부하 관리자 활성화
 Visual Studio는 지정 된 시간에 하나의 솔루션 로드 관리자만 허용 하므로 솔루션 로드 관리자를 활성화 하려면 Visual Studio에 대해 권고 해야 합니다. 나중에 두 번째 솔루션 부하 관리자를 활성화 하는 경우 솔루션 로드 관리자의 연결이 끊깁니다.

 서비스를 가져오고 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution> __VSPROPID4를 설정 해야 합니다 [. VSPROPID_ActiveSolutionLoadManager](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_ActiveSolutionLoadManager>) 속성:

```csharp
IVsSolution pSolution = GetService(typeof(SVsSolution)) as IVsSolution;
object objLoadMgr = this;   //the class that implements IVsSolutionManager
pSolution.SetProperty((int)__VSPROPID4.VSPROPID_ActiveSolutionLoadManager, objLoadMgr);
```

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnDisconnect%2A>메서드는 Visual Studio가 종료 되는 경우 또는 __VSPROPID4를 사용 하 여를 호출 하 여 다른 패키지가 활성 솔루션 로드 관리자로 수행 될 때 호출 됩니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.SetProperty%2A> [. VSPROPID_ActiveSolutionLoadManager](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_ActiveSolutionLoadManager>) 속성입니다.

#### <a name="strategies-for-different-kinds-of-solution-load-manager"></a>여러 종류의 솔루션 부하 관리자에 대 한 전략
 관리 하려는 솔루션 유형에 따라 다양 한 방법으로 솔루션 부하 관리자를 구현할 수 있습니다.

 솔루션 부하 관리자가 솔루션 로드를 일반적으로 관리 하려는 경우에는 VSPackage의 일부로 구현할 수 있습니다. VSPackage에 값을 추가 하 여 패키지를 autoload로 설정 해야 합니다 <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionOpening_guid> . 그런 다음 메서드에서 솔루션 로드 관리자를 활성화할 수 있습니다 <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> .

> [!NOTE]
> 자동 로드 패키지에 대 한 자세한 내용은 [Vspackage 로드](../extensibility/loading-vspackages.md)를 참조 하세요.

 Visual Studio는 활성화 될 마지막 솔루션 로드 관리자만 인식 하므로 일반 솔루션 부하 관리자는 자신을 활성화 하기 전에 항상 기존 부하 관리자가 있는지 여부를 검색 해야 합니다. `GetProperty()`__VSPROPID4에 대 한 솔루션 서비스에서를 호출 하는 경우 [입니다. ](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_ActiveSolutionLoadManager>)가 반환 VSPROPID_ActiveSolutionLoadManager `null` 활성 솔루션 로드 관리자가 없습니다. Null을 반환 하지 않으면 해당 개체가 솔루션 로드 관리자와 동일한 지 확인 합니다.

 솔루션 부하 관리자가 몇 가지 유형의 솔루션만 관리 하는 경우 VSPackage는를 호출 하 여 솔루션 로드 이벤트를 구독 하 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> 고에 대 한 이벤트 처리기를 사용 하 여 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A> 솔루션 부하 관리자를 활성화할 수 있습니다.

 솔루션 로드 관리자가 특정 솔루션을 관리 하려는 경우에는 솔루션 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> 이전 섹션에 대해를 호출 하 여 솔루션 파일의 일부로 활성화 정보를 유지할 수 있습니다.

 특정 솔루션 부하 관리자는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents.OnAfterCloseSolution%2A> 다른 솔루션 부하 관리자와 충돌 하지 않도록 이벤트 처리기에서 자신을 비활성화 해야 합니다.

 전역 프로젝트 로드 속성 (예: 옵션 페이지에 설정 된 속성)을 유지 하기 위해서만 솔루션 로드 관리자가 필요한 경우 이벤트 처리기에서 솔루션 로드 관리자를 활성화 하 고 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> 솔루션 속성에서 설정을 유지 한 다음 솔루션 로드 관리자를 비활성화할 수 있습니다.

## <a name="handle-solution-load-events"></a>솔루션 로드 이벤트 처리
 솔루션 로드 이벤트를 구독 하려면 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> 솔루션 로드 관리자를 활성화할 때를 호출 합니다. 을 구현 하 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents> 는 경우 다른 프로젝트 로드 속성과 관련 된 이벤트에 응답할 수 있습니다.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A>:이 이벤트는 솔루션이 열리기 전에 발생 합니다.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeBackgroundSolutionLoadBegins%2A>:이 이벤트는 솔루션이 완전히 로드 된 후 백그라운드 프로젝트 로드를 다시 시작 하기 전에 발생 합니다.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterBackgroundSolutionLoadComplete%2A>:이 이벤트는 솔루션 로드 관리자가 있는지 여부에 관계 없이 처음에 솔루션을 완전히 로드 한 후에 발생 합니다. 솔루션이 완전히 로드 될 때마다 백그라운드 로드 나 수요 로드 후에도 발생 합니다. 동시에 <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExistsAndFullyLoaded_guid> 가 다시 활성화 됩니다.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnQueryBackgroundLoadProjectBatch%2A>:이 이벤트는 프로젝트 또는 프로젝트를 로드 하기 전에 발생 합니다. 프로젝트를 로드 하기 전에 다른 백그라운드 프로세스가 완료 되도록 하려면를 `pfShouldDelayLoadToNextIdle` **true**로 설정 합니다.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeLoadProjectBatch%2A>:이 이벤트는 프로젝트 일괄 처리가 로드 될 때 발생 합니다. `fIsBackgroundIdleBatch`이 true 이면 프로젝트가 백그라운드에서 로드 되 고, `fIsBackgroundIdleBatch` 이 false 이면 사용자 요청 결과로 프로젝트가 동기적으로 로드 됩니다. 예를 들어 사용자가 솔루션 탐색기에서 보류 중인 프로젝트를 확장 합니다. 이 이벤트를 처리 하 여에서 수행 해야 하는 비용이 많이 드는 작업을 수행할 수 있습니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> .

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterLoadProjectBatch%2A>:이 이벤트는 프로젝트 일괄 처리가 로드 된 후에 발생 합니다.

## <a name="detect-and-manage-solution-and-project-loading"></a>솔루션 및 프로젝트 로드 검색 및 관리
 프로젝트 및 솔루션의 로드 상태를 검색 하려면 다음 값을 사용 하 여를 호출 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProperty%2A> .

- [__VSPROPID4. VSPROPID_IsSolutionFullyLoaded](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_IsSolutionFullyLoaded>): `var` `true` 솔루션과 모든 프로젝트가 로드 되 면를 반환 하 고, 그렇지 않으면를 반환 `false` 합니다.

- [__VSPROPID4. VSPROPID_IsInBackgroundIdleLoadProjectBatch](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_IsInBackgroundIdleLoadProjectBatch>): `var` `true` 프로젝트의 일괄 처리가 현재 백그라운드에서 로드 되 고 있으면를 반환 하 고, 그렇지 않으면를 반환 `false` 합니다.

- [__VSPROPID4. VSPROPID_IsInSyncDemandLoadProjectBatch](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_IsInSyncDemandLoadProjectBatch>): `var` `true` 현재 사용자 명령 또는 다른 명시적 로드의 결과로 프로젝트의 일괄 처리가 현재 동기적으로 로드 되 고 있으면를 반환 하 고, 그렇지 않으면를 반환 `false` 합니다.

- [__VSPROPID2. VSPROPID_IsSolutionClosing](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2.VSPROPID_IsSolutionClosing>): `var` `true` 솔루션을 현재 닫고 있으면를 반환 하 고, 그렇지 않으면를 반환 `false` 합니다.

- [__VSPROPID. VSPROPID_IsSolutionOpening](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID.VSPROPID_IsSolutionOpening>): `var` `true` 솔루션이 현재 열려 있으면를 반환 하 고, 그렇지 않으면를 반환 `false` 합니다.

다음 메서드 중 하나를 호출 하 여 프로젝트 및 솔루션을 로드 하도록 할 수도 있습니다.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureSolutionIsLoaded%2A>:이 메서드를 호출 하면 메서드가 반환 되기 전에 솔루션의 프로젝트가 로드 됩니다.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectIsLoaded%2A>:이 메서드 `guidProject` 를 호출 하면 메서드가 반환 되기 전에의 프로젝트가 로드 됩니다.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectsAreLoaded%2A>:이 메서드 `guidProjectID` 를 호출 하면 메서드가 반환 되기 전에의 프로젝트가 로드 됩니다.
