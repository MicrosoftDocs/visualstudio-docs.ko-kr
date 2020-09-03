---
title: 배포 관리를 위한 프로젝트 구성 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80706706"
---
# <a name="project-configuration-for-managing-deployment"></a>배포 관리를 위한 프로젝트 구성
배포는 디버깅 및 설치를 위해 빌드 프로세스에서 예상 위치로 출력 항목을 물리적으로 이동 하는 동작입니다. 예를 들어 웹 응용 프로그램은 로컬 컴퓨터에서 빌드한 다음 서버에 배치할 수 있습니다.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 에서는 프로젝트를 배포에 포함 시킬 수 있는 두 가지 방법을 지원 합니다.

- 배포 프로세스의 제목입니다.

- 배포 프로세스의 관리자입니다.

  솔루션을 배포 하려면 먼저 배포 옵션을 구성 하는 배포 프로젝트를 추가 해야 합니다. 배포 프로젝트가 아직 없는 경우 **빌드** 메뉴에서 **솔루션 배포** 를 선택 하거나 솔루션을 마우스 오른쪽 단추로 클릭 하 여 배포 프로젝트를 만들 것인지 묻는 메시지가 표시 됩니다. **예** 를 클릭 하면 **원격 배포 마법사** 프로젝트가 선택 된 **새 프로젝트 추가** 대화 상자가 열립니다.

  원격 배포 마법사는 응용 프로그램 유형 (Windows 또는 웹), 포함할 프로젝트 출력 그룹, 포함 하려는 추가 파일 및 배포 하려는 원격 컴퓨터를 요청 합니다. 마법사의 마지막 페이지에는 선택한 옵션에 대 한 요약이 표시 됩니다.

  배포 프로세스의 대상인 프로젝트는 대체 환경으로 이동 해야 하는 출력 항목을 생성 합니다. 이러한 출력 항목은 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> 프로젝트에서 출력을 그룹화 할 수 있도록 하는 기본 용도의 인터페이스에 대 한 매개 변수로 설명 됩니다. 구현에 대 한 자세한 내용은 `IVsProjectCfg2` [출력에 대 한 프로젝트 구성](../../extensibility/internals/project-configuration-for-output.md)을 참조 하세요.

  배포 프로세스를 관리 하는 배포 프로젝트는이 명령을 선택할 때 배포 명령을 사용 하도록 설정 하 고 응답 합니다. 배포 프로젝트는 배포를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> 수행 하 고 배포 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployStatusCallback> 상태 이벤트를 보고 하는 인터페이스를 호출 하는 인터페이스를 구현 합니다.

  구성에서는 빌드 또는 배포 작업에 영향을 주는 종속성을 지정할 수 있습니다. 빌드 또는 배포 종속성은 구성 자체가 빌드하거나 배포 되기 전이나 후에 빌드해야 하거나 배포 해야 하는 프로젝트입니다. 프로젝트 간의 빌드 종속성은 인터페이스로 설명 되며 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> 인터페이스를 사용 하 여 종속성을 배포 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> 합니다. 자세한 내용은 [빌드하기 위한 프로젝트 구성](../../extensibility/internals/project-configuration-for-building.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목
- [구성 옵션 관리](../../extensibility/internals/managing-configuration-options.md)
- [빌드를 위한 프로젝트 구성](../../extensibility/internals/project-configuration-for-building.md)
- [출력에 대한 프로젝트 구성](../../extensibility/internals/project-configuration-for-output.md)
