---
title: 비주얼 스튜디오 2015 SDK의 소스 제어의 새로운 소식 | 마이크로 소프트 문서
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- what's new [Visual Studio SDK], source control
- source control [Visual Studio SDK], what's new
ms.assetid: bcf85418-18fb-4824-9dae-d14bf3d56a77
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f90ae3e1d327b10e99713ad28aa2d5a06c0be34b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703403"
---
# <a name="whats-new-in-source-control-for-the-visual-studio-2015-sdk"></a>비주얼 스튜디오 2015 SDK의 소스 제어의 새로운 소식

[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]에서 소스 제어 VSPackage를 구현 하 여 깊이 통합 된 소스 제어 솔루션을 제공할 수 있습니다. 이 섹션에서는 소스 제어 VSPackage의 기능에 대해 설명하고 구현 단계에 대한 개요를 제공합니다.

## <a name="the-source-control-vspackage"></a>소스 제어 VS패키지

Visual Studio는 두 가지 유형의 소스 제어 솔루션을 지원합니다. 모든 버전의 Visual Studio에서 소스 제어 플러그인 API 기반 플러그인을 통합할 수 있습니다. 또한 높은 수준의 정교함과 자율성을 요구하는 소스 제어 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] 솔루션에 적합한 심층 통합 경로를 제공하는 소스 제어를 위한 VSPackage를 만들 수도 있습니다.

VSPackage는 거의 모든 종류의 기능을 Visual Studio에 추가할 수 있습니다. 소스 제어 VSPackage는 사용자에게 제공되는 UI에서 소스 제어 시스템과의 백 엔드 통신에 이르기까지 Visual Studio에 대한 완벽한 소스 제어 기능을 제공합니다.

소스 제어 VSPackage를 구현하려면 "전부 또는 전혀" 전략이 필요합니다. 소스 제어 VSPackage작성자는 전체 소스 제어 기능뿐만 아니라 Visual Studio와 성공적으로 통합하는 데 필요한 인터페이스뿐만 아니라 전체 소스 제어 기능을 다루기 위해 여러 소스 제어 인터페이스와 새로운 UI 요소(대화 상자, 메뉴 및 도구 모음)를 구현하는 데 상당한 노력을 기울여야 합니다.

다음 단계는 소스 제어 패키지를 구현하는 데 필요한 내용에 대한 일반적인 개요를 제공합니다. 자세한 내용은 [소스 제어 VSPackage 만들기를](../../extensibility/internals/creating-a-source-control-vspackage.md)참조하십시오.

1. 개인 소스 제어 서비스를 제공하는 VSPackage를 만듭니다.

2. Visual Studio에서 제공하는 소스 제어 관련 서비스(예: <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> 및 인터페이스)에서 인터페이스를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider> 구현합니다.

3. 소스 제어 VSPackage를 등록합니다.

4. 메뉴 항목, 대화 상자, 도구 모음 및 컨텍스트 메뉴를 포함한 모든 소스 제어 UI를 구현합니다.

5. 모든 소스 제어 관련 이벤트는 활성화되어 있을 때 소스 제어 VSackage로 전달되며 VSPackage에서 처리해야 합니다.

6. 소스 제어 VSPackage는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> 인터페이스를 구현하는 이벤트와 TPD(트랙 프로젝트 문서) <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> 이벤트(인터페이스에서 구현한 대로)와 같은 이벤트를 수신 대기하고 필요한 조치를 취해야 합니다.

## <a name="see-also"></a>참조

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- [개요](../../extensibility/internals/source-control-integration-overview.md)
- [소스 제어 VSPackage 만들기](../../extensibility/internals/creating-a-source-control-vspackage.md)
