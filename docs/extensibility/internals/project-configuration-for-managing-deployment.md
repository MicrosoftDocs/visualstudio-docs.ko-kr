---
title: 배포 | 관리를 위한 프로젝트 구성 Microsoft Docs
description: 디버깅 및 설치를 위해 예상되는 위치에 배포하는 방법과 Visual Studio 배포를 지원하는 프로젝트를 지원하는 두 가지 방법에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- project configurations, managing deployment
- projects [Visual Studio SDK], configuration for managing deployment
ms.assetid: bd5940d9-d94d-4944-beda-4ec1ab2bbde5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3c6077665ccc3bbe5f87b91a1d2fc5636e08539d
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899903"
---
# <a name="project-configuration-for-managing-deployment"></a>배포 관리를 위한 프로젝트 구성
배포는 빌드 프로세스에서 디버깅 및 설치를 위한 예상 위치로 출력 항목을 물리적으로 이동하는 작업입니다. 예를 들어 웹 애플리케이션을 로컬 컴퓨터에 빌드한 다음 서버에 배치할 수 있습니다.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 에서는 프로젝트를 배포에 포함할 수 있는 두 가지 방법을 지원합니다.

- 배포 프로세스의 주체입니다.

- 배포 프로세스의 관리자로.

  솔루션을 배포하려면 먼저 배포 프로젝트를 추가하여 배포 옵션을 구성해야 합니다. 배포 프로젝트가 아직 없는 경우 **빌드** 메뉴에서 **솔루션 배포를** 선택하거나 솔루션을 마우스 오른쪽 단추로 클릭할 때 프로젝트를 만들 것인지 묻는 메시지가 표시됩니다. **예를** 클릭하면 **원격 배포 마법사** 프로젝트가 선택된 새 프로젝트 **추가** 대화 상자가 열립니다.

  원격 배포 마법사는 애플리케이션 유형(Windows 또는 웹), 포함할 프로젝트 출력 그룹, 포함하려는 추가 파일 및 배포하려는 원격 컴퓨터를 요청합니다. 마법사의 마지막 페이지에는 선택한 옵션의 요약이 표시됩니다.

  배포 프로세스의 주체인 프로젝트는 대체 환경으로 이동해야 하는 출력 항목을 생성합니다. 이러한 출력 항목은 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> 프로젝트에 출력을 그룹화할 수 있도록 허용하는 경우의 기본 목적인 인터페이스에 대한 매개 변수로 설명됩니다. 구현과 관련된 자세한 내용은 `IVsProjectCfg2` [출력에 대한 프로젝트 구성을 참조하세요.](../../extensibility/internals/project-configuration-for-output.md)

  배포 프로세스를 관리하는 배포 프로젝트는 배포 명령을 사용하도록 설정하고 이 명령을 선택하면 응답합니다. 배포 프로젝트는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> 인터페이스를 구현하여 배포를 수행하고 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployStatusCallback> 인터페이스를 호출하여 배포 상태 이벤트를 보고합니다.

  구성은 빌드 또는 배포 작업에 영향을 주는 dependencies를 지정할 수 있습니다. 빌드 또는 배포는 구성 자체가 빌드되거나 배포되기 전이나 후에 빌드하거나 배포해야 하는 프로젝트입니다. 프로젝트 간의 빌드 의존도는 인터페이스를 통해 설명하고 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> 인터페이스를 통해 dependencies를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> 배포합니다. 자세한 내용은 [빌드를 위한 프로젝트 구성을 참조하세요.](../../extensibility/internals/project-configuration-for-building.md)

## <a name="see-also"></a>참조
- [구성 옵션 관리](../../extensibility/internals/managing-configuration-options.md)
- [빌드를 위한 프로젝트 구성](../../extensibility/internals/project-configuration-for-building.md)
- [출력에 대한 프로젝트 구성](../../extensibility/internals/project-configuration-for-output.md)
