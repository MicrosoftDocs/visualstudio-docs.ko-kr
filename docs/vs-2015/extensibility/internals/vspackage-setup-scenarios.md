---
title: VSPackage 설치 시나리오 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, deployment considerations
ms.assetid: d2928498-f27c-46b4-a9cd-cba41fd85a10
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a09b794a6cd81966df45a1b30182040d7ab9335e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65696752"
---
# <a name="vspackage-setup-scenarios"></a>VSPackage 설치 시나리오
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

유연성을 위해 VSPackage installer를 설계 하는 것이 중요 합니다. 예를 들어 나중에 보안 패치를 릴리스 하거나 철저 한 병렬 버전 관리를 지 원하는 비즈니스 전략을 변경 해야 할 수 있습니다.  
  
 [여러 버전의 Visual Studio를 지 원하는](../../extensibility/supporting-multiple-versions-of-visual-studio.md)경우 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] VSPackage의 공유 또는 side-by-side 설치를 사용 하 여의 병렬 설치 지원에 대 한 장점과 문제에 대해 알아볼 수 있습니다. 간단히 말해서,의 새 기능을 지원 하기 위한 유연성을 제공 하는 동시 Vspackage [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
 이 항목에서 설명 하는 시나리오는 유일 하 게 선택할 수 있는 것은 아니지만 제안 된 최선의 구현 방법으로 제공 됩니다.  
  
## <a name="components-privacy-and-sharing"></a>구성 요소, 개인 정보 보호 및 공유  
  
##### <a name="make-your-components-independent"></a>구성 요소를 독립적으로 만들기  
 구성 요소를 식별 하 고 채우고,을 할당 하 `GUID` 고, 구성 요소를 배포한 후에는 해당 구성을 변경할 수 없습니다. 구성 요소의 컴퍼지션을 변경 하는 경우 생성 되는 구성 요소는 새로운 새 구성 요소 여야 합니다 `GUID` . 이러한 사실을 감안 하 여 각 구성 요소 독립적인 자체 기반 단위를 만들면 가장 큰 버전의 유연성이 제공 됩니다. 구성 요소를 관리 하는 규칙에 대 한 자세한 내용은 구성 요소 [코드 변경](https://msdn.microsoft.com/library/aa367849\(VS.85\).aspx) 및 [구성 요소 규칙이 중단 되 면 어떻게 되나요?](https://msdn.microsoft.com/library/aa372795\(VS.85\).aspx)를 참조 하세요.  
  
##### <a name="do-not-mix-shared-and-private-resources-in-a-component"></a>구성 요소에서 공유 및 개인 리소스를 혼합 하지 마세요.  
 참조 횟수는 구성 요소 수준에서 발생 합니다. 따라서 한 구성 요소에서 공유 리소스와 개인 리소스를 혼합 하면 공유 리소스를 덮어쓰지 않고도 실행 파일 등의 개인 리소스를 업데이트할 수 없습니다. 이 시나리오는 이전 버전과의 호환성 문제를 생성 하 고 side-by-side 기능을 만들 수 없도록 제한 합니다.  
  
 예를 들어 VSPackage을에 등록 하는 데 사용 되는 레지스트리 값은 VSPackage를에 [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] 등록 하는 데 사용 되는 것과는 다른 구성 요소에 보관 되어야 합니다 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . 공유 파일 또는 레지스트리 값이 다른 구성 요소로 이동 합니다.  
  
## <a name="scenario-1-shared-vspackage"></a>시나리오 1: Shared VSPackage  
 이 시나리오에서는 공유 VSPackage (여러 버전의를 지 원하는 단일 이진 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] )이 Windows Installer 패키지에 제공 됩니다. 각 버전의에 등록 하 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 는 것은 사용자가 선택할 수 있는 기능을 통해 제어 됩니다. 또한 개별 기능에 할당 된 경우 각 구성 요소를 설치 또는 제거에 대해 개별적으로 선택 하 여 사용자가 VSPackage를 여러 버전의에 통합 하는 것을 제어할 수 있습니다 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Windows Installer 패키지의 기능 사용에 대 한 자세한 내용은 [Windows Installer 기능](https://msdn.microsoft.com/library/aa372840\(VS.85\).aspx) 을 참조 하세요.  
  
 ![VS 공유 VSPackage 그래픽](../../extensibility/internals/media/vs-sharedpackage.gif "VS_SharedPackage")  
공유 VSPackage 설치 관리자  
  
 그림에 표시 된 것 처럼 공유 구성 요소는 항상 설치 되는 Feat_Common 기능의 일부로 구성 됩니다. Feat_VS2002 및 Feat_VS2003 기능을 표시 함으로써 사용자는 설치 시 VSPackage 통합 하려는 버전을 선택할 수 있습니다 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . 또한 사용자는 Windows Installer 유지 관리 모드를 사용 하 여 기능을 추가 하거나 제거할 수 있습니다 .이 경우 다른 버전의에서 VSPackage 등록 정보를 추가 하거나 제거 합니다 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
> [!NOTE]
> 기능의 표시 열을 0으로 설정 하면 해당 열이 숨겨집니다. 낮은 수준의 열 값 (예: 1)은 항상 설치 되도록 합니다. 자세한 내용은 [Installlevel 속성](https://msdn.microsoft.com/library/aa369536\(VS.85\).aspx) 및 [기능 표](https://msdn.microsoft.com/library/aa368585.aspx)를 참조 하세요.  
  
## <a name="scenario-2-shared-vspackage-update"></a>시나리오 2: Shared VSPackage Update  
 이 시나리오에서 시나리오 1에서 업데이트 된 버전의 VSPackage 설치 관리자가 제공 됩니다. 논의를 위해 업데이트는에 대 한 지원을 추가 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 하지만 보다 간단한 보안 패치 또는 버그 수정 Service Pack 수도 있습니다. 최신 구성 요소를 설치 하는 Windows Installer 규칙에는 시스템에 있는 변경 되지 않은 구성 요소가 아직 다시 복사 되지 않아야 합니다. 이 경우 버전 1.0이 이미 있는 시스템은 업데이트 된 구성 요소 Comp_MyVSPackage.dll 덮어쓰고 사용자가 구성 요소 Comp_VS2005_Reg Feat_VS2005 새 기능을 추가 하도록 선택할 수 있습니다.  
  
> [!CAUTION]
> VSPackage가 여러 버전의에서 공유 될 때마다 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 이후 VSPackage 릴리스가 이전 버전의와의 호환성을 유지 하는 것이 중요 합니다 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . 이전 버전과의 호환성을 유지할 수 없는 경우 side-by-side, private Vspackage를 사용 해야 합니다. 자세한 내용은 [여러 버전의 Visual Studio 지원](../../extensibility/supporting-multiple-versions-of-visual-studio.md)을 참조 하세요.  
  
 ![VS 공유 VS 패키지 업데이트 이미지](../../extensibility/internals/media/vs-sharedpackageupdate.gif "VS_SharedPackageUpdate")  
공유 VSPackage 업데이트 설치 관리자  
  
 이 시나리오에서는 Windows Installer의 사소한 업그레이드 지원 기능을 활용 하 여 새로운 VSPackage 설치 관리자를 제공 합니다. 사용자는 버전 1.1만 설치 하 고 버전 1.0을 업그레이드 합니다. 그러나 시스템에 버전 1.0이 있을 필요는 없습니다. 동일한 설치 관리자가 버전 1.0이 없는 시스템에 버전 1.1을 설치 합니다. 이러한 방식으로 사소한 업그레이드를 제공 하는 장점은 업그레이드 설치 관리자와 전체 제품 설치 관리자를 개발 하는 작업을 수행할 필요가 없다는 것입니다. 한 설치 관리자가 두 작업을 모두 수행 합니다. 보안 픽스 또는 Service Pack는 Windows Installer 패치를 대신 사용할 수 있습니다. 자세한 내용은 [패치 및 업그레이드](https://msdn.microsoft.com/library/aa370579\(VS.85\).aspx)를 참조 하세요.  
  
## <a name="scenario-3-side-by-side-vspackage"></a>시나리오 3: Side-by-side VSPackage  
 이 시나리오에서는 Visual Studio .NET 2003 및의 각 버전에 대해 하나씩 두 개의 VSPackage 설치 관리자를 제공 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 합니다. 각 설치 관리자는 side-by-side 또는 개인 VSPackage (특정 버전의 특정 버전에 대해 특별히 빌드되고 설치 된)를 설치 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 합니다. 각 VSPackage는 자체 구성 요소에 있습니다. 따라서 각각은 패치 또는 유지 관리 릴리스와 개별적으로 서비스를 제공할 수 있습니다. VSPackage DLL은 버전에 따라 다르므로 DLL과 같은 구성 요소에 등록 정보를 포함 하는 것이 안전 합니다.  
  
 ![&#45;쪽 VS 패키지 그래픽을 사용한 VS Side&#45;](../../extensibility/internals/media/vs-sbys-package.gif "VS_SbyS_Package")  
Side-by-side VSPackage 설치 관리자  
  
 또한 각 설치 관리자에는 두 설치 관리자 간에 공유 되는 코드가 포함 됩니다. 공유 코드가 공통 위치에 설치 된 경우 .msi 파일을 모두 설치 하면 공유 코드도 한 번만 설치 됩니다. 두 번째 설치 관리자는 구성 요소에 대 한 참조 횟수를 증가 시킵니다. 참조 횟수를 사용 하면 Vspackage 중 하나가 제거 되 면 공유 코드는 다른 VSPackage에 대해 유지 됩니다. 두 번째 VSPackage 제거 되 면 공유 코드가 제거 됩니다.  
  
## <a name="scenario-4-side-by-side-vspackage-update"></a>시나리오 4: Side-by-side VSPackage 업데이트  
 이 시나리오에서 VSPackage은 [!INCLUDE[vsprvslong](../../includes/vsprvslong-md.md)] 보안 취약점에서 받은 후 업데이트를 실행 해야 합니다. 시나리오 2에서와 같이 기존 설치를 업데이트 하는 새 .msi 파일을 만들어 보안 픽스를 포함 하 고 새 설치를 이미 준비 된 상태로 배포할 수 있습니다.  
  
 이 경우 VSPackage는 GAC (전역 어셈블리 캐시)에 설치 된 관리 되는 VSPackage입니다. 보안 픽스를 포함 하도록 다시 작성 하는 경우 어셈블리 버전 번호의 수정 번호 부분을 변경 해야 합니다. 새 어셈블리 버전 번호에 대 한 등록 정보는 이전 버전을 덮어쓰므로 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 고정 어셈블리를 로드 합니다.  
  
 ![&#45;쪽 VS 패키지 업데이트 그래픽을 사용한 VS Side&#45;](../../extensibility/internals/media/vs-sbys-packageupdate.gif "VS_SbyS_PackageUpdate")  
Side-by-side VSPackage 업데이트 설치 관리자  
  
 **참고** Side-by-side 어셈블리 배포에 대 한 자세한 내용은 [.NET Framework를 사용 하 여 배포 간소화 및 DLL 추가 해결](https://msdn.microsoft.com/library/ms973843.aspx)을 참조 하세요.  
  
## <a name="see-also"></a>관련 항목  
 [Windows Installer](https://msdn.microsoft.com/library/cc185688\(VS.85\).aspx)   
 [여러 버전의 Visual Studio 지원](../../extensibility/supporting-multiple-versions-of-visual-studio.md)
