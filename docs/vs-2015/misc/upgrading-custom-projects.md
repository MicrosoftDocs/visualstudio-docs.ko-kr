---
title: 사용자 지정 프로젝트 업그레이드 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- upgrading project systems
- projects [Visual Studio SDK], upgrading
- project system upgrades [Visual Studio]
ms.assetid: 262ada44-7689-44d8-bacb-9c6d33834d4e
caps.latest.revision: 11
manager: jillfra
ms.openlocfilehash: c91013e7d5650e82fd9e5f6e39e28c4609e4fbfe
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "82037209"
---
# <a name="upgrading-custom-projects"></a>사용자 지정 프로젝트 업그레이드
제품의 다른 Visual Studio 버전 간에 프로젝트 파일에 있는 정보를 변경하는 경우 이전 버전에서 새 버전으로의 프로젝트 파일 업그레이드를 지원해야 합니다. **Visual Studio 변환 마법사**에 참여할 수 있도록 하는 업그레이드를 지원 하려면 인터페이스를 구현 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> 합니다. 이 인터페이스에는 복사 업그레이드에 사용할 수 있는 메커니즘만 포함되어 있습니다. 프로젝트 업그레이드는 솔루션의 일부가 열릴 때 수행됩니다. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> 인터페이스는 프로젝트 팩터리에서 구현되거나 적어도 프로젝트 팩터리에서 얻을 수 있어야 합니다.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> 인터페이스를 사용하는 이전 메커니즘은 계속 지원되지만 프로젝트의 일부가 열릴 때 프로젝트 시스템을 개념적으로 업그레이드합니다. 따라서 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> 인터페이스는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> 인터페이스가 호출 또는 구현되더라도 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 환경에서 호출됩니다. 이 접근 방식을 사용하면 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>를 사용하여 업그레이드의 복사 및 프로젝트 전용 부분을 구현하고 나머지 작업은 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> 인터페이스에서 바로(아마도 새 위치에서) 수행하도록 위임할 수 있습니다.  
  
 의 샘플 구현에 대 한 자세한 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> 내용은를 참조 [하십시오](../misc/vssdk-samples.md).  
  
 프로젝트 업그레이드에서는 다음과 같은 시나리오가 발생합니다.  
  
- 파일이 프로젝트에서 지원할 수 있는 형식보다 최신 형식인 경우 이를 설명하는 오류를 반환해야 합니다. 여기서는 제품의 이전 버전(예: Visual Studio.NET 2003)에 버전을 확인하는 코드가 포함되어 있다고 가정합니다.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> 메서드에 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> 플래그가 지정된 경우 업그레이드는 프로젝트를 열기 전에 현재 위치 업그레이드로 구현됩니다.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> 메서드에 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> 플래그가 지정된 경우 업그레이드는 복사 업그레이드로 구현됩니다.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> 호출에 <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> 플래그가 지정된 경우 프로젝트가 열린 후 환경에서 사용자에게 프로젝트 파일을 현재 위치 업그레이드로 업그레이드하라는 메시지를 표시했습니다. 예를 들어 사용자가 이전 버전의 솔루션을 여는 경우 업그레이드하라는 메시지가 표시됩니다.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> 호출에 <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> 플래그가 지정되지 않은 경우에는 사용자에게 프로젝트 파일을 업그레이드하라는 메시지를 표시해야 합니다.  
  
     다음은 업그레이드 프롬프트 메시지의 예입니다.  
  
     "'%1' 프로젝트는 이전 버전의 Visual Studio에서 만들었습니다. 이 버전의 Visual Studio에서 이 프로젝트를 열면 이전 버전의 Visual Studio에서 이 프로젝트를 열 수 없습니다. 이 프로젝트를 계속 여시겠습니까?”  
  
### <a name="to-implement-ivsprojectupgradeviafactory"></a>IVsProjectUpgradeViaFactory를 구현하려면  
  
1. 프로젝트 팩터리 구현에서 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> 인터페이스의 메서드 특히, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> 메서드를 구현하거나 프로젝트 팩터리 구현에서 해당 구현을 호출할 수 있게 합니다.  
  
2. 솔루션 열기의 일부로 현재 위치 업그레이드를 수행하려는 경우 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> 구현에서 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> 플래그를 `VSPUVF_FLAGS` 매개 변수로 제공합니다.  
  
3. 솔루션 열기의 일부로 현재 위치 업그레이드를 수행하려는 경우 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> 구현에서 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS> 플래그를 `VSPUVF_FLAGS` 매개 변수로 제공합니다.  
  
4. 2단계와 3단계 모두의 경우 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>를 사용하는 실제 파일 업그레이드 단계는 아래의 “구현`IVsProjectUpgade`” 섹션에 설명된 대로 구현할 수도 있고 실제 파일 업그레이드를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>에 위임할 수도 있습니다.  
  
5. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger>의 메서드를 사용하여 Visual Studio 마이그레이션 마법사를 사용하는 사용자에게 업그레이드 관련 메시지를 게시합니다.  
  
6. <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileUpgrade> 인터페이스는 프로젝트 업그레이드의 일부로 수행해야 하는 모든 종류의 파일 업그레이드를 구현하는 데 사용됩니다. 이 인터페이스는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>에서 호출되지는 않지만, 프로젝트 시스템의 일부이지만 기본 프로젝트 시스템에서 직접적으로 알지 못할 수도 있는 파일을 업그레이드하는 메커니즘을 제공됩니다. 예를 들어 나머지 프로젝트 시스템을 처리하는 개발 팀이 컴파일러 관련 파일 및 속성을 처리하지 않는 경우 이러한 상황이 발생할 수 있습니다.  
  
## <a name="ivsprojectupgrade-implementation"></a>IVsProjectUpgrade 구현  
 프로젝트 시스템에서를 구현 하는 경우에는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> **Visual Studio 변환 마법사**에 참여할 수 없습니다. 그러나 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> 인터페이스를 구현하더라도 여전히 파일 업그레이드를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> 구현에 위임할 수는 있습니다.  
  
#### <a name="to-implement-ivsprojectupgrade"></a>IVsProjectUpgrade를 구현하려면  
  
1. 사용자가 프로젝트를 열면 프로젝트가 열린 후 프로젝트에 대한 다른 사용자 작업을 수행할 수 있기 전에 환경에서 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> 메서드가 호출됩니다. 사용자에게 솔루션을 업그레이드하라는 메시지가 이미 표시된 경우 <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> 플래그가 `grfUpgradeFlags` 매개 변수에 전달됩니다. 사용자가 **기존 프로젝트 추가** 명령을 사용 하는 등의 방법으로 프로젝트를 직접 여는 경우 <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS> 플래그가 전달 되지 않으며 프로젝트에서 사용자에 게 업그레이드할지 묻는 메시지를 표시 해야 합니다.  
  
2. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> 호출에 응답하여 프로젝트에서는 프로젝트 파일이 업그레이드되었는지 평가해야 합니다. 프로젝트에서 프로젝트 형식을 새 버전으로 업그레이드할 필요가 없는 경우에는 간단히 <xref:Microsoft.VisualStudio.VSConstants.S_OK> 플래그를 반환할 수 있습니다.  
  
3. 프로젝트에서 프로젝트 형식을 새 버전으로 업그레이드해야 하는 경우에는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> 메서드를 호출하고 <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> 값을 `rgfQueryEdit` 매개 변수에 전달하여 프로젝트 파일을 수정할 수 있는지 여부를 확인해야 합니다. 그런 다음 프로젝트에서 다음을 수행해야 합니다.  
  
   - `pfEditCanceled` 매개 변수에서 반환된 `VSQueryEditResult` 값이 <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult>인 경우 프로젝트 파일을 쓸 수 있으므로 업그레이드를 진행할 수 있습니다.  
  
   - `pfEditCanceled` 매개 변수에서 반환된 `VSQueryEditResult` 값이 <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult>이고 `VSQueryEditResult` 값에 <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> 비트가 설정된 경우에는 사용자가 권한 문제를 직접 해결해야 하므로 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>에서 오류를 반환해야 합니다. 그런 다음 프로젝트에서 다음을 수행해야 합니다.  
  
        <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>를 호출하여 사용자에게 오류를 보고합니다. 그리고 <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes> 오류 코드를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>에 반환합니다.  
  
   - `VSQueryEditResult` 값이 <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult>이고 `VSQueryEditResultFlags` 값에 <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> 비트가 설정된 경우에서 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>, <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>,...)를 호출하여 프로젝트 파일을 체크 아웃해야 합니다.  
  
4. 프로젝트 파일에 대한 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> 호출로 파일이 체크 아웃되고 최신 버전이 검색되는 경우에는 프로젝트가 언로드되었다가 다시 로드됩니다. 프로젝트의 다른 인스턴스가 생성되면 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> 메서드가 다시 호출됩니다. 이 두 번째 호출에서 프로젝트 파일을 디스크에 쓸 수 있습니다. 프로젝트에서 프로젝트 파일의 복사본을 .OLD 확장명을 사용하는 이전 형식으로 저장하고 필요한 업그레이드 변경을 수행한 다음 프로젝트 파일을 새 형식으로 저장하는 것이 좋습니다. 마찬가지로 업그레이드 프로세스의 일부가 실패하면 메서드에서는 <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes>를 반환하여 오류를 표시해야 합니다. 이로 인해 솔루션 탐색기에서 프로젝트가 언로드됩니다.  
  
    <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> 메서드 호출(ReportOnly 값 지정)에서 <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult> 및 <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> 플래그를 반환하는 경우에 대해 환경에서 수행되는 전체 프로세스를 이해해야 합니다.  
  
5. 사용자가 프로젝트 파일을 열려고 합니다.  
  
6. 환경에서 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> 구현을 호출합니다.  
  
7. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A>가 `true`를 반환하는 경우 환경에서 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> 구현을 호출합니다.  
  
8. 환경에서 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> 구현을 호출하여 파일을 열고 프로젝트 개체(예: Project1)를 초기화합니다.  
  
9. 환경에서 `IVsProjectUpgrade::UpgradeProject` 구현을 호출하여 프로젝트 파일을 업그레이드해야 하는지 여부를 확인합니다.  
  
10. <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>를 호출하고 <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> 값을 `rgfQueryEdit` 매개 변수에 전달합니다.  
  
11. 환경에서 `VSQueryEditResult`에 대해 <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult>를 반환하고 `VSQueryEditResultFlags`에 <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags> 비트가 설정되 었습니다.  
  
12. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> 구현에서 `IVsQueryEditQuerySave::QueryEditFiles` (<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>, <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags>)를 호출합니다.  
  
    이 호출로 인해 프로젝트 파일의 새 복사본이 체크 아웃되고 최신 버전이 검색될 수 있으며 프로젝트 파일을 다시 로드해야 합니다. 이때 다음 두 가지 중 하나가 발생합니다.  
  
- 프로젝트 다시 로드를 직접 처리하는 경우 환경에서 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> (VSITEMID_ROOT) 구현을 호출합니다. 이 호출을 받는 경우 프로젝트의 첫 번째 인스턴스(Project1)를 다시 로드하고 계속 프로젝트 파일을 업그레이드합니다. <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>)에 대해 `true`를 반환하는 경우 환경에서 사용자가 프로젝트 다시 로드를 직접 처리한다고 인식합니다.  
  
- 프로젝트 다시 로드를 직접 처리하지 않는 경우에는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>)에 대해 `false`를 반환합니다. 이 경우 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> ([QEF_ForceEdit_NoPrompting](/dotnet/api/microsoft.visualstudio.shell.interop.tagvsqueryeditflags), [QEF_DisallowInMemoryEdits](/dotnet/api/microsoft.visualstudio.shell.interop.tagvsqueryeditflags))가를 반환 하기 전에 환경에서 다음과 같이 프로젝트의 다른 새 인스턴스 (예: Project2)를 만듭니다.  
  
  1. 환경에서 첫 번째 프로젝트 개체 Project1에 대해 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.Close%2A>를; 호출하여 이 개체를 비활성 상태로 둡니다.  
  
  2. 환경에서 `IVsProjectFactory::CreateProject` 구현하여 프로젝트의 두 번째 인스턴스 Project2를 만듭니다.  
  
  3. 환경에서 `IPersistFileFormat::Load` 구현을 호출하여 파일을 열고 두 번째 프로젝트 개체 Project2를 초기화합니다.  
  
  4. 환경에서 `IVsProjectUpgrade::UpgradeProject` 를 두 번째로 호출하여 프로젝트 개체를 업그레이드해야 하는지 여부를 결정합니다. 그러나 이 호출은 프로젝트의 새로운 두 번째 인스턴스 Project2에 대해 수행됩니다. 이 프로젝트가 솔루션에 열려 있는 프로젝트입니다.  
  
      > [!NOTE]
      > 첫 번째 프로젝트 Project1이 비활성 상태로 있는 인스턴스에서는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> 구현에 대한 첫 번째 호출에서 <xref:Microsoft.VisualStudio.VSConstants.S_OK>를 반환해야 합니다. 의 구현에 대 한 [기본 프로젝트](https://msdn.microsoft.com/385fd2a3-d9f1-4808-87c2-a3f05a91fc36) 를 참조 하세요 `IVsProjectUpgrade::UpgradeProject` .  
  
  5. <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>를 호출하고 <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> 값을 `rgfQueryEdit` 매개 변수에 전달합니다.  
  
  6. 환경에서 <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult>를 반환하고 프로젝트 파일을 쓸 수 있으므로 업그레이드를 진행할 수 있습니다.  
  
  업그레이드하지 않으면 `IVsProjectUpgrade::UpgradeProject`에서 <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes>를 반환합니다. 업그레이드가 필요하지 않거나 업그레이드하지 않으려면 `IVsProjectUpgrade::UpgradeProject` 호출을 no-op으로 처리합니다. <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes>를 반환하는 경우 프로젝트에 대한 자리 표시자 노드가 솔루션에 추가됩니다.  
  
## <a name="see-also"></a>관련 항목  
 [Visual Studio 변환 마법사](https://msdn.microsoft.com/4acfd30e-c192-4184-a86f-2da5e4c3d83c)   
 [프로젝트 항목 업그레이드](../misc/upgrading-project-items.md)   
 [프로젝트](../extensibility/internals/projects.md)