---
title: 공유 및 버전 이되는 VS패키지 중 선택 | 마이크로 소프트 문서
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
ms.openlocfilehash: 21fefb776fceeeef4db6997a5bd12a8b987af7d2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739880"
---
# <a name="choose-between-shared-and-versioned-vspackages"></a>공유 및 버전 이면된 VSPackage 중에서 선택
Visual Studio의 다른 버전은 동일한 컴퓨터에서 공존할 수 있습니다. VSPackage는 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 모든 버전 혼합을 지원할 수 있습니다.

 두 가지 전략, 즉 공유 전략 또는 버전 관리 전략을 통해 VSPackage를 병렬로 설치할 수 있습니다. 둘 다 .NET Framework의 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 여러 버전 및 관련 버전이 있는 것을 수용합니다.

 공유 전략에서 하나의 VSPackage가 여러 버전의 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]에서 사용하도록 등록됩니다. 버전이 버전이 있는 전략에서는 지원되는 각 버전에 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 대해 하나씩 여러 VSPackage DLL이 설치됩니다.

## <a name="shared-vspackages"></a>공유 VS패키지
 공유 VSPackage를 사용하는 것은 여러 버전의 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]에서 동일한 VSPackage를 사용하는 경우에 적합합니다. 공유 VSPackage를 구현하려면 다음 단계를 수행해야 합니다.

- VSPackage를 여러 버전의 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]여러 버전과 호환되도록 합니다. 이렇게 하는 두 가지 방법을 사용할 수 있습니다.

  - VSPackage를 지원하는 초기 버전의 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 기능만 사용하도록 제한합니다.

  - VSPackage가 실행 중인 버전에 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 맞게 프로그래밍합니다. 그런 다음 최신 서비스에 대한 쿼리가 실패하면 VSPackage는 이전 버전의 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]에서 지원되는 다른 서비스를 제공할 수 있습니다.

- VSPackage를 적절하게 등록하십시오. 자세한 내용은 [VSPackage 등록](../extensibility/internals/vspackage-registration.md) 및 [관리되는 VSPackage 등록을](https://msdn.microsoft.com/library/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)참조하십시오.

- 파일 확장자를 적절하게 등록합니다. 자세한 내용은 [나란히 배포할 수 있는 파일 이름 확장자 등록을](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)참조하십시오.

- 에 대한 적절한 버전에 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]대해 VSPackage를 배포하는 설치 관리자를 만듭니다. 자세한 내용은 WINDOWS 설치 관리자 및 [구성 요소 관리를](../extensibility/internals/component-management.md)통해 [VSPackage 설치를](../extensibility/internals/installing-vspackages-with-windows-installer.md) 참조하십시오.

- 등록 충돌 문제를 해결합니다. 자세한 내용은 [VSPackage 등록을](../extensibility/internals/vspackage-registration.md)참조하십시오.

- 공유 파일과 버전이 있는 파일 모두 참조 카운트를 준수하여 여러 버전을 안전하게 설치하고 제거할 수 있도록 합니다. 자세한 내용은 [구성 요소 관리를](../extensibility/internals/component-management.md)참조하십시오.

## <a name="versioned-vspackages"></a>버전이 있는 VS패키지
 버전이 있는 VSPackage 전략에 따라 지원하는 각 버전에 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 대해 하나의 VSPackage를 만듭니다. 이 작업을 수행하는 것은 각 VSPackage가 다른 버전에 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]영향을 주지 않고 진화할 수 있기 때문에 의 이후 버전에서 제공하는 서비스를 활용할 것으로 예상되는 경우에 적합합니다. 그럼에도 불구하고 단일 코드 베이스 또는 여러 독립 코드 베이스에서 여러 바이너리를 만드는 버전이 있는 전략은 공유 전략보다 더 많은 초기 개발을 수반할 수 있습니다. 또한 각 버전에 대해 별도의 설치를 만들거나 설치되는 버전을 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 검색하고 VSPackage가 지원하는 단일 설정을 만들어야 하므로 추가 설치 작업이 필요할 수 있습니다.

## <a name="binary-compatibility"></a>이진 호환성
 일반적으로 바이너리 호환성을 사용하면 이전 버전의 Visual Studio에서 개발한 네이티브 코드 VSPackage를 이후 버전의 Visual Studio에서 실행할 수 있습니다. 그러나 세 가지 중요한 예외가 있습니다.

- VSPackage가 공통 언어 런타임의 특정 버전을 사용하는 경우 실행 중인 버전을 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 결정해야 합니다.

- VSPackage는 다른 VSPackage 또는 다른 제품의 특정 기능에 대한 종속성을 가질 수 있습니다. 따라서 VSPackage는 종속성이 충족되는 경우에만 실행할 수 있습니다.

- VSPackage는 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 서비스 팩의 보안 수정 또는 이후 버전의 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]에 의해 영향을 받을 수 있습니다. 이러한 경우 이전 버전의 VSPackage는 보안 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] 수정 이 적용된 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 후 버전에서 실행되지 않을 수 있습니다. 그러나 이후 버전으로 패키지를 다시 빌드하고 이전 버전에서도 실행되도록 할 수 있습니다.

  관리되는 VSPackage는 의 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 버전과 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] 대상 버전의 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]과 일치하는 을 사용하여 빌드해야 합니다.

  VSPackage 바이너리에 대한 이진 호환성을 계획하는 것 외에도 솔루션 및 프로젝트 파일 형식도 고려해야 합니다. VSPackage가 새 프로젝트 유형을 만드는 경우 한 버전에서만 실행할 수 있는지 또는 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]여러 버전의 에서 실행할 수 있는지 결정해야 합니다. 자세한 내용은 [사용자 지정 프로젝트 업그레이드를](../extensibility/internals/upgrading-projects.md#upgrading-custom-projects)참조하십시오.

## <a name="see-also"></a>참조
- [WINDOWS 설치 관리자로 VS패키지 설치](../extensibility/internals/installing-vspackages-with-windows-installer.md)
- [구성 요소 관리](../extensibility/internals/component-management.md)
