---
title: 소스 제어 VS패키지 만들기 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], creating source control packages
- source control packages
ms.assetid: cca0a9ed-48ff-409f-8036-ed8db0f7533e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8608aae718ff9f8bdf2e40c0ab648c1d22c38257
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709184"
---
# <a name="create-a-source-control-vspackage"></a>소스 제어 VS패키지 만들기
이 설명서에는 통합된 소스 제어 패키지의 아키텍처 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]개요에 대한 링크, 구현할 인터페이스에 의해 정의된 API 및 사용할 서비스에 대한 링크 및 간단한 소스 제어 패키지 구현을 보여 주는 샘플이 포함되어 있습니다.

 소스 제어 VSPackage를 사용하면 소스 제어가 와 통합할 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]수 있는 심층 통합 경로를 만들 수 있습니다. 패키지를 사용하면 패키지에서 호스팅되는 기본 소스 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]제어 UI를 우회하고, 프로젝트 시스템의 소스 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 제어 요청에 응답하고, **Solution Explorer**와 같은 구성 요소와 상호 작용할 수 있습니다. 이 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] 메커니즘은 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 파트너에게 서비스 모델을 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 사용하여 통합할 수 있는 VSPackage를 만들 수 있는 권한을 부여합니다.

## <a name="in-this-section"></a>섹션 내용
- [시작](../../extensibility/internals/getting-started-with-source-control-vspackages.md)

 에서 소스 제어 기능을 구현하기 위한 소스 제어 플러그인에 대한 보다 고급 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]대안인 소스 제어 패키지에 대해 설명합니다.

- [Architecture](../../extensibility/internals/source-control-vspackage-architecture.md)

 다이어그램을 제시하고 소스 제어 패키지의 구성 요소를 설명합니다.

- [기능](../../extensibility/internals/source-control-vspackage-features.md)

 소스 제어 패키지의 다양한 기능에 대해 설명합니다.

- [디자인 요소](../../extensibility/internals/source-control-vspackage-design-elements.md)

 소스 제어 패키지가 심층 통합을 위해 구현해야 하는 VSPackage의 구조를 설명합니다.

## <a name="related-sections"></a>관련 단원
- [소스 제어 플러그인 만들기](../../extensibility/internals/creating-a-source-control-plug-in.md)

 소스 제어 사용자 인터페이스(UI)에서 소스 제어 기능을 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 제공하는 소스 제어 플러그인을 만드는 방법에 대해 설명합니다.

- [소스 제어](../../extensibility/internals/source-control.md)

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]의 통합 기능으로 소스 제어를 구현하기 위한 옵션에 대해 설명합니다.
