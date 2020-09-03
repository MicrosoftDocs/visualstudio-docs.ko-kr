---
title: VSPackage 설치 시나리오 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, deployment considerations
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 01279666642adb729d4350b8a497c42d78159120
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80703980"
---
# <a name="vspackage-setup-scenarios"></a>VSPackage 설치 시나리오

유연성을 위해 VSPackage installer를 설계 하는 것이 중요 합니다. 예를 들어 나중에 보안 패치를 릴리스 하거나 철저 한 병렬 버전 관리를 지 원하는 비즈니스 전략을 변경 해야 할 수 있습니다.

[여러 버전의 Visual Studio를 지 원하는](../../extensibility/supporting-multiple-versions-of-visual-studio.md)경우 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] VSPackage의 공유 또는 side-by-side 설치를 사용 하 여의 병렬 설치 지원에 대 한 장점과 문제에 대해 알아볼 수 있습니다. 간단히 말해서,의 새 기능을 지원 하기 위한 유연성을 제공 하는 동시 Vspackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

이 항목에서 설명 하는 시나리오는 유일 하 게 선택할 수 있는 것은 아니지만 제안 된 최선의 구현 방법으로 제공 됩니다.

## <a name="components-privacy-and-sharing"></a>구성 요소, 개인 정보 보호 및 공유

### <a name="make-your-components-independent"></a>구성 요소를 독립적으로 만들기

구성 요소를 식별 하 고 채우고,을 할당 하 `GUID` 고, 구성 요소를 배포한 후에는 해당 구성을 변경할 수 없습니다. 구성 요소의 컴퍼지션을 변경 하는 경우 생성 되는 구성 요소는 새로운 새 구성 요소 여야 합니다 `GUID` . 이러한 사실을 감안 하 여 각 구성 요소 독립적인 자체 기반 단위를 만들면 가장 큰 버전의 유연성이 제공 됩니다. 구성 요소를 관리 하는 규칙에 대 한 자세한 내용은 구성 요소 [코드 변경](/windows/desktop/Msi/changing-the-component-code) 및 [구성 요소 규칙이 중단 되 면 어떻게 되나요?](/windows/desktop/Msi/what-happens-if-the-component-rules-are-broken)를 참조 하세요.

### <a name="do-not-mix-shared-and-private-resources-in-a-component"></a>구성 요소에서 공유 및 개인 리소스를 혼합 하지 마세요.

참조 횟수는 구성 요소 수준에서 발생 합니다. 따라서 한 구성 요소에서 공유 리소스와 개인 리소스를 혼합 하면 공유 리소스를 덮어쓰지 않고도 실행 파일 등의 개인 리소스를 업데이트할 수 없습니다. 이 시나리오는 이전 버전과의 호환성 문제를 생성 하 고 side-by-side 기능을 만들 수 없도록 제한 합니다.

예를 들어 VSPackage을에 등록 하는 데 사용 되는 레지스트리 값은 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] Visual Studio에 VSPackage을 등록 하는 데 사용 되는 것과는 다른 구성 요소에 보관 되어야 합니다. 공유 파일 또는 레지스트리 값이 다른 구성 요소로 이동 합니다.

## <a name="scenario-1-shared-vspackage"></a>시나리오 1: Shared VSPackage

이 시나리오에서는 여러 버전의 Visual Studio를 지 원하는 단일 이진 파일이 Windows Installer 패키지에 제공 됩니다. 각 버전의 Visual Studio에 등록 하는 것은 사용자가 선택할 수 있는 기능을 통해 제어 됩니다. 또한 개별 기능에 할당 된 경우 각 구성 요소를 설치 또는 제거에 대해 개별적으로 선택 하 여 사용자가 VSPackage를 여러 버전의에 통합 하는 것을 제어할 수 있습니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Windows Installer 패키지의 기능 사용에 대 한 자세한 내용은 [Windows Installer 기능](/windows/desktop/Msi/windows-installer-features) 을 참조 하세요.

![VS Shared VSPackage installer](../../extensibility/internals/media/vs_sharedpackage.gif "VS_SharedPackage")

그림에 표시 된 것 처럼 공유 구성 요소는 항상 설치 되는 Feat_Common 기능의 일부로 구성 됩니다. Feat_VS2002 및 Feat_VS2003 기능을 표시 하 여 사용자는 설치 시 VSPackage 통합 하려는 Visual Studio 버전을 선택할 수 있습니다. 또한 사용자는 Windows Installer 유지 관리 모드를 사용 하 여 기능을 추가 하거나 제거할 수 있습니다 .이 경우 다른 버전의 Visual Studio에서 VSPackage 등록 정보를 추가 하거나 제거 합니다.

> [!NOTE]
> 기능의 표시 열을 0으로 설정 하면 해당 열이 숨겨집니다. 낮은 수준의 열 값 (예: 1)은 항상 설치 되도록 합니다. 자세한 내용은 [Installlevel 속성](/windows/desktop/Msi/installlevel) 및 [기능 표](/windows/desktop/Msi/feature-table)를 참조 하세요.

## <a name="scenario-2-shared-vspackage-update"></a>시나리오 2: Shared VSPackage Update

이 시나리오에서 시나리오 1에서 업데이트 된 버전의 VSPackage 설치 관리자가 제공 됩니다. 논의를 위해 업데이트는 Visual Studio에 대 한 지원을 추가 하지만 더 간단한 보안 패치 또는 버그 수정 Service Pack 수도 있습니다. 최신 구성 요소를 설치 하는 Windows Installer 규칙에는 시스템에 있는 변경 되지 않은 구성 요소가 아직 다시 복사 되지 않아야 합니다. 이 경우 버전 1.0이 이미 있는 시스템은 업데이트 된 구성 요소 Comp_MyVSPackage.dll 덮어쓰고 사용자가 구성 요소 Comp_VS2005_Reg Feat_VS2005 새 기능을 추가 하도록 선택할 수 있습니다.

> [!CAUTION]
> VSPackage가 여러 버전의에서 공유 될 때마다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 이후 VSPackage 버전이 이전 버전의 Visual Studio와의 호환성을 유지 하는 것이 중요 합니다. 이전 버전과의 호환성을 유지할 수 없는 경우 side-by-side, private Vspackage를 사용 해야 합니다. 자세한 내용은 [여러 버전의 Visual Studio 지원](../../extensibility/supporting-multiple-versions-of-visual-studio.md)을 참조 하세요.

![VS 공유 VS 패키지 업데이트 설치 관리자](../../extensibility/internals/media/vs_sharedpackageupdate.gif "VS_SharedPackageUpdate")

이 시나리오에서는 Windows Installer의 사소한 업그레이드 지원 기능을 활용 하 여 새로운 VSPackage 설치 관리자를 제공 합니다. 사용자는 버전 1.1만 설치 하 고 버전 1.0을 업그레이드 합니다. 그러나 시스템에 버전 1.0이 있을 필요는 없습니다. 동일한 설치 관리자가 버전 1.0이 없는 시스템에 버전 1.1을 설치 합니다. 이러한 방식으로 사소한 업그레이드를 제공 하는 장점은 업그레이드 설치 관리자와 전체 제품 설치 관리자를 개발 하는 작업을 수행할 필요가 없다는 것입니다. 한 설치 관리자가 두 작업을 모두 수행 합니다. 보안 픽스 또는 Service Pack는 Windows Installer 패치를 대신 사용할 수 있습니다. 자세한 내용은 [패치 및 업그레이드](/windows/desktop/Msi/patching-and-upgrades)를 참조 하세요.

## <a name="scenario-3-side-by-side-vspackage"></a>시나리오 3: Side-by-side VSPackage

이 시나리오는 Visual Studio .NET 2003 및 Visual Studio의 각 버전에 대 한 두 개의 VSPackage 설치 관리자를 제공 합니다. 각 설치 관리자는 side-by-side 또는 개인 VSPackage (특정 버전의 Visual Studio에 대해 특별히 빌드되고 설치 된)를 설치 합니다. 각 VSPackage는 자체 구성 요소에 있습니다. 따라서 각각은 패치 또는 유지 관리 릴리스와 개별적으로 서비스를 제공할 수 있습니다. VSPackage DLL은 버전에 따라 다르므로 DLL과 같은 구성 요소에 등록 정보를 포함 하는 것이 안전 합니다.

![VS Side-by-side VS 패키지 설치 관리자](../../extensibility/internals/media/vs_sbys_package.gif "VS_SbyS_Package")

또한 각 설치 관리자에는 두 설치 관리자 간에 공유 되는 코드가 포함 됩니다. 공유 코드가 공통 위치에 설치 된 경우 .msi 파일을 모두 설치 하면 공유 코드도 한 번만 설치 됩니다. 두 번째 설치 관리자는 구성 요소에 대 한 참조 횟수를 증가 시킵니다. 참조 횟수를 사용 하면 Vspackage 중 하나가 제거 되 면 공유 코드는 다른 VSPackage에 대해 유지 됩니다. 두 번째 VSPackage 제거 되 면 공유 코드가 제거 됩니다.

## <a name="scenario-4-side-by-side-vspackage-update"></a>시나리오 4: Side-by-side VSPackage 업데이트

이 시나리오에서는 VSPackage for Visual Studio가 보안 취약점을 받은 후 업데이트를 실행 해야 합니다. 시나리오 2에서와 같이 기존 설치를 업데이트 하는 새 .msi 파일을 만들어 보안 픽스를 포함 하 고 새 설치를 이미 준비 된 상태로 배포할 수 있습니다.

이 경우 VSPackage는 GAC (전역 어셈블리 캐시)에 설치 된 관리 되는 VSPackage입니다. 보안 픽스를 포함 하도록 다시 작성 하는 경우 어셈블리 버전 번호의 수정 번호 부분을 변경 해야 합니다. 새 어셈블리 버전 번호에 대 한 등록 정보는 이전 버전을 덮어쓰므로 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 고정 어셈블리를 로드 합니다.

![VS Side-by-side VS 패키지 업데이트 설치 관리자](../../extensibility/internals/media/vs_sbys_packageupdate.gif "VS_SbyS_PackageUpdate")

Side-by-side 어셈블리 배포에 대 한 자세한 내용은 [.NET Framework를 사용 하 여 배포 간소화 및 DLL 추가 해결](https://msdn.microsoft.com/library/ms973843.aspx)을 참조 하세요.

## <a name="see-also"></a>추가 정보

- [Windows Installer](/windows/desktop/Msi/windows-installer-portal)
- [여러 버전의 Visual Studio 지원](../../extensibility/supporting-multiple-versions-of-visual-studio.md)
