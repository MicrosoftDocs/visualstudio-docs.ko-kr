---
title: 소스 제어 VS패키지 아키텍처 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, architecture
ms.assetid: 453125fc-23dc-49b1-8476-94581f05e6c7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d6e62aa9e2d725e982f0605e2721f0bfeb3cc5ee
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705079"
---
# <a name="source-control-vspackage-architecture"></a>소스 제어 VSPackage 아키텍처
소스 제어 패키지는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE가 제공하는 서비스를 사용하는 VSPackage입니다. 그 대가로 소스 제어 패키지는 소스 제어 서비스로서의 기능을 제공합니다. 또한 소스 제어 패키지는 소스 제어를 에 통합하기 위한 소스 제어 플러그인보다 더 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]다양한 대안입니다.

 소스 제어 플러그인 API를 구현하는 소스 제어 플러그인은 엄격한 계약을 준수합니다. 예를 들어 플러그인은 기본 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 사용자 인터페이스(UI)를 대체할 수 없습니다. 또한 소스 제어 플러그인 API는 플러그인이 자체 소스 제어 모델을 구현할 수 있도록 설정하지 않습니다. 그러나 소스 제어 패키지는 이러한 두 가지 제한 사항을 모두 극복합니다. 소스 제어 패키지는 사용자의 소스 제어 환경을 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 완벽하게 제어할 수 있습니다. 또한 소스 제어 패키지는 자체 소스 제어 모델 및 논리를 사용할 수 있으며 모든 소스 제어 관련 사용자 인터페이스를 정의할 수 있습니다.

## <a name="source-control-package-components"></a>소스 제어 패키지 구성 요소
 아키텍처 다이어그램에 표시된 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 것처럼 소스 제어 스텁이라는 구성 요소는 소스 제어 패키지와 소스 제어 패키지를 통합하는 VSPackage입니다. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]

 소스 제어 스텁은 다음 작업을 처리합니다.

- 소스 제어 패키지 등록에 필요한 공통 UI를 제공합니다.

- 소스 제어 패키지를 로드합니다.

- 소스 제어 패키지를 활성/비활성으로 설정합니다.

  소스 제어 스텁은 소스 제어 패키지에 대한 활성 서비스를 찾고 IDE에서 해당 패키지로 들어오는 모든 서비스 호출을 라우팅합니다.

  소스 제어 어댑터 패키지는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 제공하는 특수 소스 제어 패키지입니다. 이 패키지는 소스 제어 플러그인 API를 기반으로 소스 제어 플러그인을 지원하기 위한 핵심 구성 요소입니다. 소스 제어 플러그인이 활성 플러그인인 경우 소스 제어 스텁은 해당 이벤트를 소스 제어 어댑터 패키지로 보냅니다. 차례로 소스 제어 어댑터 패키지는 소스 제어 플러그인 API를 사용하여 소스 제어 플러그인과 통신하고 모든 소스 제어 플러그인에 공통적인 기본 UI를 제공합니다.

  반면에 소스 제어 패키지가 활성 패키지인 경우 소스 제어 스텁은 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] 소스 제어 패키지 인터페이스를 사용하여 패키지와 직접 통신합니다. 소스 제어 패키지는 자체 소스 제어 UI를 호스팅합니다.

  ![소스 제어 아키텍처 그래픽](../../extensibility/internals/media/vsipsccarch.gif "VSIPSCCArch")

  소스 제어 패키지의 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 경우 통합을 위한 소스 제어 코드 또는 API를 제공하지 않습니다. 소스 제어 플러그인이 엄격한 함수 및 콜백 집합을 구현해야 하는 [소스 제어 플러그인 만들기에](../../extensibility/internals/creating-a-source-control-plug-in.md) 설명된 접근 방식과 대조됩니다.

  다른 VSPackage와 마찬가지로 소스 제어 패키지는 을 사용하여 `CoCreateInstance`만들 수 있는 COM 개체입니다. VSPackage를 구현하여 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>IDE에서 사용할 수 있습니다. 인스턴스가 생성되면 VSPackage는 사이트 포인터와 IDE에서 사용 가능한 서비스 및 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> 인터페이스에 대한 VSPackage 액세스를 제공하는 인터페이스를 받습니다.

  VSPackage 기반 소스 제어 패키지를 작성하려면 소스 제어 플러그인 API 기반 플러그인을 작성하는 것보다 고급 프로그래밍 전문 지식이 필요합니다.

## <a name="see-also"></a>참조
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>
- [시작](../../extensibility/internals/getting-started-with-source-control-vspackages.md)
