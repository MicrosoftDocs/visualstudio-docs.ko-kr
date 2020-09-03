---
title: 사용자 지정 사용자 인터페이스 (소스 제어 VSPackage) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interface, source control packages
- source control packages, user interface
ms.assetid: f35ddb24-53bf-461e-b34f-7414f657c082
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a6ef807cef17a6ca3cddfee05ba57ace27e34a9e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80708924"
---
# <a name="custom-user-interface-source-control-vspackage"></a>사용자 지정 사용자 인터페이스 (소스 제어 VSPackage)
VSPackage는 Visual Studio 명령 테이블 (*vsct*) 파일을 통해 해당 메뉴 항목 및 해당 기본 상태를 선언 합니다. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE (통합 개발 환경)는 VSPackage 로드 될 때까지 메뉴 항목을 기본 상태로 표시 합니다. 그런 다음 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 메서드를 호출 하 여 메뉴 항목을 활성화 하거나 비활성화 합니다.

 VSPackage는 명령 UI (사용자 인터페이스) 컨텍스트에 따라 VSPackage가 자동으로 로드 될 수 있도록 레지스트리 키를 설정할 수 있습니다. 하지만 일반적으로 특정 UI 컨텍스트로 전환 하는 대신 소스 제어 VSPackage는 주문형으로 로드 해야 합니다. **Autoloadpackages** 레지스트리 키에 대 한 자세한 내용은 [vspackage 관리](../../extensibility/managing-vspackages.md)를 참조 하세요.

## <a name="vspackage-ui"></a>VSPackage UI
 소스 제어 패키지는 VSPackage 구현 되며에서 UI를 사용 하지 않습니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . 각 소스 제어 VSPackage는 메뉴 항목, 메뉴 그룹, 도구 창, 도구 모음 및 소스 제어 VSPackage 특정 옵션을 설정 하는 데 필요한 UI와 같은 고유한 UI 요소를 지정 해야 합니다. 이러한 UI 요소는 정적 또는 동적으로 사용 하도록 설정할 수 있습니다. 정적 UI 요소는 *vsct* 파일에 정의 되며 VSPackage이 로드 되는지 여부를 표시 합니다. 동적 UI 요소는와 같은 특정 명령 UI 컨텍스트 <xref:EnvDTE.Constants.vsContextNoSolution> 또는 메서드에 대 한 호출의 결과로 표시 될 수 있습니다 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> . 동적 UI 요소의 표시 유형은 지연 된 Vspackage 로드에 대 한 전략을 준수 합니다.

## <a name="ui-constraints-on-source-control-vspackages"></a>소스 제어 Vspackage에 대 한 UI 제약 조건
 소스 제어 VSPackage를 로드 한 후에는 IDE에서 제거할 수 없으므로 VSPackage은 비활성 상태를 시작할 수 있어야 합니다. VSPackage가 더 이상 활성 상태가 아닌 알림을 수신 하면 VSPackage UI를 사용 하지 않도록 설정 하 고 외부 IDE 상호 작용을 무시 합니다. <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>VSPackage가 활성화 되어 있지 않으면 VSPackage의 메서드 구현에서 명령을 숨겨야 합니다.

 모든 소스 제어 VSPackage는 인터페이스를 구현 해야 합니다 `IVsSccProvider` . 인터페이스에서 및의 두 메서드 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A> 는 VSPackage에 의해 구현 되어야 합니다.

 소스 제어 VSPackage는, 등에 의해 구현 되는 다양 한 IDE 이벤트를 구독할 수 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> 있습니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> . 또한 VSPackage는와 같은 레지스트리 사용 콜백 인터페이스를 구현 했을 수 있습니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> . 이러한 인터페이스는 모두 비활성화 될 때 무시 되어야 합니다.

 다음 목록에는 소스 제어 VSPackage 활성 상태의 영향을 받는 인터페이스가 나와 있습니다.

- 프로젝트 문서 이벤트를 추적 합니다.

- 솔루션 이벤트.

- 솔루션 지 속성 인터페이스. 비활성화 하는 경우 패키지는 *.sln* 및 *.suo* 파일에 쓰지 않아야 합니다.

- 속성 extender입니다.

  <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2> 소스 제어 VSPackage가 비활성화 된 경우 필수 및 및 소스 제어와 연결 된 선택적 인터페이스도 호출 되지 않습니다.

  IDE를 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 시작할 때 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 명령 UI 컨텍스트를 현재 기본 소스 제어 VSPackage ID의 id로 설정 합니다. 이렇게 하면 실제로 VSPackage를 로드 하지 않고 IDE에 활성 소스 제어 VSPackage의 정적 UI가 표시 됩니다. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)][!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider> VSPackage에 대 한 호출을 수행 하기 전에 VSPackage가에 등록 될 때까지 일시 중지 합니다.

  다음 표에서는 IDE에서 다양 한 UI 항목을 숨기는 방법에 대 한 구체적인 정보를 설명 합니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

| UI 항목 | 설명 |
| - | - |
| 메뉴 및 도구 모음 | 소스 제어 패키지는 초기 메뉴 및 도구 모음 표시 상태를 *vsct* 파일의 [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) 섹션에 있는 소스 제어 패키지 ID로 설정 해야 합니다. 이렇게 하면 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] VSPackage를 로드 하 고 메서드 구현을 호출 하지 않고 IDE에서 메뉴 항목의 상태를 적절 하 게 설정할 수 있습니다 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> . |
| 도구 창 | 소스 제어 VSPackage 비활성화 된 경우 소유 하 고 있는 모든 도구 창을 숨깁니다. |
| 소스 제어 VSPackage 옵션 페이지 | 레지스트리 키 **HKLM\SOFTWARE\Microsoft\VisualStudio\X.Y\ToolsOptionsPages\VisibilityCmdUIContexts** 를 사용 하면 VSPackage에서 해당 옵션 페이지를 표시 해야 하는 컨텍스트를 설정할 수 있습니다. 이 키의 레지스트리 항목은 원본 제어 서비스의 SID (서비스 ID)를 사용 하 여 만들고 DWORD 값을 1로 할당 해야 합니다. 소스 제어 VSPackage가 등록 된 컨텍스트에서 UI 이벤트가 발생할 때마다 VSPackage가 활성 상태인 경우 호출 됩니다. |

## <a name="see-also"></a>추가 정보
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>
- <xref:EnvDTE.Constants.vsContextNoSolution>
- [VSPackage 관리](../../extensibility/managing-vspackages.md)
