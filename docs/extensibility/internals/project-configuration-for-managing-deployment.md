---
title: 배포 관리를 위한 프로젝트 구성 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations, managing deployment
- projects [Visual Studio SDK], configuration for managing deployment
ms.assetid: bd5940d9-d94d-4944-beda-4ec1ab2bbde5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 62f7bf6535a89e46799ade88fe8976974b3019c5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706706"
---
# <a name="project-configuration-for-managing-deployment"></a>배포 관리를 위한 프로젝트 구성
배포는 출력 항목을 빌드 프로세스에서 디버깅 및 설치에 대 한 예상 된 위치로 물리적으로 이동 하는 작동 합니다. 예를 들어 웹 응용 프로그램은 로컬 컴퓨터에 빌드된 다음 서버에 배치할 수 있습니다.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]프로젝트가 배포에 참여할 수 있는 두 가지 방법을 지원합니다.

- 배포 프로세스의 주제로.

- 배포 프로세스의 관리자로.

  솔루션을 배포하려면 먼저 배포 프로젝트를 추가하여 배포 옵션을 구성해야 합니다. 배포 프로젝트가 아직 없는 경우 **빌드** 메뉴에서 **솔루션 배포를** 선택하거나 솔루션을 마우스 오른쪽 단추로 클릭할 때 빌드 프로젝트를 만들지 묻는 메시지가 표시됩니다. **예를** 클릭하면 **원격 배포 마법사** 프로젝트를 선택한 새 프로젝트 **추가** 대화 상자가 열립니다.

  원격 배포 마법사는 응용 프로그램 유형(Windows 또는 웹), 포함할 프로젝트 출력 그룹, 포함할 추가 파일 및 배포할 원격 컴퓨터를 요청합니다. 마법사의 마지막 페이지에는 선택한 옵션에 대한 요약이 표시됩니다.

  배포 프로세스의 대상이 되는 프로젝트는 대체 환경으로 이동해야 하는 출력 항목을 생성합니다. 이러한 출력 항목은 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> 프로젝트가 출력을 그룹화할 수 있도록 허용하는 경우 인터페이스의 매개 변수로 설명됩니다. 구현과 `IVsProjectCfg2`관련된 자세한 내용은 [출력에 대한 프로젝트 구성을](../../extensibility/internals/project-configuration-for-output.md)참조하십시오.

  배포 프로세스를 관리하는 배포 프로젝트는 Deploy 명령을 사용하도록 설정하고 이 명령을 선택하면 응답합니다. 배포 프로젝트는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> 배포를 수행하고 인터페이스를 호출하여 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployStatusCallback> 배포 상태 이벤트를 보고하는 인터페이스를 구현합니다.

  구성은 빌드 또는 배포 작업에 영향을 주는 종속성을 지정할 수 있습니다. 빌드 또는 배포 종속성은 구성 자체가 빌드되거나 배포되기 전이나 후에 빌드하거나 배포해야 하는 프로젝트입니다. 프로젝트 간의 빌드 종속성은 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> 인터페이스와 함께 설명되며 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> 인터페이스와 함께 종속성을 배포합니다. 자세한 내용은 [건물용 프로젝트 구성을](../../extensibility/internals/project-configuration-for-building.md)참조하십시오.

## <a name="see-also"></a>참조
- [구성 옵션 관리](../../extensibility/internals/managing-configuration-options.md)
- [빌드를 위한 프로젝트 구성](../../extensibility/internals/project-configuration-for-building.md)
- [출력에 대한 프로젝트 구성](../../extensibility/internals/project-configuration-for-output.md)
