---
title: 솔루션에서 프로젝트 로드 관리 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- solutions, managing project loading
ms.assetid: 097c89d0-f76a-4aaf-ada9-9a778bd179a0
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a6598e2f1a178845b3ad2017716576439185379e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841450"
---
# <a name="managing-project-loading-in-a-solution"></a>솔루션의 프로젝트 로드 관리
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 솔루션에는 여러 개의 프로젝트가 포함 될 수 있습니다. 기본 Visual Studio 동작은 솔루션이 열릴 때 솔루션의 모든 프로젝트를 로드 하 고, 모든 프로젝트가 로드를 완료할 때까지 사용자가 프로젝트에 액세스할 수 없도록 하는 것입니다. 프로젝트 로드 프로세스가 2 분 이상 지속 되 면 로드 된 프로젝트 수와 총 프로젝트 수를 보여 주는 진행률 표시줄이 표시 됩니다. 사용자는 여러 프로젝트를 사용 하는 솔루션에서 작업 하는 동안 프로젝트를 언로드할 수 있지만이 절차에는 몇 가지 단점이 있습니다. 언로드된 프로젝트는 솔루션 다시 빌드 명령의 일부로 빌드되지 않으며 닫힌 프로젝트의 형식 및 멤버에 대 한 IntelliSense 설명이 표시 되지 않습니다.  
  
 개발자는 솔루션 로드 시간을 줄이고 솔루션 부하 관리자를 만들어 프로젝트 로드 동작을 관리할 수 있습니다. 솔루션 로드 관리자는 특정 프로젝트 또는 프로젝트 형식에 대해 다른 프로젝트 로드 우선 순위를 설정할 수 있습니다. 백그라운드 빌드를 시작 하기 전에 프로젝트가 로드 되는지 확인 하 고, 다른 백그라운드 작업이 완료 될 때까지 백그라운드 로드를 지연 하 고, 다른 프로젝트 로드 관리 작업을 수행할 수 있습니다.  
  
## <a name="project-loading-priorities"></a>프로젝트 로드 우선 순위  
 Visual Studio는 네 가지 프로젝트 로드 우선 순위를 정의 합니다.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority> (기본값): 솔루션이 열리면 프로젝트가 비동기적으로 로드 됩니다. 솔루션이 이미 열려 있는 상태에서이 우선 순위가 언로드된 프로젝트에 설정 되어 있으면 프로젝트가 다음 유휴 지점에 로드 됩니다.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: 솔루션이 열리면 프로젝트가 백그라운드에서 로드 되어 모든 프로젝트가 로드 될 때까지 기다리지 않고 로드 될 때 사용자가 프로젝트에 액세스할 수 있습니다.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: 프로젝트에 액세스할 때 로드 됩니다. 프로젝트가 열린 문서 목록 (솔루션의 사용자 옵션 파일에 저장 됨)에 있거나 로드 되 고 있는 다른 프로젝트에 종속성이 있는 경우 사용자가 프로젝트의 프로젝트 솔루션 탐색기 노드를 확장할 때 프로젝트에 액세스할 때 해당 프로젝트에 액세스할 수 있습니다. 이 형식의 프로젝트는 빌드 프로세스를 시작 하기 전에 자동으로 로드 되지 않습니다. 솔루션 로드 관리자는 필요한 모든 프로젝트가 로드 되도록 하는 일을 담당 합니다. 이러한 프로젝트는 전체 솔루션에서 파일의 찾기/바꾸기를 시작 하기 전에 로드 해야 합니다.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop._VSProjectLoadPriority>: 사용자가 명시적으로 요청 하지 않는 한 프로젝트를 로드 하지 않습니다. 프로젝트가 명시적으로 언로드되는 경우입니다.  
  
## <a name="creating-a-solution-load-manager"></a>솔루션 부하 관리자 만들기  
 개발자는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager> Visual Studio에서 솔루션 부하 관리자를 구현 하 고이를 구현 하 여 솔루션 부하 관리자를 만들 수 있습니다.  
  
#### <a name="activating-a-solution-load-manager"></a>솔루션 부하 관리자 활성화  
 Visual Studio는 지정 된 시간에 하나의 솔루션 로드 관리자만 허용 하므로 솔루션 로드 관리자를 활성화 하려면 Visual Studio에 대해 권고 해야 합니다. 나중에 두 번째 솔루션 부하 관리자를 활성화 하는 경우 솔루션 로드 관리자의 연결이 끊깁니다.  
  
 서비스를 가져오고 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution> 속성을 설정 해야 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> .  
  
```csharp  
IVsSolution pSolution = GetService(typeof(SVsSolution)) as IVsSolution;  
object objLoadMgr = this;   //the class that implements IVsSolutionManager  
pSolution.SetProperty((int)__VSPROPID4.VSPROPID_ActiveSolutionLoadManager, objLoadMgr);  
```  
  
#### <a name="implementing-ivssolutionloadmanager"></a>Ivs솔루션 Loadmanager 구현  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnBeforeOpenProject%2A>메서드는 솔루션을 여는 과정에서 호출 됩니다. 이 메서드를 구현 하려면 서비스를 사용 하 여 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManagerSupport> 관리 하려는 프로젝트 형식에 대 한 로드 우선 순위를 설정 합니다. 예를 들어 다음 코드는 백그라운드에서 로드 하는 c # 프로젝트 형식을 설정 합니다.  
  
```csharp  
Guid guidCSProjectType = new Guid("{FAE04EC0-301F-11d3-BF4B-00C04F79EFBC}");  
pSLMgrSupport.SetProjectLoadPriority(guidProjectID, (uint)_VSProjectLoadPriority.PLP_BackgroundLoad);  
```  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnDisconnect%2A>메서드는 Visual Studio가 종료 될 때 또는 속성을 사용 하 여를 호출 하 여 다른 패키지가 활성 솔루션 로드 관리자로 수행 될 때 호출 됩니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.SetProperty%2A> <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> .  
  
#### <a name="strategies-for-different-kinds-of-solution-load-manager"></a>여러 종류의 솔루션 부하 관리자에 대 한 전략  
 관리 하려는 솔루션 유형에 따라 다양 한 방법으로 솔루션 부하 관리자를 구현할 수 있습니다.  
  
 솔루션 부하 관리자가 솔루션 로드를 일반적으로 관리 하려는 경우에는 VSPackage의 일부로 구현할 수 있습니다. VSPackage에 값을 추가 하 여 패키지를 autoload로 설정 해야 합니다 <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionOpening_guid> . 그런 다음 메서드에서 솔루션 로드 관리자를 활성화할 수 있습니다 <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> .  
  
> [!NOTE]
> 자동 로드 패키지에 대 한 자세한 내용은 [Vspackage 로드](../extensibility/loading-vspackages.md)를 참조 하세요.  
  
 Visual Studio는 활성화 될 마지막 솔루션 로드 관리자만 인식 하므로 일반 솔루션 부하 관리자는 자신을 활성화 하기 전에 항상 기존 부하 관리자가 있는지 여부를 검색 해야 합니다. 솔루션 서비스에서에 대 한 GetProperty () 호출 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4> `null` 을 반환 하는 경우 활성 솔루션 로드 관리자가 없습니다. Null을 반환 하지 않으면 해당 개체가 솔루션 로드 관리자와 동일한 지 확인 합니다.  
  
 솔루션 부하 관리자가 몇 가지 유형의 솔루션만 관리 하는 경우 VSPackage는를 호출 하 여 솔루션 로드 이벤트를 구독 하 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> 고에 대 한 이벤트 처리기를 사용 하 여 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A> 솔루션 부하 관리자를 활성화할 수 있습니다.  
  
 솔루션 부하 관리자가 특정 솔루션을 관리 하려는 경우에는 솔루션 파일의 일부로 활성화 정보를 유지할 수 있습니다. 이렇게 하려면 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> 이전 솔루션 섹션에 대해를 호출 합니다.  
  
 특정 솔루션 부하 관리자는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents.OnAfterCloseSolution%2A> 다른 솔루션 부하 관리자와 충돌 하지 않도록 이벤트 처리기에서 자신을 비활성화 해야 합니다.  
  
 전역 프로젝트 로드 우선 순위 (예: 옵션 페이지에 설정 된 속성)를 유지 하기 위한 솔루션 로드 관리자만 필요한 경우 이벤트 처리기에서 솔루션 로드 관리자를 활성화 하 고 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents2.OnAfterOpenProject%2A> 솔루션 속성에서 설정을 유지 한 다음 솔루션 로드 관리자를 비활성화할 수 있습니다.  
  
## <a name="handling-solution-load-events"></a>솔루션 로드 이벤트 처리  
 솔루션 로드 이벤트를 구독 하려면 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> 솔루션 로드 관리자를 활성화할 때를 호출 합니다. 을 구현 하 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents> 는 경우 다른 프로젝트 로드 우선 순위와 관련 된 이벤트에 응답할 수 있습니다.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A>: 솔루션이 열리기 전에 발생 합니다. 이를 사용 하 여 솔루션의 프로젝트에 대 한 프로젝트 로드 우선 순위를 변경할 수 있습니다.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeBackgroundSolutionLoadBegins%2A>: 솔루션이 완전히 로드 된 후 백그라운드 프로젝트 로드가 다시 시작 되기 전에 발생 합니다. 예를 들어 사용자가 로드 우선 순위가 LoadIfNeeded 프로젝트에 액세스 했거나, 솔루션 부하 관리자가 프로젝트 로드 우선 순위를 BackgroundLoad로 변경 했을 수 있습니다. 그러면 해당 프로젝트의 백그라운드 로드가 시작 됩니다.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterBackgroundSolutionLoadComplete%2A>: 솔루션 부하 관리자가 있는지 여부에 관계 없이 처음에 솔루션을 완전히 로드 한 후에 발생 합니다. 솔루션이 완전히 로드 될 때마다 백그라운드 로드 나 수요 로드 후에도 발생 합니다. 동시에 <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExistsAndFullyLoaded_guid> 가 다시 활성화 됩니다.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnQueryBackgroundLoadProjectBatch%2A>: 프로젝트 또는 프로젝트를 로드 하기 전에 발생 합니다. 프로젝트를 로드 하기 전에 다른 백그라운드 프로세스가 완료 되도록 하려면를 `pfShouldDelayLoadToNextIdle` **true**로 설정 합니다.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeLoadProjectBatch%2A>:이는 프로젝트의 일괄 처리가 로드 될 때 발생 합니다. `fIsBackgroundIdleBatch`이 true 이면 프로젝트가 백그라운드에서 로드 되 고, `fIsBackgroundIdleBatch` 이 false 이면 사용자 요청 결과로 프로젝트가 동기적으로 로드 됩니다. 예를 들어 사용자가 솔루션 탐색기에서 보류 중인 프로젝트를 확장 합니다. 이를 구현 하 여에서 수행 해야 하는 비용이 많이 드는 작업을 수행할 수 있습니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> .  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterLoadProjectBatch%2A>: 프로젝트 일괄 처리가 로드 된 후에 발생 합니다.  
  
## <a name="detecting-and-managing-solution-and-project-loading"></a>솔루션 및 프로젝트 로드 검색 및 관리  
 프로젝트 및 솔루션의 로드 상태를 검색 하려면 다음 값을 사용 하 여를 호출 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProperty%2A> .  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` `true` 솔루션과 모든 프로젝트가 로드 되 면를 반환 하 고, 그렇지 않으면를 반환 `false` 합니다.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` `true` 프로젝트의 일괄 처리가 현재 백그라운드에서 로드 되 고 있으면를 반환 하 고, 그렇지 않으면를 반환 `false` 합니다.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4>: `var` `true` 사용자 명령 또는 다른 명시적 로드의 결과로 현재 프로젝트 일괄 처리가 동기적으로 로드 되 고 있으면를 반환 하 고 그렇지 않으면를 반환 `false` 합니다.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>: `var` `true` 솔루션을 현재 닫고 있으면를 반환 하 고, 그렇지 않으면를 반환 `false` 합니다.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>: `var` `true` 솔루션이 현재 열려 있으면를 반환 하 고, 그렇지 않으면를 반환 `false` 합니다.  
  
  다음 방법 중 하나를 호출 하 여 프로젝트와 솔루션이 로드 되는지 확인할 수도 있습니다 (프로젝트 로드 우선 순위에 관계 없이).  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureSolutionIsLoaded%2A>:이 메서드를 호출 하면 메서드가 반환 되기 전에 솔루션의 프로젝트가 로드 됩니다.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectIsLoaded%2A>:이 메서드 `guidProject` 를 호출 하면 메서드가 반환 되기 전에의 프로젝트가 로드 됩니다.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectsAreLoaded%2A>:이 메서드 `guidProjectID` 를 호출 하면 메서드가 반환 되기 전에의 프로젝트가 로드 됩니다.  
  
> [!NOTE]
> . 기본적으로 요청 부하 및 백그라운드 로드 우선 순위가 있는 프로젝트만 로드 되지만 <xref:Microsoft.VisualStudio.Shell.Interop.__VSBSLFLAGS> 플래그가 메서드에 전달 되 면 명시적으로 로드 하도록 표시 된 프로젝트를 제외 하 고 모든 프로젝트가 로드 됩니다.
