---
title: 공유 및 버전 관리 Vspackage 중에서 선택 Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- SxS
- side-by-side installation
- installation [Visual Studio SDK], side-by-side
ms.assetid: e3128ac3-2e92-48e9-87ab-3b6c9d80e8c9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 96386c2d3b7d1e822fdd1dd6632d754740f86301
ms.sourcegitcommit: 4b29efeb3a5f05888422417c4ee236e07197fb94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90011933"
---
# <a name="choose-between-shared-and-versioned-vspackages"></a>공유 및 버전 관리 Vspackage 중에서 선택
서로 다른 버전의 Visual Studio가 동일한 컴퓨터에 공존할 수 있습니다. Vspackage는 모든 혼합 버전을 지원할 수 있습니다 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

 두 가지 전략, 즉 공유 전략 또는 버전이 지정 된 전략 중 하나를 통해 Vspackage의 병렬 설치를 사용 하도록 설정할 수 있습니다. 여러 버전의와 관련 된 버전의 .NET Framework을 모두 포함 합니다 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

 공유 전략에서는 여러 버전의에서 사용 하기 위해 하나의 VSPackage가 등록 됩니다 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . 버전이 지정 된 전략에서는 지원 되는 각 버전에 대해 하나씩, 여러 VSPackage Dll이 설치 됩니다 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

## <a name="shared-vspackages"></a>공유 Vspackage
 여러 버전의에서 동일한 VSPackage를 사용 하는 경우 공유 VSPackage를 사용 하는 것이 적합 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 합니다. 공유 VSPackage을 구현 하려면 다음 단계를 수행 해야 합니다.

- 여러 버전의와 호환 되는 VSPackage를 만드세요 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . 이 작업을 수행 하는 방법에는 다음 두 가지가 있습니다.

  - 지원 되는 가장 오래 된 버전의 기능만 사용 하도록 VSPackage를 제한 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 합니다.

  - VSPackage를 프로그래밍 하 여 실행 중인의 버전에 맞게 조정 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 합니다. 그런 다음 새 서비스에 대 한 쿼리가 실패 하면 VSPackage는 이전 버전의에서 지원 되는 다른 서비스를 제공할 수 있습니다 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

- VSPackage를 적절 하 게 등록 합니다. 자세한 내용은 [VSPackage 등록](../extensibility/internals/vspackage-registration.md) 및 [관리 되는 VSPackage 등록](/previous-versions/bb166783(v=vs.100))을 참조 하세요.

- 파일 확장명을 적절 하 게 등록 합니다. 자세한 내용은 side-by-side [배포를 위한 파일 이름 확장명 등록](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)을 참조 하세요.

- 적절 한 버전의에 대 한 VSPackage를 배포 하는 설치 관리자를 만듭니다 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . 자세한 내용은 Windows Installer 및 [구성 요소 관리](../extensibility/internals/component-management.md)를 [사용 하 여 vspackage 설치](../extensibility/internals/installing-vspackages-with-windows-installer.md) 를 참조 하세요.

- 등록 충돌 문제를 해결 합니다. 자세한 내용은 [VSPackage 등록](../extensibility/internals/vspackage-registration.md)을 참조 하세요.

- 여러 버전의 안전 하 게 설치 및 제거할 수 있도록 공유 파일 및 버전 관리 파일 모두 참조 횟수를 준수 하는지 확인 합니다. 자세한 내용은 [구성 요소 관리](../extensibility/internals/component-management.md)를 참조 하세요.

## <a name="versioned-vspackages"></a>버전 관리 Vspackage
 버전이 지정 된 VSPackage 전략에서는 지원 되는 각 버전에 대해 VSPackage 하나를 만듭니다 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . 이 작업은 이후 버전의에서 제공 하는 서비스를 활용 하는 경우에 적합 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 합니다. 각 VSPackage는 다른 사용자에 게 영향을 주지 않고 진화 될 수 있기 때문입니다. 그럼에도 불구 하 고 단일 코드 베이스 또는 여러 독립적인 코드 베이스에서 여러 이진 파일을 만드는 방법에 대 한 버전 지정 전략은 공유 전략 보다 초기 개발을 더 많이 해야 할 수 있습니다. 또한 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 설치 되어 있고 VSPackage에서 지 원하는 버전을 검색 하는 단일 설치 또는 각 버전에 대해 별도의 설치 프로그램을 만들어야 하기 때문에 추가 설치 작업이 필요할 수 있습니다.

## <a name="binary-compatibility"></a>이진 호환성
 일반적으로 이진 호환성을 사용 하면 이전 버전의 visual Studio에서 개발한 네이티브 코드 Vspackage를 사용 하 여 이후 버전의 Visual Studio에서 실행할 수 있습니다. 그러나 다음과 같은 세 가지 중요 한 예외가 있습니다.

- VSPackage 특정 버전의 공용 언어 런타임을 사용 하는 경우 실행 중인 버전을 확인 해야 합니다 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

- VSPackage는 다른 VSPackage 또는 다른 제품의 특정 기능에 대 한 종속성이 있을 수 있습니다. 따라서 종속성이 충족 되는 경우에만 VSPackage을 실행할 수 있습니다.

- VSPackage는 Service Pack 이상 버전의 보안 수정에 의해 영향을 받을 수 있습니다 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . 이러한 경우 이전 버전의로 개발 된 VSPackage [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 보안 픽스를 적용 한 후 버전에서 실행 되지 않을 수 있습니다. 그러나 최신 버전을 사용 하 여 패키지를 다시 작성 하 고 이전 버전 에서도 실행 되도록 할 수 있습니다.

  관리 되는 Vspackage는의 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 대상 버전과 일치 하는 및 버전을 사용 하 여 빌드해야 합니다 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

  VSPackage 이진 파일에 대 한 이진 호환성 계획 외에도 솔루션 및 프로젝트 파일 형식을 고려해 야 합니다. VSPackage에서 새 프로젝트 형식을 만드는 경우 한 버전 또는 여러 버전의에서 실행할 수 있는지 여부를 결정 해야 합니다 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . 자세한 내용은 [사용자 지정 프로젝트 업그레이드](../extensibility/internals/upgrading-projects.md#upgrading-custom-projects)를 참조 하세요.

## <a name="see-also"></a>참고 항목
- [Windows Installer를 사용 하 여 Vspackage 설치](../extensibility/internals/installing-vspackages-with-windows-installer.md)
- [구성 요소 관리](../extensibility/internals/component-management.md)