---
title: 관련 서비스 및 인터페이스(소스 제어 VS패키지) | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, interfaces
- interfaces, source control packages
ms.assetid: 3e96e838-5675-46bb-99cf-40d420086038
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 533f1bf4fcfbaebb25ec10908abf4a46ddacd521
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705623"
---
# <a name="related-services-and-interfaces-source-control-vspackage"></a>관련 서비스 및 인터페이스(소스 제어 VSPackage)
이 섹션에서는 의 모든 소스 제어 VSPackage [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]관련 인터페이스를 나열합니다. 소스 제어 VSPackage는 이러한 인터페이스 중 일부를 구현하고 다른 인터페이스를 사용하여 소스 제어 작업을 수행합니다.

## <a name="interfaces-implemented-by-and-for-source-control-vspackages"></a>소스 제어 VSPackage에 의해 구현된 인터페이스
 다음 인터페이스는 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]에 설명되어 있으며 소스 제어 VSPackage는 원하는 기능 집합에 따라 해당 인터페이스의 하위 집합을 구현합니다. 일부 인터페이스는 필수로 표시되며 모든 소스 제어 VSPackage에서 구현해야 합니다.

 패키지가 구현하지 않는 인터페이스의 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 경우 기본 구현을 제공합니다. VSPackage가 등록되지 않고 프로젝트가 제어되지 않는 경우 기본 구현이 설계되었습니다. 제대로 작성된 소스 제어 VSPackage는 해당 인터페이스의 기본 구현에 맡기지 않고 필요한 모든 인터페이스를 구현합니다.

 소스 제어 VSPackage는 다음 인터페이스의 일부 또는 전부를 캡슐화하는 개인 서비스를 구현해야 합니다.

 인터페이스는 다음과 같습니다.

- 필수: 적절한 엔터티(소스 제어 VSPackage, 소스 제어 스텁, 프로젝트)는 인터페이스를 구현해야 합니다.

- 권장 사항: 엔터티는 이 인터페이스를 구현해야 합니다. 그렇지 않으면 소스 제어 기능이 제한될 수 있습니다.

- 선택 사항: 엔터티는 이 인터페이스를 구현하여 보다 풍부한 기능 집합을 제공할 수 있습니다.

| 인터페이스 | 목적 | 에 의해 구현 | 구현? |
| - | - |--------------------------|-------------|
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> | 편집기는 파일을 수정하거나 저장하기 전에 이 인터페이스를 호출합니다. 소스 제어 VSPackage 파일을 체크 아웃하거나 체크 아웃에 실패하면 작업을 거부할 수 있습니다. | 소스 제어 VS패키지 | 권장 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2> | 이 인터페이스는 소스 제어를 통해 프로젝트를 등록 및 등록 취소하고 기본 소스 제어 글리프에 대한 지원을 제공하는 등 프로젝트에 대한 기본 소스 제어 기능을 제공합니다. | 소스 제어 VS패키지 | 필수 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> | 이 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 인터페이스는 <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> 함수를 사용하거나 구현하는 `IVsHierarchy` 개체를 로 `IVsSccProject2`캐스팅하기만 하면 됩니다. 프로젝트에서 소스 제어하에 파일을 얻거나 현재 소스 제어 상태 또는 위치를 프로젝트에 알리는 데 사용됩니다. | Project | 필수 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider> | 통합 모듈은 이 인터페이스를 사용하여 현재 활성 VSPackage를 설정합니다. | 소스 제어 VS패키지 | 필수 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> | 이 인터페이스는 구독 모델을 기반으로 합니다. 모든 VSPackage는 문서 이벤트를 수신하고 발생하려는 이벤트에 대해 셸에서 조언을 받도록 신호를 표시할 수 있습니다. 구현 하 고 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]VSPackage에 구현 `IVsTrackProjectDocumentsEvents2` 하는 이벤트를 전달 하는 에 의해 처리 됩니다. | 소스 제어 스텁 | 필수 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments3> | 이 인터페이스는 일괄 처리, 동기화된 읽기/쓰기 `OnQueryAddFiles` 작업 및 고급 메서드를 제공합니다. | 소스 제어 스텁 | 필수 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> | **솔루션 탐색기** 및 프로젝트는 새 파일이 프로젝트에 추가되거나 파일 및 폴더의 이름이 바뀌거나 프로젝트에서 삭제될 때 이 인터페이스를 호출합니다. 소스 제어 VSPackage는 프로젝트 파일을 체크 아웃하거나 작업을 취소할 수 있습니다. | 소스 제어 VS패키지 | 권장 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents3> | **솔루션 탐색기** 및 프로젝트는 IVstrackProjectDocuments3 인터페이스의 메서드에 대한 호출에 대한 응답으로 이 인터페이스를 호출합니다. 소스 제어 VSPackage는 일괄 처리된 작업을 추적하고, 동기화된 읽기/쓰기 `OnQueryAddFiles` 작업을 추적하고, 보다 고급 메서드로 작업할 수 있습니다. | 소스 제어 VS패키지 | 권장 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccEnlistmentPathTranslation> | 이 인터페이스는 웹 프로젝트에 대한 인리스트먼트 관리 지원을 제공합니다. | 소스 제어 VS패키지 | 권장 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManagerTooltip> | 이 인터페이스는 프로젝트의 소스 제어 파일에 대한 도구 팁을 검색하는 데 사용됩니다. | 소스 제어 VS패키지 | Optional |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccOpenFromSourceControl> | 이 인터페이스는 네임스페이스 확장 지원을 제공합니다. | 소스 제어 VS패키지 | Optional |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccControlNewSolution> | VSPackage는 이 인터페이스를 사용하여 네임스페이스 확장을 **새**것, **열기**또는 **저장** 대화 상자에 통합합니다. 따라서 프로젝트를 생성 시 소스 제어에 자동으로 추가하거나 저장 작업이 적용될 때 소스 제어에 추가할 수 있습니다. | 소스 제어 VS패키지 | Optional |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs> | VSPackage는 이 인터페이스를 사용하여 **솔루션 탐색기의**노드에 대한 소스 제어 글리프로 추가 글리프를 정의합니다. | 소스 제어 VS패키지 | Optional |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccAddWebProjectFromSourceControl> | 웹 프로젝트에 대한 대화 상자 **추가** 상자는 이 인터페이스를 사용합니다. 소스 제어 위치를 검색하고 해당 위치의 소스 제어 리포지토리에 이전에 추가된 웹 프로젝트를 여는 메서드를 제공합니다. | 소스 제어 VS패키지 | 권장 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc> | 이 인터페이스는 소스 제어에서 프로젝트의 비동기(백그라운드) 로드를 지원합니다. | 소스 제어 VS패키지 | Optional |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromSccProjectEvents> | 이 인터페이스를 통해 프로젝트에서 시작된 비동기 로드의 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc>진행 상황을 볼 수 있습니다. | Project | Optional |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccToolsOptions> | 이 인터페이스를 사용하면 IDE가 활성 소스 제어 VSPackage를 쿼리할 수 있습니다. IDE는 등록된 활성 소스 제어 VSPackage가 없는 경우에도 의미가 있는 소스 제어 설정값을 쿼리합니다. 이 인터페이스는 에서 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]구현및 처리됩니다. | 소스 제어 스텁 | 필수 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider> | 이 인터페이스는 소스 제어 VSPackage를 등록하는 데 사용됩니다. | 소스 제어 스텁 | 필수 |
| <xref:EnvDTE.SourceControl> | 이 인터페이스는 자동화에 사용됩니다. 따라서 UI를 표시하지 않고 실행할 수 있는 함수만 노출됩니다. | 소스 제어 VS패키지 | Optional |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> | 이 인터페이스는 솔루션(.sln) 파일에 소스 제어 설정을 저장하는 데 사용됩니다. 설정에는 소스 제어 위치 및 소스 제어 상태 플래그가 포함됩니다. | 소스 제어 VS패키지 | 권장 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> | 이 인터페이스는 솔루션 옵션(.suo) 파일에 소스 제어 설정을 저장하는 데 사용됩니다. 여기에는 현재 사용자의 인리스트먼트 위치와 같은 사용자별 소스 제어 설정이 포함될 수 있습니다. | 소스 제어 VS패키지 | 권장 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> | 이 인터페이스는 솔루션을 닫기 전에 프로젝트 파일을 체크 인하거나 프로젝트를 열 때 소스 제어에서 새 파일을 가져오는 등의 작업을 수행하기 위해 이벤트를 모니터링하는 데 사용됩니다. | 소스 제어 VS패키지 | 권장 |

## <a name="see-also"></a>참조
- [디자인 요소](../../extensibility/internals/source-control-vspackage-design-elements.md)
