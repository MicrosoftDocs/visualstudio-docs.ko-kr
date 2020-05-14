---
title: 등록 및 선택(소스 제어 VS패키지) | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, source control packages
- source control packages, registration
ms.assetid: 7d21fe48-489a-4f55-acb5-73da64c4e155
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 973eb19916a737dfa775fe79ee62cb3d11fe0123
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705715"
---
# <a name="registration-and-selection-source-control-vspackage"></a>등록 및 선택(소스 제어 VSPackage)
소스 제어 VS패키지에 노출하려면 등록해야 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]합니다. 두 개 이상의 소스 제어 VSPackage가 등록된 경우 사용자는 적절한 시간에 로드할 VSPackage를 선택할 수 있습니다. [VSPackage에](../../extensibility/internals/vspackages.md) 대한 자세한 내용과 등록 방법은 VSPackage를 참조하십시오.

## <a name="registering-a-source-control-package"></a>소스 제어 패키지 등록
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 환경이 소스 제어 패키지를 찾아 지원되는 기능을 쿼리할 수 있도록 소스 제어 패키지가 등록됩니다. 이는 패키지의 인스턴스가 기능 이나 명령이 필요하거나 명시적으로 요청된 경우에만 생성되는 지연 로드 체계에 따라 결정됩니다.

 VSPackages는 버전별 레지스트리 키에 정보를\\배치합니다(HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio*X.Y,* 여기서 *X는* 주 버전 번호이고 *Y는* 부버전 번호입니다. 이 연습에서는 여러 버전의 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]여러 버전을 나란히 설치할 수 있는 기능을 제공합니다.

 사용자 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 인터페이스(UI)는 소스 제어 어댑터 패키지를 통해 설치된 여러 소스 제어 플러그인과 소스 제어 VSPackage 중에서 선택을 지원합니다. 한 번에 하나의 활성 소스 제어 플러그인 또는 VSPackage만 있을 수 있습니다. 그러나 아래에 설명된 대로 IDE를 사용하면 자동 솔루션 기반 패키지 교환 메커니즘을 통해 소스 제어 플러그인과 VSPackage 간에 전환할 수 있습니다. 이 선택 메커니즘을 사용 하려면 소스 제어 VSPackage 부분에 몇 가지 요구 사항이 있습니다.

### <a name="registry-entries"></a>레지스트리 항목
 소스 제어 패키지에는 세 개의 개인 GUID가 필요합니다.

- 패키지 GUID: 이 가이드는 소스 제어 구현(이 섹션의 ID_Package)을 포함하는 패키지의 기본 GUID입니다.

- 소스 제어 GUID: 이 GUID는 Visual Studio 소스 제어 스텁에 등록하는 데 사용되는 소스 제어 VSPackage에 대한 GUID이며 명령 UI 컨텍스트 GUID로도 사용됩니다. 소스 제어 서비스 GUID는 소스 제어 GUID에 따라 등록됩니다. 예제에서 소스 제어 GUID를 ID_SccProvider 라고 합니다.

- 소스 제어 서비스 GUID: Visual Studio에서 사용하는 개인 서비스 GUID입니다(이 섹션의 SID_SccPkgService). 이 외에도 소스 제어 패키지는 VSPackage, 도구 창 등에 대한 다른 GUID를 정의해야 합니다.

  다음 레지스트리 항목은 소스 제어 VSPackage에서 수행해야 합니다.

| 키 이름 | 항목 |
| - | - |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\` | (기본값) = rg_sz:{ID_SccProvider} |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\` | (기본값) =\<rg_sz: 패키지> 이름<br /><br /> 서비스 = rg_sz:{SID_SccPkgService} |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SourceControlProviders\             {ID_SccProvider}\               Name\` | (기본값) =\<지역화된 이름> 대한 rg_sz:# 리소스 ID<br /><br /> 패키지 = rg_sz:{ID_Package} |
| `HKEY_LOCAL_MACHINE\   SOFTWARE\     Microsoft\       VisualStudio\         X.Y\           SolutionPersistence\             <PackageName>\`<br /><br /> (의 키 이름은 `SourceCodeControl`이미 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 사용중이며 PackageName> 선택사항으로 \<사용할 수 없습니다.) | (기본값) = rg_sz:{ID_Package} |

## <a name="selecting-a-source-control-package"></a>소스 제어 패키지 선택
 여러 소스 제어 API 기반 플러그인 및 소스 제어 VSPackage가 동시에 등록될 수 있습니다. 소스 제어 플러그인 또는 VSPackage를 선택하는 프로세스는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 적절한 시간에 플러그인 또는 VSPackage를 로드해야 하며 필요한 때까지 불필요한 구성 요소를 로드하는 것을 연기할 수 있습니다. 또한 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 메뉴 항목, 대화 상자 및 도구 모음을 비롯한 다른 비활성 VSPackage에서 모든 UI를 제거하고 활성 VSPackage에 대한 UI를 표시해야 합니다.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]다음 작업 중 하나가 수행될 때 소스 제어 VSPackage를 로드합니다.

- 솔루션이 열리면(솔루션이 소스 제어하에 있을 때).

   소스 제어 하에 있는 솔루션 또는 프로젝트가 열리면 IDE는 해당 솔루션에 대해 지정된 소스 제어 VSPackage를 로드합니다.

- 소스 제어 VSPackage의 메뉴 명령이 실행됩니다.

  소스 제어 VSPackage는 실제로 사용될 때만 필요한 모든 구성 요소를 로드해야 합니다(지연 된 로드라고도 함).

### <a name="automatic-solution-based-vspackage-swapping"></a>자동 솔루션 기반 VS패키지 스와핑
 소스 제어 범주 아래의 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **옵션** 대화 상자를 통해 소스 제어 VSPackage를 수동으로 **교환할** 수 있습니다. 자동 솔루션 기반 패키지 교환은 특정 솔루션에 대해 지정된 소스 제어 패키지가 해당 솔루션을 열 때 자동으로 활성으로 설정된다는 것을 의미합니다. 모든 소스 제어 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A> 패키지는 구현해야 하며 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A>. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]는 소스 제어 플러그인(소스 제어 플러그인 API 구현) 및 소스 제어 VSPackage 간의 스위치를 처리합니다.

 소스 제어 어댑터 패키지는 소스 제어 플러그인 API 기반 플러그인으로 전환하는 데 사용됩니다. 중간 소스 제어 어댑터 패키지로 전환하고 활성 또는 비활성으로 설정해야 하는 소스 제어 플러그인을 결정하는 프로세스는 사용자에게 투명합니다. 어댑터 패키지는 소스 제어 플러그인이 활성화되어 있을 때 항상 활성화됩니다. 두 소스 제어 플러그인 사이를 전환하면 플러그 인 DLL을 로드하고 언로드하기만 하면 됩니다. 그러나 소스 제어 VSPackage로 전환하려면 IDE와 상호 작용하여 적절한 VSPackage를 로드해야 합니다.

 소스 제어 VSPackage는 모든 솔루션이 열리고 VSPackage의 레지스트리 키가 솔루션 파일에 있을 때 호출됩니다. 솔루션이 열리면 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 레지스트리 값을 찾아 적절한 소스 제어 VSPackage를 로드합니다. 모든 소스 제어 VSPackage에는 위에서 설명한 레지스트리 항목이 있어야 합니다. 소스 제어하에 있는 솔루션은 특정 소스 제어 VSPackage와 연결된 것으로 표시됩니다. 소스 제어 VSPackage자동 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> 솔루션 기반 VSPackage 스와핑을 사용하도록 구현해야 합니다.

### <a name="visual-studio-ui-for-package-selection-and-switching"></a>패키지 선택 및 전환을 위한 비주얼 스튜디오 UI
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]소스 제어 **범주** 아래의 **옵션** 대화 상자에서 소스 제어 VSPackage 및 플러그인 선택을 위한 UI를 제공합니다. 그것은 사용자가 활성 소스 제어 플러그인 또는 VSPackage를 선택할 수 있습니다. 드롭다운 목록에는 다음이 포함됩니다.

- 설치된 모든 소스 제어 패키지

- 설치된 모든 소스 제어 플러그인

- 소스 코드 제어를 사용하지 않도록 설정하는 "none" 옵션

  활성 소스 제어 선택에 대한 UI만 표시됩니다. VSPackage 선택은 이전 VSPackage의 UI를 숨기고 새 패키지의 UI를 표시합니다. 활성 VSPackage는 사용자별로 선택됩니다. 사용자가 동시에 열려 있는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 복사본이 여러 개인 경우 각 복사본은 잠재적으로 다른 활성 VSPackage를 사용할 수 있습니다. 여러 사용자가 동일한 컴퓨터에 로그온한 경우 각 사용자는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 각각 다른 활성 VSPackage를 사용하여 열려 있는 별도의 인스턴스를 가질 수 있습니다. 사용자가 여러 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 인스턴스를 닫으면 마지막 열린 솔루션에 대해 활성 상태였던 소스 제어 VSPackage가 기본 소스 제어 VSPackage가 되어 다시 시작할 때 활성으로 설정됩니다.

  이전 버전과 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]달리 IDE 다시 시작은 더 이상 소스 제어 VSPackage를 전환하는 유일한 방법이 아닙니다. VS패키지 선택은 자동입니다. 패키지를 전환하려면 관리자 또는 Power User가 아닌 Windows 사용자 권한이 필요합니다.

## <a name="see-also"></a>참조
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>
- [기능](../../extensibility/internals/source-control-vspackage-features.md)
- [소스 제어 플러그 인 만들기](../../extensibility/internals/creating-a-source-control-plug-in.md)
- [VSPackage](../../extensibility/internals/vspackages.md)
