---
title: 관련 서비스 및 인터페이스 (소스 제어 VSPackage) | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80705623"
---
# <a name="related-services-and-interfaces-source-control-vspackage"></a>관련 서비스 및 인터페이스(소스 제어 VSPackage)
이 섹션에는의 모든 소스 제어 VSPackage 관련 인터페이스가 나열 되어 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] 있습니다. 소스 제어 VSPackage는 이러한 인터페이스 중 일부를 구현 하 고 다른 인터페이스를 사용 하 여 소스 제어 작업을 수행 합니다.

## <a name="interfaces-implemented-by-and-for-source-control-vspackages"></a>소스 제어 Vspackage에 대해 및에서 구현 된 인터페이스
 다음 인터페이스는에 설명 되어 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] 있으며, 소스 제어 VSPackage는 원하는 기능 집합에 따라 하위 집합을 구현 합니다. 일부 인터페이스는 필수로 표시 되며 모든 소스 제어 VSPackage 구현 되어야 합니다.

 패키지에서 구현 하지 않는 인터페이스의 경우에서는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 기본 구현을 제공 합니다. 기본 구현에서는 VSPackage가 등록 되지 않고 프로젝트가 제어 되지 않는 경우를 위해 설계 되었습니다. 올바르게 작성 된 소스 제어 VSPackage는 해당 인터페이스의 기본 구현으로 유지 하는 대신 필요한 모든 인터페이스를 구현 합니다.

 소스 제어 VSPackage는 다음 인터페이스의 일부 또는 전부를 캡슐화 하는 개인 서비스를 구현 해야 합니다.

 인터페이스는 다음과 같습니다.

- 필수: 적절 한 엔터티 (소스 제어 VSPackage, 소스 제어 스텁, 프로젝트)가 인터페이스를 구현 해야 합니다.

- 권장: 엔터티는이 인터페이스를 구현 해야 합니다. 그렇지 않으면 소스 제어 기능이 제한 될 수 있습니다.

- 선택 사항: 엔터티는이 인터페이스를 구현 하 여 보다 다양 한 기능 집합을 제공할 수 있습니다.

| 인터페이스 | 목적 | 구현 방법 | 구현한? |
| - | - |--------------------------|-------------|
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> | 편집기는 파일을 수정 하거나 저장 하기 전에이 인터페이스를 호출 합니다. 소스 제어 VSPackage는 체크 아웃에 실패 하는 경우 파일을 체크 아웃 하거나 작업을 거부할 수 있습니다. | 소스 제어 VSPackage | 권장 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2> | 이 인터페이스는 소스 제어를 사용 하 여 프로젝트를 등록 및 등록 취소 하 고 기본 소스 제어 문자 모양에 대 한 지원을 제공 하는 등 프로젝트의 기본 소스 제어 기능을 제공 합니다 | 소스 제어 VSPackage | 필수 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> | 이 인터페이스는에서 함수를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 사용 하 여 <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> 가져오거나를 구현 하는 개체를 단순히 캐스팅 하 여 가져옵니다 `IVsHierarchy` `IVsSccProject2` . 이 클래스는 프로젝트에서 소스 제어에서 사용 중인 파일을 가져오거나 현재 소스 제어 상태 또는 위치를 프로젝트에 알리는 데 사용 됩니다. | 프로젝트 | 필수 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider> | 통합 모듈은이 인터페이스를 사용 하 여 현재 활성 VSPackage를 설정 합니다. | 소스 제어 VSPackage | 필수 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> | 이 인터페이스는 구독 모델을 기반으로 합니다. 모든 VSPackage은 문서 이벤트를 수신 하 고 발생 하는 이벤트에 대해 셸에서 advise 하는 것으로 신호를 보낼 수 있습니다. 이는을 구현 하 고 처리 하며,이는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 을 구현 하는 이벤트를 `IVsTrackProjectDocumentsEvents2` VSPackage에 전달 합니다. | 소스 제어 스텁 | 필수 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments3> | 이 인터페이스는 일괄 처리, 동기화 된 읽기/쓰기 작업 및 고급 메서드를 제공 합니다 `OnQueryAddFiles` . | 소스 제어 스텁 | 필수 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> | 프로젝트에 새 파일을 추가 하거나 프로젝트에서 파일 및 폴더의 이름을 바꾸거나 삭제할 때 **솔루션 탐색기** 및 프로젝트는이 인터페이스를 호출 합니다. 소스 제어 VSPackage는 프로젝트 파일을 체크 아웃 하거나 작업을 취소할 수 있습니다. | 소스 제어 VSPackage | 권장 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents3> | **솔루션 탐색기** 및 프로젝트는 IVstrackProjectDocuments3 인터페이스의 메서드에 대 한 호출에 대 한 응답으로이 인터페이스를 호출 합니다. 원본 제어 VSPackage는 일괄 처리 된 작업을 추적 하 고, 읽기/쓰기 작업을 동기화 하 고, 고급 메서드를 사용할 수 있습니다 `OnQueryAddFiles` . | 소스 제어 VSPackage | 권장 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccEnlistmentPathTranslation> | 이 인터페이스는 웹 프로젝트에 대 한 참여 관리 지원을 제공 합니다. | 소스 제어 VSPackage | 권장 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManagerTooltip> | 이 인터페이스는 프로젝트에서 소스 제어 파일에 대 한 도구 설명을 검색 하는 데 사용 됩니다. | 소스 제어 VSPackage | 선택 사항 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccOpenFromSourceControl> | 이 인터페이스는 네임 스페이스 확장을 지원 합니다. | 소스 제어 VSPackage | 선택 사항 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccControlNewSolution> | VSPackage는이 인터페이스를 사용 하 여 **새**, **열기**또는 **저장** 대화 상자에 네임 스페이스 확장을 통합 합니다. 따라서 저장 작업이 적용 될 때 프로젝트가 생성 될 때 소스 제어에 자동으로 추가 되거나 소스 제어에 추가 될 수 있습니다. | 소스 제어 VSPackage | 선택 사항 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs> | VSPackage는이 인터페이스를 사용 하 여 **솔루션 탐색기**의 노드에 대 한 소스 제어 문자 모양으로 추가 문자 모양을 정의 합니다. | 소스 제어 VSPackage | 선택 사항 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccAddWebProjectFromSourceControl> | 웹 프로젝트에 대 한 **추가** 대화 상자는이 인터페이스를 사용 합니다. 소스 제어 위치를 검색 하 고 해당 위치의 소스 제어 리포지토리에 이전에 추가 된 웹 프로젝트를 여는 메서드를 제공 합니다. | 소스 제어 VSPackage | 권장 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc> | 이 인터페이스는 소스 제어에서 프로젝트의 비동기 (백그라운드) 로드를 지원 합니다. | 소스 제어 VSPackage | 선택 사항 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromSccProjectEvents> | 이 인터페이스를 사용 하면 프로젝트에서에 의해 시작 된 비동기 로드의 진행률을 볼 수 있습니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAsynchOpenFromScc> . | 프로젝트 | 선택 사항 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccToolsOptions> | 이 인터페이스를 사용 하면 IDE에서 활성 소스 제어 VSPackage를 쿼리할 수 있습니다. IDE는 활성화 된 소스 제어 VSPackage 등록 되지 않은 경우에도 의미가 있는 소스 제어 설정 값을 쿼리 합니다. 이 인터페이스는에서 구현 되 고 처리 됩니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . | 소스 제어 스텁 | 필수 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider> | 이 인터페이스는 소스 제어 VSPackage를 등록 하는 데 사용 됩니다. | 소스 제어 스텁 | 필수 |
| <xref:EnvDTE.SourceControl> | 이 인터페이스는 자동화에 사용 됩니다. 따라서 UI를 표시 하지 않고 실행할 수 있는 함수만 노출 합니다. | 소스 제어 VSPackage | 선택 사항 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> | 이 인터페이스는 솔루션 (.sln) 파일의 소스 제어 설정을 저장 하는 데 사용 됩니다. 설정에는 소스 제어 위치 및 소스 제어 상태 플래그가 포함 됩니다. | 소스 제어 VSPackage | 권장 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> | 이 인터페이스는 솔루션 옵션 (.suo) 파일의 소스 제어 설정을 저장 하는 데 사용 됩니다. 여기에는 현재 사용자의 참여 위치와 같은 사용자 관련 소스 제어 설정이 포함 될 수 있습니다. | 소스 제어 VSPackage | 권장 |
| <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> | 이 인터페이스는 솔루션을 닫기 전에 프로젝트 파일 체크 인 또는 프로젝트를 열 때 소스 제어에서 새 파일 가져오기 등의 작업을 수행 하기 위해 이벤트를 모니터링 하는 데 사용 됩니다. | 소스 제어 VSPackage | 권장 |

## <a name="see-also"></a>추가 정보
- [디자인 요소](../../extensibility/internals/source-control-vspackage-design-elements.md)
