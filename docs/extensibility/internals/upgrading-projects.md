---
title: 프로젝트 업그레이드 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- upgrading VSPackages
- upgrading applications, strategies
- VSPackages, upgrade support
ms.assetid: e01cb44a-8105-4cf4-8223-dfae65f8597a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a99207fc14cf9f462bc1abc88d6fed166ea6523f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704260"
---
# <a name="upgrading-projects"></a>프로젝트 업그레이드

한 버전의 Visual Studio에서 다음 버전으로 프로젝트 모델을 변경하려면 프로젝트와 솔루션을 업그레이드하여 최신 버전에서 실행할 수 있습니다. 이 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] 인터페이스는 자체 프로젝트에서 업그레이드 지원을 구현하는 데 사용할 수 있는 인터페이스를 제공합니다.

## <a name="upgrade-strategies"></a>업그레이드 전략

업그레이드를 지원하려면 프로젝트 시스템 구현에서 업그레이드 전략을 정의하고 구현해야 합니다. 전략을 결정할 때 나란히(SxS) 백업, 복사 백업 또는 둘 다를 지원하도록 선택할 수 있습니다.

- SxS 백업은 프로젝트가 적절한 파일 이름 접미사(예: ".old")를 추가하여 업그레이드가 필요한 파일만 복사한다는 것을 의미합니다.

- 복사 백업은 프로젝트가 사용자가 제공한 백업 위치에 모든 프로젝트 항목을 복사한다는 것을 의미합니다. 그런 다음 원래 프로젝트 위치에 있는 관련 파일이 업그레이드됩니다.

## <a name="how-upgrade-works"></a>업그레이드 작동 방식

이전 버전의 Visual Studio에서 만든 솔루션이 최신 버전에서 열리면 IDE는 솔루션 파일을 검사하여 업그레이드해야 하는지 확인합니다. 업그레이드가 필요한 경우 **업그레이드 마법사가** 자동으로 시작되어 업그레이드 프로세스를 진행합니다.

솔루션을 업그레이드해야 하는 경우 각 프로젝트 팩터리에서 업그레이드 전략을 쿼리합니다. 이 전략은 프로젝트 팩터리에서 복사 백업 또는 SxS 백업을 지원하는지 여부를 결정합니다. 이 정보는 업그레이드 **마법사로**전송되어 백업에 필요한 정보를 수집하고 사용자에게 적용 가능한 옵션을 제공합니다.

### <a name="multi-project-solutions"></a>다중 프로젝트 솔루션

솔루션에 여러 프로젝트가 포함되어 있고 SxS 백업만 지원하는 C++ 프로젝트와 복사 백업만 지원하는 웹 프로젝트와 같이 업그레이드 전략이 다른 경우 프로젝트 팩터는 업그레이드 전략을 협상해야 합니다.

솔루션은 각 프로젝트 팩터리에서 에 대해 쿼리합니다. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> 그런 다음 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly%2A> 전역 프로젝트 파일을 업그레이드해야 하는지 확인하고 지원되는 업그레이드 전략을 결정합니다. 그러면 **업그레이드 마법사가** 호출됩니다.

사용자가 마법사를 완료한 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> 후 각 프로젝트 팩터리에서 실제 업그레이드를 수행하도록 호출됩니다. 백업을 용이하게 하기 위해 IVsProjectUpgradeViaFactory 메서드는 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> 업그레이드 프로세스의 세부 정보를 기록하는 서비스를 제공합니다. 이 서비스는 캐시할 수 없습니다.

모든 관련 전역 파일을 업데이트한 후 각 프로젝트 팩터리는 프로젝트를 인스턴스화하도록 선택할 수 있습니다. 프로젝트 구현은 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>을 지원해야 합니다. 그런 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> 다음 메서드를 호출하여 모든 관련 프로젝트 항목을 업그레이드합니다.

> [!NOTE]
> 메서드는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> SVsUpgradeLogger 서비스를 제공하지 않습니다. 이 서비스는 호출하여 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>얻을 수 있습니다.

## <a name="best-practices"></a>모범 사례

<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> 서비스를 사용하여 파일을 편집하기 전에 편집할 수 있는지 확인하고 저장하기 전에 저장할 수 있습니다. 이렇게 하면 백업 및 업그레이드 구현에서 소스 제어하에 프로젝트 파일, 사용 권한이 부족한 파일 등을 처리하는 데 도움이 됩니다.

백업 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> 및 업그레이드의 모든 단계에서 서비스를 사용하여 업그레이드 프로세스의 성공 또는 실패에 대한 정보를 제공합니다.

프로젝트 백업 및 업그레이드에 대한 자세한 내용은 vsshell2.idl의 IVsProject업그레이드에 대한 주석을 참조하십시오.

## <a name="upgrading-custom-projects"></a><a name="upgrading-custom-projects"></a>사용자 지정 프로젝트 업그레이드

제품의 다른 Visual Studio 버전 간에 프로젝트 파일에 있는 정보를 변경하는 경우 이전 버전에서 새 버전으로의 프로젝트 파일 업그레이드를 지원해야 합니다. **Visual Studio 변환 마법사에**참여할 수 있는 업그레이드를 지원하려면 인터페이스를 구현합니다. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> 이 인터페이스에는 복사 업그레이드에 사용할 수 있는 메커니즘만 포함되어 있습니다. 프로젝트 업그레이드는 솔루션의 일부가 열릴 때 수행됩니다. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> 인터페이스는 프로젝트 팩터리에서 구현되거나 적어도 프로젝트 팩터리에서 얻을 수 있어야 합니다.

<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> 인터페이스를 사용하는 이전 메커니즘은 계속 지원되지만 프로젝트의 일부가 열릴 때 프로젝트 시스템을 개념적으로 업그레이드합니다. 따라서 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> 인터페이스를 호출하거나 구현하는 경우에도 Visual <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> Studio 환경에서 인터페이스를 호출합니다. 이 접근 방식을 사용하면 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>를 사용하여 업그레이드의 복사 및 프로젝트 전용 부분을 구현하고 나머지 작업은 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> 인터페이스에서 바로(아마도 새 위치에서) 수행하도록 위임할 수 있습니다.

의 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>샘플 구현은 [VSSDK 샘플을](https://github.com/Microsoft/VSSDK-Extensibility-Samples)참조하십시오.

프로젝트 업그레이드에서는 다음과 같은 시나리오가 발생합니다.

- 파일이 프로젝트에서 지원할 수 있는 형식보다 최신 형식인 경우 이를 설명하는 오류를 반환해야 합니다. 이전 버전의 제품에 버전을 확인하는 코드가 포함되어 있다고 가정합니다.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> 메서드에 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP> 플래그가 지정된 경우 업그레이드는 프로젝트를 열기 전에 현재 위치 업그레이드로 구현됩니다.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> 메서드에 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_COPYBACKUP> 플래그가 지정된 경우 업그레이드는 복사 업그레이드로 구현됩니다.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> 호출에 <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> 플래그가 지정된 경우 프로젝트가 열린 후 환경에서 사용자에게 프로젝트 파일을 현재 위치 업그레이드로 업그레이드하라는 메시지를 표시했습니다. 예를 들어 사용자가 이전 버전의 솔루션을 여는 경우 업그레이드하라는 메시지가 표시됩니다.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> 호출에 <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> 플래그가 지정되지 않은 경우에는 사용자에게 프로젝트 파일을 업그레이드하라는 메시지를 표시해야 합니다.

     다음은 업그레이드 프롬프트 메시지의 예입니다.

     "'%1' 프로젝트는 이전 버전의 Visual Studio에서 만들었습니다. 이 버전의 Visual Studio에서 이 프로젝트를 열면 이전 버전의 Visual Studio에서 이 프로젝트를 열 수 없습니다. 이 프로젝트를 계속 여시겠습니까?”

### <a name="to-implement-ivsprojectupgradeviafactory"></a>IVsProjectUpgradeViaFactory를 구현하려면

1. 프로젝트 팩터리 구현에서 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> 인터페이스의 메서드 특히, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> 메서드를 구현하거나 프로젝트 팩터리 구현에서 해당 구현을 호출할 수 있게 합니다.

2. 솔루션 열기의 일부로 현재 위치 업그레이드를 수행하려는 경우 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> 구현에서 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP> 플래그를 `VSPUVF_FLAGS` 매개 변수로 제공합니다.

3. 솔루션 열기의 일부로 현재 위치 업그레이드를 수행하려는 경우 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> 구현에서 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_COPYBACKUP> 플래그를 `VSPUVF_FLAGS` 매개 변수로 제공합니다.

4. 2단계와 3단계 모두의 경우 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>를 사용하는 실제 파일 업그레이드 단계는 아래의 “구현`IVsProjectUpgade`” 섹션에 설명된 대로 구현할 수도 있고 실제 파일 업그레이드를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>에 위임할 수도 있습니다.

5. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger>의 메서드를 사용하여 Visual Studio 마이그레이션 마법사를 사용하는 사용자에게 업그레이드 관련 메시지를 게시합니다.

6. <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileUpgrade> 인터페이스는 프로젝트 업그레이드의 일부로 수행해야 하는 모든 종류의 파일 업그레이드를 구현하는 데 사용됩니다. 이 인터페이스는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory>에서 호출되지는 않지만, 프로젝트 시스템의 일부이지만 기본 프로젝트 시스템에서 직접적으로 알지 못할 수도 있는 파일을 업그레이드하는 메커니즘을 제공됩니다. 예를 들어 나머지 프로젝트 시스템을 처리하는 개발 팀이 컴파일러 관련 파일 및 속성을 처리하지 않는 경우 이러한 상황이 발생할 수 있습니다.

### <a name="ivsprojectupgrade-implementation"></a>IVsProjectUpgrade 구현

프로젝트 시스템이 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> 구현하는 경우에만 Visual Studio 변환 **마법사에**참여할 수 없습니다. 그러나 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> 인터페이스를 구현하더라도 여전히 파일 업그레이드를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> 구현에 위임할 수는 있습니다.

#### <a name="to-implement-ivsprojectupgrade"></a>IVsProjectUpgrade를 구현하려면

1. 사용자가 프로젝트를 열면 프로젝트가 열린 후 프로젝트에 대한 다른 사용자 작업을 수행할 수 있기 전에 환경에서 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> 메서드가 호출됩니다. 사용자에게 솔루션을 업그레이드하라는 메시지가 이미 표시된 경우 <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> 플래그가 `grfUpgradeFlags` 매개 변수에 전달됩니다. 사용자가 기존 프로젝트 **추가** 명령을 사용하는 등 프로젝트를 직접 열면 <xref:Microsoft.VisualStudio.Shell.Interop.__VSUPGRADEPROJFLAGS.UPF_SILENTMIGRATE> 플래그가 전달되지 않으며 프로젝트에서 사용자에게 업그레이드하라는 메시지를 표시해야 합니다.

2. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> 호출에 응답하여 프로젝트에서는 프로젝트 파일이 업그레이드되었는지 평가해야 합니다. 프로젝트에서 프로젝트 형식을 새 버전으로 업그레이드할 필요가 없는 경우에는 간단히 <xref:Microsoft.VisualStudio.VSConstants.S_OK> 플래그를 반환할 수 있습니다.

3. 프로젝트에서 프로젝트 형식을 새 버전으로 업그레이드해야 하는 경우에는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> 메서드를 호출하고 <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags> 값을 `rgfQueryEdit` 매개 변수에 전달하여 프로젝트 파일을 수정할 수 있는지 여부를 확인해야 합니다. 그런 다음 프로젝트에서 다음을 수행해야 합니다.

    - `pfEditCanceled` 매개 변수에서 반환된 `VSQueryEditResult` 값이 <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditOK>인 경우 프로젝트 파일을 쓸 수 있으므로 업그레이드를 진행할 수 있습니다.

    - `pfEditCanceled` 매개 변수에서 반환된 `VSQueryEditResult` 값이 <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK>이고 `VSQueryEditResult` 값에 <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyNotUnderScc> 비트가 설정된 경우에는 사용자가 권한 문제를 직접 해결해야 하므로 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>에서 오류를 반환해야 합니다. 그런 다음 프로젝트에서 다음을 수행해야 합니다.

         호출하여 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> 사용자에게 오류를 보고하고 <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED> 오류 코드를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade>로 반환합니다.

    - `VSQueryEditResult` 값이 <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK>이고 `VSQueryEditResultFlags` 값에 <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc> 비트가 설정된 경우에서 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ForceEdit_NoPrompting>, <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_DisallowInMemoryEdits>,...)를 호출하여 프로젝트 파일을 체크 아웃해야 합니다.

4. 프로젝트 파일에 대한 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> 호출로 파일이 체크 아웃되고 최신 버전이 검색되는 경우에는 프로젝트가 언로드되었다가 다시 로드됩니다. 프로젝트의 다른 인스턴스가 생성되면 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> 메서드가 다시 호출됩니다. 이 두 번째 호출에서 프로젝트 파일을 디스크에 쓸 수 있습니다. 프로젝트에서 프로젝트 파일의 복사본을 .OLD 확장명을 사용하는 이전 형식으로 저장하고 필요한 업그레이드 변경을 수행한 다음 프로젝트 파일을 새 형식으로 저장하는 것이 좋습니다. 마찬가지로 업그레이드 프로세스의 일부가 실패하면 메서드에서는 <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED>를 반환하여 오류를 표시해야 합니다. 이로 인해 솔루션 탐색기에서 프로젝트가 언로드됩니다.

     <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> 메서드 호출(ReportOnly 값 지정)에서 <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK> 및 <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc> 플래그를 반환하는 경우에 대해 환경에서 수행되는 전체 프로세스를 이해해야 합니다.

5. 사용자가 프로젝트 파일을 열려고 합니다.

6. 환경에서 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> 구현을 호출합니다.

7. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A>가 `true`를 반환하는 경우 환경에서 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CanCreateProject%2A> 구현을 호출합니다.

8. 환경에서 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> 구현을 호출하여 파일을 열고 프로젝트 개체(예: Project1)를 초기화합니다.

9. 환경에서 `IVsProjectUpgrade::UpgradeProject` 구현을 호출하여 프로젝트 파일을 업그레이드해야 하는지 여부를 확인합니다.

10. <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>를 호출하고 <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ReportOnly> 값을 `rgfQueryEdit` 매개 변수에 전달합니다.

11. 환경에서 `VSQueryEditResult`에 대해 <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditNotOK>를 반환하고 `VSQueryEditResultFlags`에 <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResultFlags.QER_ReadOnlyUnderScc> 비트가 설정되 었습니다.

12. <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> 구현에서 `IVsQueryEditQuerySave::QueryEditFiles` (<xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ForceEdit_NoPrompting>, <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_DisallowInMemoryEdits>)를 호출합니다.

이 호출로 인해 프로젝트 파일의 새 복사본이 체크 아웃되고 최신 버전이 검색될 수 있으며 프로젝트 파일을 다시 로드해야 합니다. 이때 다음 두 가지 중 하나가 발생합니다.

- 프로젝트 다시 로드를 직접 처리하는 경우 환경에서 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> (VSITEMID_ROOT) 구현을 호출합니다. 이 호출을 받는 경우 프로젝트의 첫 번째 인스턴스(Project1)를 다시 로드하고 계속 프로젝트 파일을 업그레이드합니다. <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_HandlesOwnReload>)에 대해 `true`를 반환하는 경우 환경에서 사용자가 프로젝트 다시 로드를 직접 처리한다고 인식합니다.

- 프로젝트 다시 로드를 직접 처리하지 않는 경우에는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_HandlesOwnReload>)에 대해 `false`를 반환합니다. 이 경우(QEF_ForceEdit_NoPrompting, QEF_DisallowInMemoryEdits) 반환하기 전에 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>환경은 다음과 같이 Project2와 같은 프로젝트의 또 다른 새 인스턴스를 만듭니다.

    1. 환경에서 첫 번째 프로젝트 개체 Project1에 대해 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.Close%2A>를; 호출하여 이 개체를 비활성 상태로 둡니다.

    2. 환경에서 `IVsProjectFactory::CreateProject` 구현하여 프로젝트의 두 번째 인스턴스 Project2를 만듭니다.

    3. 환경에서 `IPersistFileFormat::Load` 구현을 호출하여 파일을 열고 두 번째 프로젝트 개체 Project2를 초기화합니다.

    4. 환경에서 `IVsProjectUpgrade::UpgradeProject` 를 두 번째로 호출하여 프로젝트 개체를 업그레이드해야 하는지 여부를 결정합니다. 그러나 이 호출은 프로젝트의 새로운 두 번째 인스턴스 Project2에 대해 수행됩니다. 이 프로젝트가 솔루션에 열려 있는 프로젝트입니다.

        > [!NOTE]
        > 첫 번째 프로젝트 Project1이 비활성 상태로 있는 인스턴스에서는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A> 구현에 대한 첫 번째 호출에서 <xref:Microsoft.VisualStudio.VSConstants.S_OK>를 반환해야 합니다.

    5. <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>를 호출하고 <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditFlags.QEF_ReportOnly> 값을 `rgfQueryEdit` 매개 변수에 전달합니다.

    6. 환경에서 <xref:Microsoft.VisualStudio.Shell.Interop.tagVSQueryEditResult.QER_EditOK>를 반환하고 프로젝트 파일을 쓸 수 있으므로 업그레이드를 진행할 수 있습니다.

업그레이드하지 않으면 `IVsProjectUpgrade::UpgradeProject`에서 <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED>를 반환합니다. 업그레이드가 필요하지 않거나 업그레이드하지 않으려면 `IVsProjectUpgrade::UpgradeProject` 호출을 no-op으로 처리합니다. <xref:Microsoft.VisualStudio.Shell.Interop.VSErrorCodes.VS_E_PROJECTMIGRATIONFAILED>를 반환하는 경우 프로젝트에 대한 자리 표시자 노드가 솔루션에 추가됩니다.

## <a name="upgrading-project-items"></a>프로젝트 항목 업그레이드

구현하지 않은 프로젝트 시스템 내에 항목을 추가하거나 관리하는 경우 프로젝트 업그레이드 프로세스에 참여해야 할 수 있습니다. 크리스탈 보고서는 프로젝트 시스템에 추가할 수 있는 항목의 예입니다.

일반적으로 프로젝트 항목 구현자는 프로젝트 참조가 무엇이며 업그레이드 결정을 내리기 위해 어떤 다른 프로젝트 속성이 있는지 알아야 하기 때문에 이미 완전히 인스턴스화되고 업그레이드된 프로젝트를 활용하려고 합니다.

### <a name="to-get-the-project-upgrade-notification"></a>프로젝트 업그레이드 알림을 받으려면

1. 프로젝트 <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80.SolutionOrProjectUpgrading> 항목 구현에서 플래그(vsshell80.idl에 정의)를 설정합니다. 이렇게 하면 프로젝트 항목 VSPackage Visual Studio 셸에서 프로젝트 시스템을 업그레이드 하는 과정에 있는지 확인 하면 자동으로 로드 됩니다.

2. 방법을 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> 통해 인터페이스에 대해 조언합니다. <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution2.AdviseSolutionEvents%2A>

3. 인터페이스는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> 프로젝트 시스템 구현이 업그레이드 작업을 완료하고 업그레이드된 새 프로젝트가 생성된 후에 발생합니다. 시나리오에 따라 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEventsProjectUpgrade> 인터페이스는 . <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A>

### <a name="to-upgrade-the-project-item-files"></a>프로젝트 항목 파일을 업그레이드하려면

1. 프로젝트 항목 구현에서 파일 백업 프로세스를 신중하게 관리해야 합니다. 이는 특히 `fUpgradeFlag` <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> 메서드의 매개 변수가 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPPROJECTUPGRADEVIAFACTORYFLAGS.PUVFF_SXSBACKUP>설정된 나란히 백업에 적용되며 백업된 파일은 ".old"로 지정된 측면 파일을 따라 배치됩니다. 프로젝트를 업그레이드한 시스템 시간보다 오래된 백업된 파일은 오래된 파일로 지정할 수 있습니다. 또한 이를 방지하기 위한 구체적인 단계를 취하지 않는 한 덮어쓸 수 있습니다.

2. 프로젝트 항목에서 프로젝트 업그레이드 알림을 받으면 Visual **Studio 변환 마법사가** 계속 표시됩니다. 따라서 인터페이스의 메서드를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUpgradeLogger> 사용 하 여 마법사 UI에 업그레이드 메시지를 제공 해야 합니다.

## <a name="see-also"></a>참조

- [프로젝트](../../extensibility/internals/projects.md)
