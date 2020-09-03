---
title: 등록 및 선택 (소스 제어 VSPackage) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- registration, source control packages
- source control packages, registration
ms.assetid: 7d21fe48-489a-4f55-acb5-73da64c4e155
caps.latest.revision: 35
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 692f2a9f34edd41839179f7229e079ec8e791800
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185829"
---
# <a name="registration-and-selection-source-control-vspackage"></a>등록 및 선택(소스 제어 VSPackage)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

소스 제어 VSPackage를에 노출 하려면 등록 해야 합니다 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . 둘 이상의 소스 제어 VSPackage가 등록 된 경우 사용자는 적절 한 시간에 로드할 VSPackage를 선택할 수 있습니다. Vspackage에 대 한 자세한 내용 및 등록 방법에 대 한 자세한 내용은 [vspackage](../../extensibility/internals/vspackages.md) 를 참조 하세요.  
  
## <a name="registering-a-source-control-package"></a>소스 제어 패키지 등록  
 원본 제어 패키지는 환경에서 해당 패키지를 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 찾고 지원 되는 기능을 쿼리할 수 있도록 등록 됩니다. 이는 해당 기능 또는 명령이 필요 하거나 명시적으로 요청 된 경우에만 패키지의 인스턴스가 생성 되는 지연 로드 체계에 따라 결정 됩니다.  
  
 Vspackage 레지스트리 키 HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio x. Y에 정보를 저장 합니다 \\ *.* 여기서 *x* 는 주 버전 번호이 고 *Y* 는 부 버전 번호입니다. 이 연습에서는 여러 버전의를 함께 설치할 수 있는 기능을 제공 합니다 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
 UI (사용자 인터페이스)는 소스 제어 Vspackage 뿐만 아니라 원본 제어 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 어댑터 패키지를 통해 설치 된 여러 소스 제어 플러그 인에서의 선택을 지원 합니다. 한 번에 하나의 활성 소스 제어 플러그 인 또는 VSPackage 있을 수 있습니다. 그러나 아래에 설명 된 것 처럼 IDE는 자동 솔루션 기반 패키지 교환 메커니즘을 통해 소스 제어 플러그 인과 Vspackage 간을 전환할 수 있습니다. 이 선택 메커니즘을 사용 하도록 설정 하려면 소스 제어 VSPackage 일부에 몇 가지 요구 사항이 있습니다.  
  
### <a name="registry-entries"></a>레지스트리 항목  
 소스 제어 패키지에는 세 가지 개인 Guid가 필요 합니다.  
  
- Package GUID: 소스 제어 구현 (이 섹션의 ID_Package 이라고 함)을 포함 하는 패키지의 기본 GUID입니다.  
  
- 소스 제어 GUID: Visual Studio 소스 제어 스텁에 등록 하는 데 사용 되는 소스 제어 VSPackage의 GUID 이며 명령 UI 컨텍스트 GUID로도 사용 됩니다. 소스 제어 서비스 GUID는 소스 제어 GUID에 등록 됩니다. 이 예제에서는 소스 제어 GUID를 ID_SccProvider 라고 합니다.  
  
- 소스 제어 서비스 GUID: Visual Studio에서 사용 하는 개인 서비스 GUID입니다 (이 섹션의 SID_SccPkgService 이라고 함). 이 외에도 소스 제어 패키지는 Vspackage, 도구 창 등에 대해 다른 Guid를 정의 해야 합니다.  
  
  다음 레지스트리 항목은 소스 제어 VSPackage에서 이루어져야 합니다.  
  
|키 이름|항목만|  
|--------------|-------------|  
|`HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\`|(기본값) = rg_sz: {ID_SccProvider}|  
|`HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\`|(기본값) = rg_sz:\<Friendly name of Package><br /><br /> Service = rg_sz: {SID_SccPkgService}|  
|`HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\               Name\`|(기본값) = rg_sz: #\<Resource ID for localized name><br /><br /> Package = rg_sz: {ID_Package}|  
|`HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SolutionPersistence\             <PackageName>\`<br /><br /> 키 이름은 `SourceCodeControl` 이미에서 사용 되며 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 에 대 한 선택으로 사용할 수 없습니다 \<PackageName> .|(기본값) = rg_sz: {ID_Package}|  
  
## <a name="selecting-a-source-control-package"></a>소스 제어 패키지 선택  
 여러 소스 제어 플러그 인 API 기반 플러그 인 및 소스 제어 Vspackage 동시에 등록 될 수 있습니다. 원본 제어 플러그 인 또는 VSPackage를 선택 하는 프로세스는에서 플러그 인 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 또는 VSPackage를 적절 한 시간에 로드 하 고, 필요할 때까지 불필요 한 구성 요소 로드를 연기할 수 있도록 해야 합니다. 또한는 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 메뉴 항목, 대화 상자, 도구 모음 등의 비활성 vspackage에서 모든 ui를 제거 하 고 활성 VSPACKAGE ui를 표시 해야 합니다.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 다음 작업 중 하나가 수행 되 면 소스 제어 VSPackage를 로드 합니다.  
  
- 솔루션이 열립니다 (솔루션을 소스 제어에서 사용할 때).  
  
   소스 제어에서 솔루션 또는 프로젝트를 열면 IDE는 해당 솔루션에 대해 지정 된 소스 제어 VSPackage를 로드 합니다.  
  
- 소스 제어 VSPackage의 모든 메뉴 명령이 실행 됩니다.  
  
  소스 제어 VSPackage은 실제로 사용 될 때만 필요한 구성 요소를 로드 해야 합니다 (지연 된 로드 라고도 함).  
  
### <a name="automatic-solution-based-vspackage-swapping"></a>자동 솔루션 기반 VSPackage 스와핑  
 원본 제어 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 범주 아래의 **옵션** 대화 상자를 통해 소스 제어 vspackage를 수동으로 **Source Control** 바꿀 수 있습니다. 자동 솔루션 기반 패키지 스와핑은 해당 솔루션이 열릴 때 특정 솔루션에 대해 지정 된 소스 제어 패키지가 자동으로 활성으로 설정 됨을 의미 합니다. 모든 소스 제어 패키지는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A> 및를 구현 해야 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A> 합니다. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 소스 제어 플러그 인 (소스 제어 플러그 인 API 구현) 및 소스 제어 Vspackage 간의 전환을 처리 합니다.  
  
 원본 제어 어댑터 패키지는 소스 제어 플러그 인 API 기반 플러그 인으로 전환 하는 데 사용 됩니다. 중간 소스 제어 어댑터 패키지로 전환 하 고 활성 또는 비활성으로 설정 해야 하는 원본 제어 플러그 인을 결정 하는 프로세스는 사용자에 게 투명 합니다. 원본 제어 플러그 인이 활성 상태인 경우 어댑터 패키지는 항상 활성 상태입니다. 두 소스 제어 플러그 인을 전환 하 여 플러그 인 DLL을 로드 하 고 언로드할 수 있습니다. 그러나 소스 제어 VSPackage로 전환 하는 경우에는 IDE와 상호 작용 하 여 적절 한 VSPackage를 로드 해야 합니다.  
  
 소스 제어 VSPackage는 솔루션이 열리고 VSPackage에 대 한 레지스트리 키가 솔루션 파일에 있을 때 호출 됩니다. 솔루션이 열리면에서 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 레지스트리 값을 찾아 적절 한 소스 제어 VSPackage를 로드 합니다. 모든 소스 제어 Vspackage 위에 설명 된 레지스트리 항목을 포함 해야 합니다. 소스 제어에서 사용 중인 솔루션이 특정 소스 제어 VSPackage 연결 되는 것으로 표시 되어 있습니다. <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>자동 솔루션 기반 VSPackage 스와핑을 사용 하려면 소스 제어 vspackage에서를 구현 해야 합니다.  
  
### <a name="visual-studio-ui-for-package-selection-and-switching"></a>패키지 선택 및 전환에 대 한 Visual Studio UI  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]소스 **제어** 범주 아래에 있는 **옵션** 대화 상자에서 소스 제어 VSPackage 및 플러그 인 선택에 대 한 UI를 제공 합니다. 이를 통해 사용자는 활성 소스 제어 플러그 인 또는 VSPackage를 선택할 수 있습니다. 드롭다운 목록에는 다음이 포함 됩니다.  
  
- 설치 된 모든 원본 제어 패키지  
  
- 설치 된 모든 원본 제어 플러그 인  
  
- 소스 코드 제어를 사용 하지 않도록 설정 하는 "none" 옵션  
  
  활성 소스 컨트롤 선택 항목에 대 한 UI만 표시 됩니다. VSPackage 선택은 이전 VSPackage에 대 한 UI를 숨기고 새 ui에 대 한 UI를 표시 합니다. Active VSPackage는 사용자 단위로 선택 됩니다. 사용자에 게 여러 복사본이 동시에 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 열려 있는 경우 각각 다른 활성 VSPackage를 사용할 수 있습니다. 여러 사용자가 동일한 컴퓨터에 로그온 한 경우 각 사용자는 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 서로 다른 활성 VSPackage를 사용 하 여 별도의 열린 인스턴스를 사용할 수 있습니다. 사용자가의 여러 인스턴스를 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 닫으면 마지막으로 열린 솔루션에 대해 활성화 된 소스 제어 VSPackage가 다시 시작 시 활성 상태로 설정 되는 기본 소스 제어 VSPackage가 됩니다.  
  
  이전 버전의와 달리 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE 다시 시작은 더 이상 소스 제어 vspackage를 전환 하는 유일한 방법입니다. VSPackage 선택이 자동으로 선택 됩니다. 패키지를 전환 하려면 관리자 또는 고급 사용자가 아닌 Windows 사용자 권한이 필요 합니다.  
  
## <a name="see-also"></a>관련 항목  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>   
 [요소](../../extensibility/internals/source-control-vspackage-features.md)   
 [소스 제어 플러그 인 만들기](../../extensibility/internals/creating-a-source-control-plug-in.md)   
 [VSPackages](../../extensibility/internals/vspackages.md)
