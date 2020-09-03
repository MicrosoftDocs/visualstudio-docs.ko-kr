---
title: 소스 제어 VSPackage 만들기 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80709184"
---
# <a name="create-a-source-control-vspackage"></a>소스 제어 VSPackage 만들기
이 설명서에는와 통합 된 소스 제어 패키지의 아키텍처 개요에 대 한 링크 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , 구현할 인터페이스에 의해 정의 된 API, 사용할 서비스 및 간단한 소스 제어 패키지 구현을 보여 주는 샘플이 포함 되어 있습니다.

 소스 제어 VSPackage를 사용 하 여 원본 제어를 통합 하기 위한 전체 통합 경로를 만들 수 있습니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . 이를 통해 패키지는에서 호스트 되는 기본 소스 컨트롤 UI를 무시 하 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 고, 프로젝트 시스템의 소스 제어 요청에 응답 하 고, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **솔루션 탐색기**와 같은 구성 요소와 상호 작용할 수 있습니다. 에서는 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 서비스 모델을 사용 하 여와 통합할 수 있는 VSPackage를 만드는 메커니즘이 파트너에 게 역량을 강화 합니다.

## <a name="in-this-section"></a>섹션 내용
- [시작](../../extensibility/internals/getting-started-with-source-control-vspackages.md)

 에서 소스 제어 기능을 구현 하기 위한 소스 제어 플러그 인에 대 한 보다 고급 방법인 소스 제어 패키지에 대해 설명 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 합니다.

- [아키텍처](../../extensibility/internals/source-control-vspackage-architecture.md)

 다이어그램을 표시 하 고 소스 제어 패키지의 구성 요소에 대해 설명 합니다.

- [기능](../../extensibility/internals/source-control-vspackage-features.md)

 원본 제어 패키지의 다양 한 기능에 대해 설명 합니다.

- [디자인 요소](../../extensibility/internals/source-control-vspackage-design-elements.md)

 원본 제어 패키지가 심층 통합을 위해 구현 해야 하는 VSPackage의 구조를 설명 합니다.

## <a name="related-sections"></a>관련 단원
- [소스 제어 플러그 인 만들기](../../extensibility/internals/creating-a-source-control-plug-in.md)

 소스 제어 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] UI (사용자 인터페이스)에서 소스 제어 기능을 제공 하는 소스 제어 플러그 인을 만드는 방법에 대해 설명 합니다.

- [원본 제어](../../extensibility/internals/source-control.md)

 의 통합 기능으로 소스 제어를 구현 하기 위한 옵션에 대해 설명 합니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .
