---
title: VS패키지 설정 시나리오 | 마이크로 소프트 문서
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703980"
---
# <a name="vspackage-setup-scenarios"></a>VSPackage 설치 시나리오

유연성을 위해 VSPackage 설치 관리자를 설계하는 것이 중요합니다. 예를 들어 나중에 보안 패치를 릴리스해야 하거나 철저한 버전 전환 지원이 필요한 비즈니스 전략을 변경할 수 있습니다.

[여러 버전의 Visual Studio 지원에서는](../../extensibility/supporting-multiple-versions-of-visual-studio.md)VSPackage의 공유 또는 나란히 설치를 통해 병렬 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 설치를 지원하는 장점과 문제에 대해 읽을 수 있습니다. 즉, 나란히 VSPackage는 의 새로운 기능을 지원할 수 있는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]유연성을 제공합니다.

이 항목에서 설명하는 시나리오는 유일한 선택 사항이 아니라 제안된 모범 사례로 제공됩니다.

## <a name="components-privacy-and-sharing"></a>구성 요소, 개인 정보 보호 및 공유

### <a name="make-your-components-independent"></a>구성 요소를 독립적으로 만들기

구성 요소를 식별하고 `GUID`채우고, 을 할당하고, 구성 요소를 배포한 후에는 해당 구성요소를 변경할 수 없습니다. 구성 요소의 컴포지션을 변경하는 경우 결과 구성 요소는 새 `GUID`구성 요소와 새 구성 요소여야 합니다. 이러한 사실을 감안할 때, 각 구성 요소를 독립적이고 독립적인 단위로 만들어 가장 큰 버전 관리 유연성을 확보할 수 있습니다. 구성 요소를 관리하는 규칙에 대한 자세한 내용은 [구성 요소 코드 변경](/windows/desktop/Msi/changing-the-component-code) 및 구성 요소 [규칙이 손상되면 어떻게 됩니까 를](/windows/desktop/Msi/what-happens-if-the-component-rules-are-broken)참조하십시오.

### <a name="do-not-mix-shared-and-private-resources-in-a-component"></a>구성 요소에서 공유 및 개인 리소스를 혼합하지 마십시오.

참조 카운트는 구성 요소 수준에서 발생합니다. 따라서 공유 리소스와 개인 리소스를 한 구성 요소에 혼합하면 공유 리소스를 덮어쓰지 않고 실행 파일과 같은 개인 리소스를 업데이트할 수 없습니다. 이 시나리오에서는 이전 버전과의 호환성 문제를 만들고 나란히 기능을 만들지 못하도록 제한합니다.

예를 들어 VSPackage를 등록하는 데 사용되는 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] 레지스트리 값은 VSPackage를 Visual Studio에 등록하는 데 사용되는 것과 는 별도로 구성 요소에 보관해야 합니다. 공유 파일 또는 레지스트리 값은 또 다른 구성 요소로 이동합니다.

## <a name="scenario-1-shared-vspackage"></a>시나리오 1: 공유 VS패키지

이 시나리오에서는 공유 VSPackage(여러 버전의 Visual Studio를 지원하는 단일 바이너리)가 Windows 설치 관리자 패키지로 제공됩니다. Visual Studio의 각 버전에 등록하는 것은 사용자가 선택할 수 있는 기능에 의해 제어됩니다. 또한 별도의 피처에 할당된 경우 설치 또는 제거를 위해 각 구성 요소를 개별적으로 선택할 수 있으므로 사용자가 VSPackage를 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]다른 버전의 에 통합할 수 있습니다. Windows [설치 관리자](/windows/desktop/Msi/windows-installer-features) 패키지의 기능 사용에 대한 자세한 내용은 Windows 설치 관리자 기능을 참조하십시오.

![VS 공유 VS패키지 설치 프로그램](../../extensibility/internals/media/vs_sharedpackage.gif "VS_SharedPackage")

그림과 같이 공유 구성 요소는 항상 설치되는 Feat_Common 기능의 일부로 구성됩니다. Feat_VS2002 및 Feat_VS2003 기능을 표시함으로써 사용자는 설치 시 VSPackage를 통합할 Visual Studio 버전을 선택할 수 있습니다. 사용자는 Windows Installer 유지 관리 모드를 사용하여 기능을 추가하거나 제거할 수 있으며, 이 경우 다른 버전의 Visual Studio에서 VSPackage 등록 정보를 추가하거나 제거합니다.

> [!NOTE]
> 피처의 표시 열을 0으로 설정하면 피쳐가 숨겨지습니다. 1과 같은 낮은 수준 열 값은 항상 설치됩니다. 자세한 내용은 [INSTALLLEVEL 속성](/windows/desktop/Msi/installlevel) 및 [기능 테이블을](/windows/desktop/Msi/feature-table)참조하십시오.

## <a name="scenario-2-shared-vspackage-update"></a>시나리오 2: 공유 VS패키지 업데이트

이 시나리오에서는 시나리오 1에서 VSPackage 설치 프로그램의 업데이트 된 버전이 제공 됩니다. 토론을 위해 이 업데이트는 Visual Studio에 대한 지원을 추가하지만 더 간단한 보안 패치 또는 버그 수정 서비스 팩일 수도 있습니다. 최신 구성 요소를 설치하기 위한 Windows Installer의 규칙에 따라 시스템에 이미 변경되지 않은 구성 요소가 다시 복사되지 않도록 해야 합니다. 이 경우 버전 1.0이 이미 있는 시스템은 업데이트된 구성 요소 Comp_MyVSPackage.dll을 덮어쓰고 사용자가 해당 구성 요소 Comp_VS2005_Reg 사용하여 Feat_VS2005 새 기능을 추가하도록 선택할 수 있도록 합니다.

> [!CAUTION]
> VSPackage가 여러 버전의 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]사이에서 공유될 때마다 VSPackage의 후속 릴리스는 이전 버전의 Visual Studio와 이전 버전과의 이전 버전과의 호환성을 유지하는 것이 중요합니다. 이전 버전과의 호환성을 유지할 수 없는 경우 나란히 개인 VSPackage를 사용해야 합니다. 자세한 내용은 [여러 버전의 Visual Studio 를 참조하세요.](../../extensibility/supporting-multiple-versions-of-visual-studio.md)

![VS 공유 VS 패키지 업데이트 설치 프로그램](../../extensibility/internals/media/vs_sharedpackageupdate.gif "VS_SharedPackageUpdate")

이 시나리오에서는 Windows Installer의 사소한 업그레이드 지원을 활용 하는 새 VSPackage 설치 관리자를 제공 합니다. 사용자는 단순히 버전 1.1을 설치하고 버전 1.0을 업그레이드합니다. 그러나 시스템에 버전 1.0이 있을 필요는 없습니다. 동일한 설치 프로그램은 버전 1.0이 없는 시스템에 버전 1.1을 설치합니다. 이러한 방식으로 사소한 업그레이드를 제공하는 이점은 업그레이드 설치 관리자 및 전체 제품 설치 관리자를 개발하는 작업을 진행할 필요가 없다는 것입니다. 한 설치 관리자는 두 작업을 모두 수행합니다. 보안 수정 또는 서비스 팩 대신 Windows 설치 관리자 패치를 활용할 수 있습니다. 자세한 내용은 [패치 및 업그레이드 를](/windows/desktop/Msi/patching-and-upgrades)참조하십시오.

## <a name="scenario-3-side-by-side-vspackage"></a>시나리오 3: 나란히 VS패키지

이 시나리오에서는 Visual Studio .NET 2003 및 Visual Studio의 각 버전에 대해 하나씩 두 개의 VSPackage 설치 프로그램을 제공합니다. 각 설치 관리자는 나란히 또는 개인 VSPackage(특정 버전의 Visual Studio에 맞게 특별히 빌드되고 설치되는 패키지)를 설치합니다. 각 VSPackage는 자체 구성 요소에 있습니다. 따라서 각 패치 또는 유지 관리 릴리스를 개별적으로 서비스할 수 있습니다. VSPackage DLL은 이제 버전별이므로 DLL과 동일한 구성 요소에 등록 정보를 포함하는 것이 안전합니다.

![VS 나란히 VS 패키지 설치 프로그램](../../extensibility/internals/media/vs_sbys_package.gif "VS_SbyS_Package")

각 설치 관리자에는 두 설치 프로그램 간에 공유되는 코드도 포함됩니다. 공유 코드가 공통 위치에 설치되면 .msi 파일을 모두 설치하면 공유 코드가 한 번만 설치됩니다. 두 번째 설치 관리자는 구성 요소에 대한 참조 수를 증가시다. 참조 수를 확인하면 VSPackage 중 하나가 제거된 경우 다른 VSPackage에 대한 공유 코드가 유지됩니다. 두 번째 VSPackage도 제거된 경우 공유 코드가 제거됩니다.

## <a name="scenario-4-side-by-side-vspackage-update"></a>시나리오 4: 나란히 VS패키지 업데이트

이 시나리오에서는 VSPackage for Visual Studio 보안 취약점이 발생 하 고 업데이트를 발급 해야 합니다. 시나리오 2에서와 같이 기존 설치를 업데이트하여 보안 수정 프로그램을 포함하도록 업데이트하는 새 .msi 파일을 만들고 이미 설치된 보안 수정 프로그램을 사용하여 새 설치를 배포할 수 있습니다.

이 경우 VSPackage는 GAC(전역 어셈블리 캐시)에 설치된 관리되는 VSPackage입니다. 보안 수정 프로그램을 포함하도록 다시 빌드할 때 어셈블리 버전 번호의 개정 번호 부분을 변경해야 합니다. 새 어셈블리 버전 번호의 등록 정보가 이전 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 버전을 덮어쓰면 고정 어셈블리가 로드됩니다.

![VS 나란히 VS 패키지 업데이트 설치 프로그램](../../extensibility/internals/media/vs_sbys_packageupdate.gif "VS_SbyS_PackageUpdate")

나란히 배치되는 어셈블리에 대한 자세한 내용은 [.NET 프레임워크를 사용하여 배포 단순화 및 DLL 헬을 해결합니다.](https://msdn.microsoft.com/library/ms973843.aspx)

## <a name="see-also"></a>참조

- [윈도우 설치 프로그램](/windows/desktop/Msi/windows-installer-portal)
- [여러 버전의 Visual Studio 지원](../../extensibility/supporting-multiple-versions-of-visual-studio.md)
