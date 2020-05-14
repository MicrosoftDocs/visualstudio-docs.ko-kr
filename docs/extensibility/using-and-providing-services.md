---
title: 서비스 이용 및 제공 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- examples [Visual Studio SDK], services
- Visual Studio, services
- services
ms.assetid: c0b415ba-b825-4da0-9faf-8a60a663e302
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8741d8d66af96ad4c6abea44b238393a34c5aa95
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698734"
---
# <a name="using-and-providing-services"></a>서비스 사용 및 제공
서비스는 두 VSPackage 간의 계약입니다. 한 VSPackage는 다른 VSPackage에서 사용할 특정 인터페이스 집합을 제공합니다. 예를 들어 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 로드하는 <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> 모든 VSPackage에 서비스를 제공합니다. 이 서비스는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> 활동 로그에 쓰는 데 사용할 수 있는 인터페이스를 제공합니다. 자세한 내용은 [사용 방법: 활동 로그를 사용](../extensibility/how-to-use-the-activity-log.md)하 여 참조 하십시오.

 VSPackage는 <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> 인터페이스를 사용하여 자체 서비스를 제공할 수 있습니다.

 Visual Studio는 다음과 같은 중요한 서비스를 제공합니다.

|IDE 서비스|설명|
|-----------------|-----------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>|기본 기능, VSPackage 및 레지스트리를 다루는 IDE 서비스에 대한 액세스를 제공합니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>|도구 및 문서 창을 만드는 기능과 같은 IDE의 기본 창 및 UI 관련 기능을 제공합니다.|
|<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>|프로젝트를 등록하고, 새 프로젝트를 만들고, 프로젝트 변경 내용을 모니터링하는 기능과 같은 기본 솔루션 관련 기능을 제공합니다.|

## <a name="in-this-section"></a>섹션 내용
- [서비스 필수 정보](../extensibility/internals/service-essentials.md) Visual Studio 서비스의 중요한 요소를 제공합니다.

- [방법: 서비스 받기](../extensibility/how-to-get-a-service.md) 서비스를 요청(사용)하는 방법에 대해 설명합니다.

- [방법: 서비스 제공](../extensibility/how-to-provide-a-service.md) 서비스를 제공하는 방법에 대해 설명합니다.

- [방법: 비동기 비주얼 스튜디오 서비스 제공](../extensibility/how-to-provide-an-asynchronous-visual-studio-service.md) 비동기 서비스를 제공하는 방법에 대해 설명합니다.

- [방법: 서비스 문제 해결](../extensibility/how-to-troubleshoot-services.md) 일반적인 문제에 대해 논의하고 해결책을 제시합니다.

## <a name="related-sections"></a>관련 단원
- [Visual Studio SDK](../extensibility/visual-studio-sdk.md)
